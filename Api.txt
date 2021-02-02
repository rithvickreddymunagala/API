var express = require('express')
var firebase = require("firebase");
var firebaseConfig = {
    apiKey: "AIzaSyCfyiRcSjxd0JPVQrhudKJOggmXPSxFhP4",
    authDomain: "cllg-project.firebaseapp.com",
    databaseURL: "https://cllg-project-default-rtdb.firebaseio.com",
    projectId: "cllg-project",
    storageBucket: "cllg-project.appspot.com",
    messagingSenderId: "782428865265",
    appId: "1:782428865265:web:b0548097017c9d39d1df50",
    measurementId: "G-PWV17JBYPB"
   };
   firebase.initializeApp(firebaseConfig);
   var app = express()

   const port = process.env.PORT || 3002
   const bodyParser = require('body-parser');

   app.use(bodyParser.json());
   app.use(bodyParser.urlencoded({
    extended: true
  }));

    app.use((req, res, next) => {
    res.header("Access-Control-Allow-Origin", "*"); // update to match the domain you will make the request from
    res.header("Access-Control-Allow-Headers", "*"); //
    next();
   });

    app.post('/', (req, res) => {
    let data = req.body
    console.log(req)
    res.send({ data: data })
    firebase.database().ref('users/2').set(
      {
        percentage: data.distance,
        ass_persone: "ramesh",
        name: "BH-3",
        url: "https://firebasestorage.googleapis.com/v0/b/cllg-project.appspot.com/o/bh3.png?alt=media&token=b4aa0159-7668-4b30-9c2c-1b4dc4e9bdd7",
        id: "1",
        contact: "9586321476"
     });
  })
    app.get('/', (req, res) => {
    res.send('it is working')
})
console.log("htct");
app.listen(port)
