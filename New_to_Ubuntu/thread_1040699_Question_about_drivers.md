---
title: "Question about drivers"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by kneedragger on 2009-01-15
I have an Acer Aspire and decided to install Ubuntu because I liked it on my desktop. After installing I realised that the wireless doesn't work with the new Ubuntu. I found searching through the forums success with Easy Peasy 1.0 so decided to give it a try. After the install the wireless worked out of the box. After spending some time with Easy Peasy I noticed it looks just like Ubuntu. Is it possible to find what driver is working for the Easy Peasy and use it with Ubuntu?

I'm new to Ubuntu so excuse my ignorance.

thanks

---

### Post by drascus on 2009-01-16
yes you can! that's the beauty of Free Software. if it works on one GNU/Linux system it should be able to be adapted and compiled to work on any other. It may not be easy to do. you may have to contact the developers of that distros community to see eactly what they are doing to get your wireless up.

---

### Post by kneedragger on 2009-01-16
thanks for the info. Is there an easy way to see what driver is used for the wireless?

---

### Post by handydan918 on 2009-01-16
> **kneedragger said:**
> thanks for the info. Is there an easy way to see what driver is used for the wireless?

Open a terminal and do ```
lspci | grep -i net
```

This should reveal any network adapters, wireless or otherwise. Armed with that knowledge, you can ask you best friend, Google.  You may also want to do ```
lsmod
```to list the modules that are loaded on your system with the goofy name (oops, did I type that out loud?)  but I really can't tell you what to look for, other than something that sounds suspiciously wireless.

:popcorn:

---

### Post by kneedragger on 2009-01-16
> **handydan918 said:**
> Open a terminal and do ```
lspci | grep -i net
```


:popcorn:


This one left me with atheros communication inc. AR242x 802.11abg wireless pci adapter.


 ```
lsmod
```


I didn't know what to look for with this one. I didn't see anything saying wireless or anything

---

### Post by handydan918 on 2009-01-17
Seems to be a [launcpad bug on this one]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/289912")...

however, it looks like the best thing is to ```
sudo apt-get install linux-backports-modules-intrepid 
```
Then reboot to make sure the ath5k module is loaded.

---

