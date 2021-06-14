function loadSoldByOthers(userID) {
    var itemListSoldByOthers = document.getElementById('itemListSoldByOthers');

    // SOLD BY OTHERS QUERY + Add cards to list
    db.collection("items")
      .where("status", "==", "Sold")
      .orderBy('soldDate', 'desc')
      .limit(20)
      .get()
      .then((querySnapshot) => {
        querySnapshot.forEach((doc) => {
          var sellerId = doc.data().user;
          var brand = doc.data().brand;
          var soldPrice = doc.data().soldPrice;
          var images = doc.data().images;
          var imageUrl = images.frontImage;

          // Add card to list if seller is other than myself
          if (sellerId != userID) {
            if ("productImage" in images) {
              imageUrl = images.productImage;
            }
            var soldByOthersItemCardHTML = `<div class="div-block-14"><div class="ratio-box _16-9"><div class="conten-block with-image"><div class="img-container" style="background-image: url('${imageUrl}');"></div></div></div><div class="text-block-14">${soldPrice} kr</div><div class='text-block-34'>${brand}</div></div>`;
            itemListSoldByOthers.innerHTML += soldByOthersItemCardHTML;
          }
        });
      });
  }
