---
title: "Wireless on Ubuntu"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by meteoradew on 2011-03-28
First off i would like to say that i am a complete new linux and ubuntu user. With that said, i dual-boot Windows 7 and Ubuntu 10.10. The wireless works fine for Windows but i can only connect through an ethernet cable for Ubuntu. Help?

---

### Post by cbowman57 on 2011-03-28
Without any other info to go on I'll make a leap and guess that you're running a laptop with broadcom wifi.  If so, go into your package manager and install b43-fwcutter, or from a terminal sudo apt-get install bw43-fwcutter.

There will likely be somebody much more knowledgeable than I on such matters but this works for a large majority.  Good luck.

---

### Post by TBABill on 2011-03-28
Can you open a terminal and run the following commands and paste the outputs back here for us to see?

```
lspci
```

```
sudo lshw -C network
```

---

### Post by Cybie257 on 2011-03-28
You can also check the System-> Administration -> Additional Drivers menu item and check there if there is a proprietary driver available that needs to be enabled. I have found that as a working option many times on different laptops. 

-Cybie

---

### Post by MrWES on 2011-03-28
> **cbowman57 said:**
> Without any other info to go on I'll make a leap and guess that you're running a laptop with broadcom wifi.  If so, go into your package manager and install b43-fwcutter, or from a terminal sudo apt-get install bw43-fwcutter.

There will likely be somebody much more knowledgeable than I on such matters but this works for a large majority.  Good luck.

Shouldn't have to do that. If you have connected via an internet cable, there is a good chance the hardware driver is already available. Goto System | Hardware Drivers and see if one it there. If so, activate it and you should be on your way with wireless.

Bill

---

### Post by MrWES on 2011-03-28
> **Cybie257 said:**
> You can also check the System-> Administration -> Additional Drivers menu item and check there if there is a proprietary driver available that needs to be enabled. I have found that as a working option many times on different laptops. 

-Cybie

Well said :)

---

### Post by Locke_99GS on 2011-03-28
I've usually start by blindly installing the linux-firmware-nonfree package which includes many wireless drivers. This has worked for me on a few occasions. On other occasions I've actually needed to know specifically what wireless chipset I was working with, then either found the specific wrapper package for it or found the driver sources elsewhere and compiled them.

If nothing shows up in jockey and the linux-firmware-nonfree package doesn't get your wireless working, definitely do as TBABill recommended earlier and report the outputs of those commands so we can try to direct you towards getting your wireless set up.

---

### Post by cbowman57 on 2011-03-28
Good point!  I told him the cavalry would show up, and you did. I didn't think of the simplest method, been spending some time with Debian lately and things aren't always that easy.

> **MrWES said:**
> Shouldn't have to do that. If you have connected via an internet cable, there is a good chance the hardware driver is already available. Goto System | Hardware Drivers and see if one it there. If so, activate it and you should be on your way with wireless.

Bill

---

### Post by TBABill on 2011-03-28
> **cbowman57 said:**
> Good point!  I told him the cavalry would show up, and you did. I didn't think of the simplest method, been spending some time with Debian lately and things aren't always that easy.

Don't sweat it!! They aren't that easy with Ralink or Atheros devices lately so we'll see what the OP comes back with. For Broadcom devices that is often all it takes, but others sometimes take a bit more work. Regardless, we'll just hope they get online asap.

---

### Post by cbowman57 on 2011-03-28
Yeah, I deal with a Ralink & no wired connection here so I've learned the drill.

---

### Post by fuquam on 2011-03-28
Just out of curiosity what kind of computer are you using? I just bought an Acer Aspire laptop to play around with Ubuntu. Three weeks later I still can't get internet access, wired or wireless. I installed the ndiswrapper module then installed the drivers I downloaded from Acer's website. I still can't get a wireless network to show up and when I plug directly into my router the light on the ethernet port turns off. It came with Windows 7 preinstalled and that works fine (only its Windows). I'm wondering at this point if my laptop is incapable of having a network connection using Linux so that's why I'm curious to know what kind of machine you're using?

---

### Post by 5149.5 on 2011-03-28
> **fuquam said:**
> Just out of curiosity what kind of computer are you using? I just bought an Acer Aspire laptop to play around with Ubuntu. Three weeks later I still can't get internet access, wired or wireless. I installed the ndiswrapper module then installed the drivers I downloaded from Acer's website. I still can't get a wireless network to show up and when I plug directly into my router the light on the ethernet port turns off. It came with Windows 7 preinstalled and that works fine (only its Windows). I'm wondering at this point if my laptop is incapable of having a network connection using Linux so that's why I'm curious to know what kind of machine you're using?

My AAO D255 just worked with ubuntu 10.10. All I had to do was put in my security code for WPA and it was connected.

---

### Post by dcsoldschool53 on 2011-03-29
**I'm sorry ,but I need more information in order to help you. First, what steps did you take to install or connect to your wireless...what did you do. Second, do you have  Ubuntu certified hardware, or components. I know, for a fact, that you should check to see if your system and its components are compatible with Ubuntu first before installing it.**

**For** [B]Ubuntu certified hardware,
[/B][http://www.ubuntu.com/certification](http://www.ubuntu.com/certification)
[B]
For Ubuntu components
[/B][http://www.ubuntu.com/certification/catalog](http://www.ubuntu.com/certification/catalog)

---

