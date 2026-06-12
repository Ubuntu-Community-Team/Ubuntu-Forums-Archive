---
title: "Network Adapter Doesn't work? ~Broadcom Wireless~"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by jamorama on 2008-08-05
Ok, I am a complete beginner when it comes to other OS. My Wireless adapter is Broadcom 802.11 b/g WLAN, and I cannot get it to work on Ubuntu, which I installed with wubi. If anyone can please give me a complete how-to, it would be nice... 

I've read other posts, but could not understand stuff such as ndiswrapper/ terminal, etc...

Please Help! Thanks A Lot!

---

### Post by cdtech on 2008-08-05
First thing you need to do is go to "System > Administration > Synaptic Package Manager" and click on search. Type in "ndiswrapper" within the search box and you should see a list of ndiswrapper programs:
```
ndisgtk
ndiswrapper-common
ndiswrapper-utils-1.9
```

Select to install all of those....

Next bring up a terminal and type:
```
lspci | grep -i network
```

This will tell us what wireless card you have...

Report back........

---

### Post by warmaster4z2 on 2013-02-25
It took me several days to solve this problem and the only way you stand a chance, is if you use an ethernet cable or wireless adapter to get wifi on your computer. Once you do that you can run a simple command to get the packages you need but for me I just enabled the broadcom proprietary driver and everything worked for the most part

---

### Post by oldfred on 2013-02-25
Thread Closed. Very old.

---

