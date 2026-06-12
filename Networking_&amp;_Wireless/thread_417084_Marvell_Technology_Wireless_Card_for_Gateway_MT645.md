---
title: "Marvell Technology Wireless Card for Gateway MT6456"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by xflatlinex on 2007-04-21
Hi, I have a Gateway MT6456 notebook with a Marvell Technology wireless card. I am running Ubuntu7.04 AMD64 and cannot for the life of me get a wireless driver to work.  I have what I believe is the .inf driver file from my windows partition but when I try to add it using NDIS it will not add, no error message, nothing, it just doesnt add. Here is the output of my card specs from xterm

05:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
        Subsystem: Marvell Technology Group Ltd. Unknown device 2a08
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at c0310000 (32-bit, non-prefetchable) [size=64K]
        Memory at c0300000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

I think that this is correct. Anyone please throw some ideas my way or any suggestions would be awsome.
Thanks

---

### Post by smartboyathome on 2007-04-21
You could try looking in the Restricted Drivers Manager (system>administration>restricted drivers manager). If it is in there, it is not supported.

---

### Post by bdogg64 on 2007-04-21
You could try installing and using ndiswrapper and see if that works

---

### Post by xflatlinex on 2007-04-21
It is not a restricted driver, I checked that and I am using NDIS Wrapper and when I select my .inf file from my windows partition and click add, I get nothing, as in nothing appears in the box of drivers.

**Update**
Now I am getting the driver is already installed, do I need to restart my laptop or anything?

---

### Post by bdogg64 on 2007-04-21
after you run 

```
sudo ndiswrapper -i file.inf
```

you should run this to see if its installed

```
sudo ndiswrapper -l
```

if it is then you run this so it detects it at boot

```
sudo ndiswrapper -m
```

then you run this to load it up in your current session

```
sudo modprobe ndiswrapper
```

Then check your network manager to see if it detects wirless networks and can connect

---

### Post by xflatlinex on 2007-04-21
Yep I am getting invalid driver when I do that, so obiously I have the wrong driver.  I will look around, thanks

---

### Post by xflatlinex on 2007-04-23
Does anyone else have any other suggestions?
Thanks

---

### Post by bdogg64 on 2007-04-23
Where did you get your driver files from? You could try downloading another set of windows drivers to use with ndiswrapper

---

### Post by SixedUp on 2007-04-23
> **xflatlinex said:**
> Does anyone else have any other suggestions?
I just followed the instructions under the title "Install Windows driver" on this page ([http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)), which got me a valid driver install image from a 3COM site.  I took the XP drivers from that, and then installed the ndiswrapper utils using synaptic, which allowed me to install the drivers.

I then followed the instructions bdogg64 posted, and I now have a working Marvell card. I'm still fighting with my access points WPA security, but at least I have the basic hardware working now. I can see light at the end of the tunnel :) 

UPDATE: Now fully working on wireless ... turns out that my problem with WPA was down to an inability to type my passphrase reliably :)

Cheers
Richard

---

### Post by xflatlinex on 2007-04-24
Hmm, I followed that guide and get a FATAL error when I do the
modprobe ndiswrapper
For some reason I am thinking that they tried to make this driver ONLY available for Vista, but I cant stand Vista  .  Hopefully I can find another driver and try this again.

EDIT**  I am getting the following after installing the driver

josh@jgwUbuntu:~/Desktop$ ndiswrapper -l
yk51x86 : driver installed
        device (11AB:4352) present (alternate driver: sky2)

Anyone know if this is telling me to use a sky2 driver?

---

### Post by Jouke74 on 2007-04-24
Nope, Sky2 was your previous failed driver. This one seems to work.
Do check that Sky2 is not loaded anymore by the Kernel (dmesg command).
Otherwise remove it (how to is on ndiswrapper site).

---

### Post by xflatlinex on 2007-04-24
So do I need to remove the old driver before the new one will work?
I never installed a driver to begin with though, the Marvell driver is the first one, unless Ubuntu installed one by default, or NDIS wrapper installed one.
thanks

---

### Post by xflatlinex on 2007-04-24
I am looking on the NDIS site and cannot seem to find how to remove the old driver, please inform me. THank you

---

### Post by bdogg64 on 2007-04-24
> **xflatlinex said:**
> I am looking on the NDIS site and cannot seem to find how to remove the old driver, please inform me. THank you

```
sudo ndiswrapper -e yk51x86
```

---

### Post by xflatlinex on 2007-06-21
Anyone come up with a solution for this issue yet?  If you have a MT6456 Gateway , and you have the wireless working, please, oh please, help me fix this issue.
thankyou

---

### Post by SpiritIsReality on 2007-10-17
howdy
blaquesmith0 has a working wireless
[http://ubuntuforums.org/showthread.php?t=575785&highlight=mt6456](http://ubuntuforums.org/showthread.php?t=575785&highlight=mt6456)
I have an mt6456 , installing 7.04 now. 
another link, to the wiki, has mt6456 listed
[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

trails

---

