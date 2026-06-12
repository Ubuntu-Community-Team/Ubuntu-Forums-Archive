---
title: "Wireless capability suddenly missing"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by sayeo87 on 2008-05-04
Hi, I am using 8.04 and I got my wireless (BCM4312 rev 01 on HP dv6000 laptop) working perfectly with ndiswrapper following this very comprehensive guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff). For a few days it ran perfectly - when I was plugged in with my wireless card on it used the wired connection, I could turn on/off my wireless or restart my laptop and the wireless would be fine etc. 

But yesterday, for no apparent reason, when I booted into Ubuntu the wireless capability wasn't even present in the network manager. (it wasn't just greyed out, it wasn't even there) iwconfig said something like "no wireless detected" for both lo and eth0 too. Is this a common problem? Will I be forced to reinstall my drivers every few days?

---

### Post by sayeo87 on 2008-05-04
Anybody?

---

### Post by btermeli on 2008-05-04
Hi,

Today I had the same problem...
I was using 8.04 without any problem but I re-installed 7.10 because of  my webcam problem. And 7.10 even doesn't show my wireless properties.When I restarted showed me the available networks for few seconds and disappeared again... 

If somebody help us,I will be glad...

---

### Post by sayeo87 on 2008-05-04
Well if you reverted back to 7.10 you probably have to blacklist and reinstall your drivers again to make it work. My problem is that I didn't make any changes to my system whatsoever.....my wireless just disappeared out of the blue! =(

---

### Post by Ayuthia on 2008-05-04
> **sayeo87 said:**
> Hi, I am using 8.04 and I got my wireless (BCM4312 rev 01 on HP dv6000 laptop) working perfectly with ndiswrapper following this very comprehensive guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff). For a few days it ran perfectly - when I was plugged in with my wireless card on it used the wired connection, I could turn on/off my wireless or restart my laptop and the wireless would be fine etc. 

But yesterday, for no apparent reason, when I booted into Ubuntu the wireless capability wasn't even present in the network manager. (it wasn't just greyed out, it wasn't even there) iwconfig said something like "no wireless detected" for both lo and eth0 too. Is this a common problem? Will I be forced to reinstall my drivers every few days?

Next time this happens type the following:```
lsmod|grep -i -e b43 -e bcm43xx -e ssb -e ndiswrapper
```
lsmod will list all your active modules and the second part only will grab the modules starting with b43, bcm43xx, ssb, and ndiswrapper.  I am thinking that ndiswrapper is not loading.  If that is the case, you can always load the module by typing:```
sudo modprobe ndiswrapper
```

---

### Post by btermeli on 2008-05-05
> **sayeo87 said:**
> Well if you reverted back to 7.10 you probably have to blacklist and reinstall your drivers again to make it work. My problem is that I didn't make any changes to my system whatsoever.....my wireless just disappeared out of the blue! =(

but it is unlogical, I was using 7.10 without any problem and updated it online to 8.04. I couldn't get webcam support and in the forum they recommended me to switch back to 7.10. I formatted and installed 7.10 again and now I can't connect... I dont want to waste more time...I made the same process as I did first for 7.10 why did it work that time but not now????

---

### Post by btermeli on 2008-05-06
how can I blacklist???can u explain a little? I am a newb...

---

### Post by Ayuthia on 2008-05-06
> **btermeli said:**
> how can I blacklist???can u explain a little? I am a newb...Blacklisting makes sure that a particular module does not load up at boot.  The file is called /etc/modprobe.d/blacklist.  For example, if you wanted to blacklist ndiswrapper, you add this:
```
blacklist ndiswrapper
```.

You can modify the file by:
```
gksu gedit /etc/modprobe.d/blacklist
```

---

### Post by btermeli on 2008-05-06
I did it but the result is the same.
I can see the networks when I click manual settings but cant connect...
First my webcam problem and now wireless problem, I lost all my desire to use linux...I tried to install fedora with some suggestions but installation  freezes... 
may be it ll be easier for me to learn how to uninstall ubuntu from my system...
anyway thanx for ur helps and replies...

---

### Post by cyber_rigger on 2009-06-01
> Is this a common problem? I just got a report for a Dell Laptop. The wireless just quit working for no apparent reason.

It uses the same  BCM4312 rev 01.

Avoid Broadcom.

---

### Post by john_g on 2009-08-16
Wireless just stopped working about a month ago on my compaq using hardy 8.04.3 LTS.  the chip is a broadcom 4306 and I am using the b43 driver.  since this happened after an update I tried the older versions of the kernel.  going back 2 update versions to  2.6.24-22-generic  brought back wireless.

---

