---
title: "I need some help on getting my wireless drivers set up for Ubuntu 7.10."
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by shinjiKobiyashi on 2007-11-12
My wireless adapter is called Belkin N wireless USB adapter and if anyone can help me with this problem that would be great.
Thank You!

---

### Post by reckless2k2 on 2007-11-12
post the results of this from the terminal:

```
lspci -v
```

More than likely you will need a driver download from this site below unless you have the windows driver disk.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)

you'll have to install using ndiswrapper. ndiswrapper is already in ubuntu but you have to add a couple of packages to make it work: in synaptic add these packages:

ndiswrapper-utils-1.9
ndiswrapper-common

this is on the disk if you don't have a net connection. once you have the .sys and .inf driver for the device in your home folder, from the terminal type these things.

this will add the driver:
```
sudo ndiswrapper -i THEDRIVER.inf
```

this will tell you if it's installed (should say present):
```
sudo ndiswrapper -l
```

```
sudo depmod -a
```

```
sudo modprobe ndiswrapper
```

final insertion of module:
```
sudo ndiswrapper -m
```

open modules file and add "ndiswrapper" at the bottom:

put ndiswrapper at the bottom
```
gksudo gedit /etc/modules
```

save it. 

now when you open network connections you will see wlan0. set it up and you will be fine every boot. with wifi. make sure to enbale the wlan0 connection and disable the eth0.

---

### Post by shinjiKobiyashi on 2007-11-13
Thank you very much i will try this now.

---

### Post by shinjiKobiyashi on 2007-11-27
When i go to this site it dont have a link to my drivers it lists my adapter but it dont have a link for my drivers. If you could tell me another link or something else that would be gerat Thank You

---

### Post by reckless2k2 on 2007-11-27
Well if you have the driver CD from the vendor then you can copy the drivers from the CDROM. You want to navigate to the XP folder of the disk and grab the .inf and .sys files from there and then dump them in your home directory. 

If you don't have the driver CD, you will need to post the results of lspci -v so we can find your drivers.

---

### Post by TimeDragon on 2007-11-28
I did it like this and sometimes it works like a charm but most times it just don't connect....
Now I have to restart the pc about 5 times before it returns to life
I'm going crazy does anybody knows how to solve this?

---

### Post by reckless2k2 on 2007-11-29
it really depends on your hardware. what did you do? do you mean you followed my tutorial? do you have the same hardware? sounds to me like you might have a broadcom chip and might be better using the broadcom cutter and firmware. i'm not sure of your situation without more details.

---

