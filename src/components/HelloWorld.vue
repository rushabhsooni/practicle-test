<template>
  <div class="hello">
    
              <nav class="navbar navbar-expand-lg navbar-light bg-light">
                <a class="navbar-brand" href="#">Navbar</a>
                <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                  <span class="navbar-toggler-icon"></span>
                </button>

                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                  <ul class="navbar-nav mr-auto">
                    <li class="nav-item ">
                      <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
                    </li>
                    <li class="nav-item">
                      <a class="nav-link" href="#">Link</a>
                    </li>
                    <li class="nav-item dropdown">
                      <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                        Dropdown
                      </a>
                      <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                        <a class="dropdown-item" href="#">Action</a>
                        <a class="dropdown-item" href="#">Another action</a>
                        <div class="dropdown-divider"></div>
                        <a class="dropdown-item" href="#">Something else here</a>
                      </div>
                    </li>
                    <li class="nav-item">
                      <a class="nav-link disabled" href="#">Disabled</a>
                    </li>
                  </ul>
                  <form class="form-inline my-2 my-lg-0">
                    <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
                    <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
                  </form>
                </div>
                </nav>
                <div class="container mt-5  ">
                  <div class="card">
                    
                <div class="row  ">  
                   <div class="col-2  border-right mt-1 ">
                     <h4> Documents </h4>
                     <ul>
                       <li v-for="n in 4" :key=n >  <button @click="newTab(n)"  type="button" class="btn btn-link "  >  {{"Document "+n}}  </button>
                          </li>
                     </ul>
                      
                   </div>
                   <div class="col-9 ml-2 ">
                      <ul>
                        <div class="row mt-2  ">
                         <div :class="[i != selected ? ' non-active col-3' :'active col-3']" v-for="i in tabs" :key="i">
                            <span  @click="closeTab(i)" class="badge  cross text-danger  "> x </span>
                         <button  type="button" @click="change(i)"  class="btn ">
                              Document {{i}}
                         </button>
                         </div>
                        </div>
                        <div class="row active body  " v-show="tabs.length > 0" >
                            <div class=" p-3 ">
                              this is the content of Document {{selected}}
                             </div>
                        </div>
                      </ul>
                </div> 
                </div>
              </div>
              </div>
    
      
  </div>
</template>



<script>



export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
      return {
        tabs: [
          1,
        ],
        selected:'1',  
      }

    },
     methods: {
       
      closeTab(x) {
        for (let i = 0; i < this.tabs.length; i++) {
          if (this.tabs[i] === x) {
            this.tabs.splice(i, 1)
          }
          var last = (this.tabs.length -1);
        }
        this.selected = this.tabs[last];
      },

      newTab(y) {
          if(this.tabs.includes(y))
          {
            this.selected = y;
          }
          else{
            this.tabs.push(y);
          }
      },
    
    change(active){
      console.log(active);
      this.selected = active;
    }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.red{
  background: red;
}

.blue{
  background: blue;
}
.cross{
  position: relative;
  top:-5px;
  right:-150px;

}
.non-active{
  background-color: rgb(185,185,185)  ;
}
.active{
  background-color: rgb(225,225,225) !important;
}

.btn:focus{
outline: 0;
box-shadow: 0 0 0 0.2rem rgba(0, 0, 0, 0);
}
.body{
  height:100px;
  
}
</style>
