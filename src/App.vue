<template>
  <div class="wrapper">
        <div class="row" v-if="products.length"> <!--checking if theres data in the array-->
            <div class="prodCard" v-for="product in products" :key="product.id"> <!--do not put your if statement with your for loop. This variable will specific a specific object. WHen making use of for loop, we need to make us of key to make it unique.  -->
                <div class="card-header">
                    <h3>{{ product.prodName }}</h3> <!--displaying the product name-->
                </div>
                <div class="card-body">
                    <img :src="product.image" :alt="product.prodName" loading="lazy" @mouseenter="onMouseEnter" @mouseleave="onMouseLeave">
                    <p :class="{expensive : product.amount>420}">R{{ product.amount.toFixed(2) }}</p>
                </div> 
                <!-- if its more then 420 then we need to add a class which kinda states its expensive -->
                <div class="card-footer">
                    <a href="#" type="button">View Details</a>
                </div>
            </div> <!--an else statement can be added below if statement is false/or theres nothing in the array. Also make use of a spinner.-->
          
        </div>  
        <div v-else> 
            <h2>Suimasen! No products found.</h2>
        </div>
    </div>
</template>

<script>


export default {
  name: 'ProductsComp',
        data() { //any variable you want to create is stored in data , also don't forget to return what you stated in the data.  
        //Reactive state refers to data
            return {  //an array was create inside the return statement. Return function is similar to the factory function. 
                products: [  //products that will be displayed, if we want more the one we want to the make an array of objects
                    {
                        id: 1,
                        prodName: 'Python Crash Course',
                        category: 'Python',
                        amount: 400.9999,
                        image: 'https://i.postimg.cc/MKDLBPYm/Python-Crash-Course-cover.jpg'
                    }, //the property for the first product
                    {
                        id: 2,
                        prodName: 'Python Programming',
                        category: 'Python',
                        amount: 900.4586,
                        image: 'https://i.postimg.cc/rFcbKX5p/Python-Programming-for-Beginners-cover.jpg'
                    },
                    {
                        id: 3,
                        prodName: 'Mastering C++',
                        category: 'C++',
                        amount: 1800.896,
                        image: 'https://i.postimg.cc/Ss9zrpfT/Mastering-C-Programming.jpg'
                    },
                ]
            } //end of the products
        },
        components: {

        },
        computed() {},
        methods: {
            onMouseEnter() {
                alert('Tonight will be the night that I will fall for youuu') //displaying  a message to the user
            },
            onMouseLeave() {
                alert('Under the night, dont make me change my mind. ')
            },
    }
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2C3E50;
  margin-top: 60px;
}

.wrapper :is(.row) {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
.prodCard {
  width: 18rem;
}
.prodCard :is(>*, img){
  width: 100%;
  aspect-ratio: 1/1;
}
.expensive {
  font-weight: bolder;
  color: darkkhaki;
}
.cheap {
  color: black;
}
</style>
