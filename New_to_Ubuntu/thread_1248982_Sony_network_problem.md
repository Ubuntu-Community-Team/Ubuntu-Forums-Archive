---
title: "Sony network problem"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by lover_of_sc on 2009-08-24
Hi guys,

I finally managed to get ubuntu installed on my newly purchased Sony vaio W11S1E netbook. I run into problem immidiately with the network adaptor, here is the spec from Sony:

Connectivity Integrated Wireless LAN YES 
Wireless LAN Max. Date Rate (Mbps) 150 (RX)/ 150 (TX) 
Wireless LAN Range (m) max. 100 
Wireless LAN Type IEEE 802.11b/g Draft n 
Integrated Bluetooth (Version) 2.1 + EDR 
Bluetooth Range (m) 10 
Ethernet network 10BASE-T/100BASE-TX 

My system dont seem to find the card at all and I cant find anything on the forum so far... Please help! I am still very new to ubuntu as well.

---

### Post by philcamlin on 2009-08-24
I would recommend using ndiswrapper and the windows drivers.:popcorn:

---

### Post by lover_of_sc on 2009-08-24
Hi there,

Thanks for reply, I actually found another one with the same problem: [http://ubuntuforums.org/showthread.php?p=7409939](http://ubuntuforums.org/showthread.php?p=7409939)

The anwer was to do: *sudo apt-get install linux-backports-modules-jaunty*
but i get an error message saying: could not find package *sudo apt-get install linux-backports-modules-jaunty*

I have the same problem with the ndiswrapper - it cant find the package...

What do I do?? Thx

---

### Post by philcamlin on 2009-08-24
do you have all the sources enabed cause it seems to work for me :confused::confused:

---

### Post by lover_of_sc on 2009-08-24
I may sound like an idiot now but can you actually use the apt-get without a internet connection working on that computer?

---

### Post by lover_of_sc on 2009-08-24
ah sorted the problem, downloaded them on a usb stick and installed them manually-it wooooooorks. :0)

---

