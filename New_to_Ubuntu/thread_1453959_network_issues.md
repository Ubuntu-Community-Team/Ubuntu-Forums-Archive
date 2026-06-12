---
title: "network issues"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by letsgomudkip! on 2010-04-14
For some reason when I use bittorent (any client) the network manager kicks me off and will not restart and freezes up which usually leads me to have to restart the computer manually.  Also the same thing happens if I use a site that has a lot of images to upload such as a manga/comic reader site. Does anyone have any suggestions?  I am new to Linux and to ubuntu/kubuntu karmic koala netbook remix. i can use both ubuntu/kubuntu and its partitioned with windows 7 starter...

---

### Post by letsgomudkip! on 2010-04-14
I'm pretty bummed so please help me out...

---

### Post by Fuith on 2010-04-14
I had the same problem with Network Manager on my laptop. I eventually installed wicd which seems to work. Open a terminal and type this:

```
sudo apt-get install wicd
```

This will also uninstall network manager, so it might be wise to save a backup of the network manager deb.

As to why it does this I have no idea.

---

### Post by letsgomudkip! on 2010-04-15
when i installed wicd network manager i set up the encryption code but it cant find the ip address so when i input all that good stuff it still doesn't connect and suggestions?

---

### Post by Fogel35 on 2010-04-15
> **letsgomudkip! said:**
> For some reason when I use bittorent (any client) the network manager kicks me off and will not restart and freezes up which usually leads me to have to restart the computer manually.  Also the same thing happens if I use a site that has a lot of images to upload such as a manga/comic reader site. Does anyone have any suggestions?  I am new to Linux and to ubuntu/kubuntu karmic koala netbook remix. i can use both ubuntu/kubuntu and its partitioned with windows 7 starter...

You connecting via wireless or through a wire?  What kind of network hardware are you using?

---

### Post by letsgomudkip! on 2010-04-15
wireless through a linksys router. It says it cannot contact a wireless access point.

---

### Post by letsgomudkip! on 2010-04-15
WOOT!!! i FIGURED IT OUT!!!

---

