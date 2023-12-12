<template>
  <div class="category-dropdown">
    <label for="category"> Select category</label>
    <select v-model="selectedCategory" @change="filteredProducts">
    <option value="all">All Products</option>
    <option value="bread">Bread</option>
    <option value="cakes">Cakes</option>
    </select>
  </div>
  <div class="search-bar">
  <label for="search">Search:</label>
  <input v-model="searchTerm" @input="filteredProducts" type="text" id="search" placeholder="Enter product name">
</div>
  <div class="wrapper">
    <div class="row" v-if="filteredProducts.length">
      <div class="prodCard" v-for=" product in filteredProducts " :key="product.id">

        <div class="card-header">
        <h3>{{ product.name }}</h3>
      </div>
      <div @mouseenter="onMouseEnter" @mouseleave="onMouseLeave" class="card-body">
        <img :src="product.image" alt="product.name" loading="lazy">
        <p :class="{expensive : product.amount > 420}">R{{ product.amount.toFixed(2) }}</p>
      </div>
      <div class="card-footer">
        <a href="#" type="button">View Details</a>
      </div>
    </div>
  </div>
  <div v-else>
    <h2>Out of stock</h2>
  </div>
 </div>
</template>

<script>



  export default {
        name: 'App',
        data() {
            return {
             products: [  
    // product data
    {
        id: 1,
        name: 'Super-seeded-oat-bread',
        amount: 35,
        image: "https://i.postimg.cc/63dyHm59/super-seeded-oat-bread-2.jpg"
    },
    {
        id: 2,
        name: 'Crunchies',
        amount: 12,
        image: "https://i.postimg.cc/DfBYDYXy/crunchies-12.jpg"
    },
    {
        id: 3,
        name: 'German Chocolate Cake',
        amount: 650,
        image: "https://i.postimg.cc/Y9XfXZy5/german-chocolate-cake-177122-1.jpg"

    },
    {
        id: 4,
        name: 'Crazy Brownies',
        amount: 9,
        image: "https://i.postimg.cc/8c04C9RR/crazy-brownies-1.jpg"
    },
    {
        id: 5,
        name: 'Homemade-artisan-bread',
        amount: 18,
        image: "https://i.postimg.cc/RV1L3g7x/homemade-artisan-bread.jpg"
    },
    {
        id: 6,
        name: 'Santa-fe-cafe-tune-up-cafe breakfast',
        amount: 50,
        image: "https://i.postimg.cc/fWK6sR6s/best-breakfast-santa-fe-cafe-tune-up-cafe-fwx-298bbf750723481eabb95d3edbe7895d.jpg"
    },
    {
        id: 7,
        name: 'Chocolate Lamington',
        amount: 12,
        image: "https://i.postimg.cc/tTdMz6jg/lamington-recipe-ft.jpg"
    },
    {
        id: 8,
        name: 'Scones',
        amount: 6,
        image: "https://i.postimg.cc/tTDzTNbF/Me-Feb-2.jpg"
    },
    {
        id: 9,
        name: 'Breakfast with coffee',
        amount: 40,
        image: "https://i.postimg.cc/k4MxkRSG/the-best-coffee-and-breakfast.jpg"
    },
],
selectedCategory: 'all'
            };
        },
        computed: {
          filteredProducts() {
    if (this.selectedCategory === 'all') {
      return this.products;
    } else {
     
      return this.products.filter(product => product.category === this.selectedCategory);
    }
  }
        },
        methods: {
            onMouseEnter() {
                alert("Hello there")
            },
            onMouseLeave() {
                alert("Bye")
            }
        }
    }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
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
.category-dropdown {
    margin-bottom: 20px;
    
  }

</style>
