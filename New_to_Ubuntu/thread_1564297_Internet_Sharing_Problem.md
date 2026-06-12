---
title: "Internet Sharing Problem"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by MindController on 2010-08-30
Hey! I've got one problem regarding internet sharing. Here is the detail..... my laptop is running on lucid and using the internet with wifi. I have another pc runnign on window without wireless card. Can I share the internet connection with that widows pc. How do I configure the both laptop and PC. Please help me.
Sorry for my bad english,BTW

---

### Post by kwacka on 2010-08-30
Assuming you have an xDSl connection, does the PC have a network card? If yes, just plug straight into switch/router.

If no, you'll need one - your choice for wired or unwired.

---

### Post by MindController on 2010-08-30
:( nobody interested in my thread. so sad. Please help me.

---

### Post by Iowan on 2010-08-30
> **MindController said:**
> :( nobody interested in my thread. so sad. Please help me.
**kwacka** doesn't count???

The GUI version of [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page might work for you - or it may need some tweaking for wireless... Depending on the network cards, you may need a crossover cable (or hub/switch) between the two machines.

---

### Post by gabriel8a2002 on 2010-08-31
Mr. Mind Controller, it looks like you need a router,  please specify what internet type you are using.  A router will not work with dial-up im sorry.  Only Cable and DSL will work, and for the comptuer that has no wireless, a long cat5 cable will do =)  depending on where you are at they should be relatively cheap.

---

### Post by varunendra on 2010-09-02
> **Iowan said:**
> **kwacka** doesn't count???......
:lolflag:

I guess they must have made simultaneous posts & as such, he couldn't have noticed kwacka's post. :D


@MindController,

Is [this]("http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/") what you want. (if yes, say thanks to Justin Pot on that page!)

This would tell how make your laptop ready to give. Now how to make windows PC ready to take would be a different story. I hope nobody would mind if you post back in case of problems with that.

And yes, as Iowan said, you must use an Ethernet **cross **cable between the laptop & the PC.

---

### Post by bredman on 2010-09-02
To use your laptop as an Internet Gateway, you will need to connect the PC to the laptop. You cannot connect directly using a normal Ethernet cable, you must use a crossover cable, or put a router between the PC and the laptop.

If you need to buy a crossover cable, I suggest it is cheaper just to add WiFi to your PC. You can get a standard USB WiFi for less than $10 at
[http://www.dealextreme.com/details.dx/sku.24688](http://www.dealextreme.com/details.dx/sku.24688)

This particular item is no thing of beauty, but it is cheap and works perfectly on Windows.

---

### Post by varunendra on 2010-09-02
> **bredman said:**
> You cannot connect directly using a normal Ethernet cable, you **must use a crossover cable**, or put a router between the PC and the laptop.
Hmm.... Looks like I must correct myself :(

I was confusing [Auto-MDIX]("http://homepage.ntlworld.com/robin.d.h.walker/cmtips/ethernet.html") with Auto-negotiation. Just made a brief search & found they are entirely different things. Correcting that line in my previous post.

Sorry for the wrong assumption & Thanks for correcting me bredman.

---

