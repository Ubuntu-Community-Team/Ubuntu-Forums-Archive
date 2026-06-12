---
title: "Jaunty ISO via Transmission bittorrent"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by ricardisimo on 2009-04-23
I have no idea how to use bittorrent clients, so when the3 dialogue popped up, I asked Firefox to open the link target for "ubuntu-9.04-desktop-i386.iso.torrent" with Transmission. On the minus side, Transmission is clearly not involved in the least, just FF's download manager.

On the plus side, it's downloading from this source at about 10 times the speed of any of the mirrors I've found.

Two questions:
[LIST=1]
[*]If I were to get the ISO via torrents, how would I do that?
[*]In the meantime, am I getting a usable ISO just downloading as I am right now?
[/LIST]
Thanks.

---

### Post by michy99 on 2009-04-23
It sounds like you are downloading the ISO via Transmission bittorrent. Do you see a little stick-shift icon in the top right corner? If so, then Transmission is doing its thing. Click on it to open it up.

---

### Post by ricardisimo on 2009-04-23
No, it is definitely just the FF download manager. How would I have initiated a torrent download?

---

### Post by lovinglinux on 2009-04-23
> **ricardisimo said:**
> I have no idea how to use bittorrent clients, so when the3 dialogue popped up, I asked Firefox to open the link target for "ubuntu-9.04-desktop-i386.iso.torrent" with Transmission. On the minus side, Transmission is clearly not involved in the least, just FF's download manager.

The .torrent file is not actually the content you want to download, it is a metadata file, which is basically like a "cake recipe" containing information about the ingredients to make the cake and the phone number of a directory of grocery stores from where you can get them. 

When you open a torrent file with Firefox, it uses the download manager because it needs to download the "recipe" (.torrent) first and then open it with the torrent client (Transmission). 

The torrent client will then grab the address of the tracker server (directory phone number) contained in the .torrent file and send a request (phone call) to check from which peers (grocery stores) you can get the pieces (ingredients) of the file (cake) you want to download. Once the tracker gives your torrent client this information, the client will contact each peer (grocery store) directly, to request  pieces of the file (ingredients). Some peers might not have all the pieces of the file, while others do (seeder), but you can get different pieces (ingredients) from different peers (grocery stores) at the same time.

Once you get all the pieces, the torrent client will put them together (bake) and you have a single file of the content you wanted to download (cake). In this case, an ISO file.

> **ricardisimo said:**
> On the plus side, it's downloading from this source at about 10 times the speed of any of the mirrors I've found.

That's the beauty of BitTorrent. Consider the mirror a supermarket, where everyone can get all ingredients to bake the cake. This is very convenient and usually faster than searching for different grocery stores to get all ingredients you need. But today is "Cake Day" and everyone in the world is trying to buy the ingredients, so the supermarket is full of people. The supermarket has enough ingredients for everyone, but you have to wait a lot to pass through the register.  

The torrent in the other hand, is not distributed by a single store (server). So you can request different ingredients from several stores at the same time and each one of them will send a delivery guy to your door. Some delivery guys are faster than others, but in overall you have all ingredients for your cake much faster than if you would have to pass through the supermaket register with hundreds of people ahead of you.

> **ricardisimo said:**
> 
[LIST=1]
[*]If I were to get the ISO via torrents, how would I do that?
[/LIST]

The torrent client you put all the pieces together and when it finishes downloading you will have an ISO file.

> **ricardisimo said:**
> 
[LIST=1]
[*]In the meantime, am I getting a usable ISO just downloading as I am right now?
[/LIST]

Yes. The torrent client checks if the pieces you download are actually the ones you need (list of ingredients). Nevertheless, is a good idea to check if the final file has the same hash number as the one distributed on the Ubuntu site.

For first time users I recommend using a little extension for Firefox called firetorrent instead of using Transmission. Simply download firetorrent form this [link](http://www.fireaddons.com/downloads/). It should install automatically, then restart Firefox, find a torrent to download and click it. It should start downloading the file automatically, like any other regular download. Can get simpler than that. With this extension, the Firefox download manager downloads the recipe and the ingredients.

---

