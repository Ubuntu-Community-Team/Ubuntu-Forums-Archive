---
title: "Laptop not recognizing router."
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Wicked_Glory on 2009-12-21
So I had to reinstall 9.04 because of unrelated issues, and ever since then I can't connect to any wireless networks. I've got a working driver and wireless card as well. If it matters I have a 2Wire home portal 1000sw router and linksys router whose model I can't seem to remember.

---

### Post by Some Penguin on 2009-12-21
You might want to mention --

- the chipset of your wireless card
- the driver you're using
- the method you're using to try to get the wireless card to associate with the router and how you're determining that it's not working

---

### Post by Wicked_Glory on 2009-12-21
Alright. I've got a Dell Wireless 1397 802.11a/g Half Mini-Card. The driver is a Broadcom STA wireless driver. Before I had to reinstall it would recognize the networks automatically. Now it doesn't, and even when I manually enter the details it still doesn't. It shows the device when I use lshw, but won't connect to the router.

---

### Post by Some Penguin on 2009-12-21
[https://bugs.launchpad.net/ubuntu/+bug/203819](https://bugs.launchpad.net/ubuntu/+bug/203819)
[http://ubuntuforums.org/showthread.php?p=8533161]("http://ubuntuforums.org/uforums.org/showthread.php?p=8533161")

That looks to be a fairly ugly case.

---

### Post by Wicked_Glory on 2009-12-21
Damn... So I basically have to get a new wireless card... Or would downloading a different driver solve it?

---

### Post by muteXe on 2009-12-21
Where in the world are you fella?  If the UK you could have a look at this maybe:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/288401](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/288401)

---

### Post by Wicked_Glory on 2009-12-21
Nope, not from the Uk. Thanks anyway.

---

### Post by muteXe on 2009-12-21
SOrry that article was about being in the US using a UK laptop. I wasn't clear sorry.

---

### Post by Some Penguin on 2009-12-21
Well, it might be worth giving that Broadcom-targeted kernel a try:

sudo apt-get install bcmwl-kernel-source

---

### Post by Wicked_Glory on 2009-12-21
Oh, in that case I honestly don't know. But more than likely it wasn't built in the UK.

---

### Post by Wicked_Glory on 2009-12-21
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package bcmwl-kernel-source

---

