---
title: "[SOLVED] Beginner problems with Wireless. Please help!"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by ElTesorillo on 2008-06-29
Hello, I am brand new to ubuntu and have been enjoying it for the most part. When I first installed it, my wireless was working fine but about 5 days later, ubuntu wont connect to the wifi. It reads the network and tries to connect but never makes it. I have a Dell Vostro 1500 with a Intel-N wireless card. Thank you for all of your help in advance.

---

### Post by pytheas22 on 2008-06-29
What kind of wireless card do you have?  If you don't know, please post the output of:

```
lspci
```

Have you installed any updates lately?

You may also want to try using something other than Network Manager, like [wicd]("http://wicd.sourceforge.net"), to see if that will connect you.

---

### Post by ElTesorillo on 2008-06-29
I have an Intel Corporation PRO/Wireless 4965 AG or AGN Network connection (rev 61). How do you install widc?

---

### Post by ElTesorillo on 2008-06-29
I should be more specific. When I try to reload the package manager in order to get wicd, an error occurs and it doesnt allow me to install wicd. And I have downloaded new packages lately.

---

### Post by pytheas22 on 2008-06-29
If you click [here]("http://downloads.sourceforge.net/wicd/wicd_1.4.2-1-all.deb?modtime=1203246585&big_mirror=0") you should be able to download the installer for wicd.  Just run it and you should be all set.

(It will force you to uninstall Network Manager, with which wicd is incompatible.  If at any point in the future you want to get Network Manager back, just type:
```

sudo apt-get install network-manager-gnome
```)

If wicd doesn't solve the problem, please try connecting a couple of times to your network and then immediately post the output of:
```

dmesg | grep -e wlan -e dhc
```

---

