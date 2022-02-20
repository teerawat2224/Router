<template  >
<div  class="bg-image d-flex justify-content-center align-items-center"
     style="
            background-image: url('https://images7.alphacoders.com/992/thumb-1920-992404.jpg');
            height: 100%
            
            
            
            " >
  <v-container >
    
    <center><h1 class="text-info">Product Page</h1></center>
    <v-container class="d-flex flex-wrap">
      <v-card
        class="mx-auto mb-5"
        max-width="400"
        v-for="(i, index) in productlist"
        :key="index"
      >
        <v-img class="white--text align-end" height="200px" :src="i.imageurl">
          <v-card-title>{{ i.name }}</v-card-title>
        </v-img>

        <v-card-subtitle class="pb-0 ">{{ i.rightText }}</v-card-subtitle>

        <v-card-text class="text--primary">
          <div>{{ i.leftText }}</div>
        </v-card-text>

        <v-card-actions>
          <v-btn  color="info" text :to="'/detail/' + i.name">detail</v-btn>
          <v-btn color="green" text @click="selected(i)"> Add </v-btn>
         
        </v-card-actions>
      </v-card>
    </v-container>

    <table class="table table-striped table-hover">        
    
    </table>
    <v-container
      ><h4 class="text-danger fs-1">ยอดชำระเงิน  {{ total() }} บาท</h4></v-container
    >
    <v-container grid-list-xs class="success">
      <router-view :key="$route.path"></router-view>
    </v-container>
  </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
        productlist: [
        {
         
          name: "Megaman collection",
          imageurl:
            "https://th-live.slatic.net/p/7d3bef7be475816ac8fbd69a2e7b86bf.jpg",
          rightText: "price : 199",
          producturl: "https://www.lazada.co.th/products/megaman-zerozx-legacy-collection-ps4-game-1-rockman-zero-zx-legacy-collection-ps4-i759066102-s1459286627.html?spm=a2o4m.searchlist.list.3.62d924d9hTk6nM&search=1/",
          ctaText: "Shop Now",
          active: false,
          price: 199,
        },

        {
         
          name: "Elder Ring",
          imageurl:
            "https://cdn-prod.scalefast.com/public/assets/user/122595/image/8a9c67edada66b838b347d5d61d71ae3.jpg",
          rightText: "เกมที่จะมาทดสอบจิตใจของคุณว่าแข็งแกร่งแค่ไหน",
          leftText: "",
          ctaText: "Shop Now",
          active: false,
          price: 199,
        },

        {
         
          name: "gundam extreme vs ",
          imageurl:
            https://www.metalbridges.com/wp-content/uploads/2020/02/mobile-suit-gundam-extreme-vs-maxiboost-on-ps4-2.jpg",
          ctaText: "Shop Now",
          active: false,
          price: 99,
        },

        {
         
          name: "dying light 2",
          imageurl:
            "https://m.media-amazon.com/images/I/71bHmsaYKIL._SX342_.jpg",
          rightText: "price : 199",
          ctaText: "Shop Now",
          active: false,
          price: 99,
        },
      ],
    };
  },
  methods: {
    selected: function (i) {
      i.active = !i.active;
    },
    total: function () {
      var sum = 0;
      this.productlist.forEach(function (i) {
        if (i.active) {
          sum += i.price;
        }
      });
      return sum;
    },
  },
 
};
</script>

<style>
h2 {
  color: white;
}
@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  100% {
    background-position: 100% 0%;
  }
}
h1 {
  background: linear-gradient(80deg, #17191a, #fffffd);
  background-size: 50%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradient 2s infinite;
}
.text-danger {
  background: linear-gradient(80deg, #ede9f0, #121312);
  background-size: 50%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradient 2s infinite;
}
.white{
  background: linear-gradient(80deg, #1ab7f5, #b0eb25);
  background-size: 50%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradient 2s infinite;
}
</style>
