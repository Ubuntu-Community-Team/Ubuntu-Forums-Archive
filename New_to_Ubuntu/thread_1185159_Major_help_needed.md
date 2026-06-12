---
title: "Major help needed"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by shizumasa14 on 2009-06-11
I currently have an Acer Aspire 4730-4516 with Ubuntu 9.04

It runs slow as molasses! I have had the computer for less than 4 months. Any upgrades recomended. I want to replace my graphics card with an NVIDIA gpu, and I want to upgrade to either 4 or 8 gigs of RAM (The 64 bit version can handle 8 gigs right?)

Here are my Specs:

CPU: Intel Pentium dual-core processor T3400 (2.16ghz)
LCD: 14.1 WXGA Acer CrystalBrite
Memory: 2GB DDR2
HDD: 250GB
ODD: DVD Super Milti Double Layer
Modem: 56k
LAN: Giga Lan
Wireless LAN: Acer Nplify 802.11b/g/Draft-N WLAN
O/S: Ubuntu 9.04 "Jaunty"

---

### Post by abhiroopb on 2009-06-11
When you say it runs "slow" can you identify WHEN it is running slowly?

---

### Post by H2SO_four on 2009-06-11
> **shizumasa14 said:**
> I currently have an Acer Aspire 4730-4516 with Ubuntu 9.04

It runs slow as molasses! I have had the computer for less than 4 months. Any upgrades recomended. I want to replace my graphics card with an NVIDIA gpu, and I want to upgrade to either 4 or 8 gigs of RAM (The 64 bit version can handle 8 gigs right?)

Here are my Specs:

CPU: Intel Pentium dual-core processor T3400 (2.16ghz)
LCD: 14.1 WXGA Acer CrystalBrite
Memory: 2GB DDR2
HDD: 250GB
ODD: DVD Super Milti Double Layer
Modem: 56k
LAN: Giga Lan
Wireless LAN: Acer Nplify 802.11b/g/Draft-N WLAN
O/S: Ubuntu 9.04 "Jaunty"

Most people don't report issues having the same specs as you.  Is it safe to assume that Jaunty was running fast at some point?  Regarding the ram, unless you are doing some serious compiling, encoding or VM's anything above the 4GB mark is overkill.  Have you tried any other distro such as 8.1 or Xubuntu?

---

### Post by shizumasa14 on 2009-06-12
It is fast when I first install ubu.  But slow after a day or so.  I have re installed like 7 times now.  Also, it wont connect to my home wireless network anymore (I'm on a friend's Windows computer to post this, so I know it's a computer issue, not my network).

---

### Post by alphacrucis2 on 2009-06-12
> **shizumasa14 said:**
> It is fast when I first install ubu.  But slow after a day or so.  I have re installed like 7 times now.  Also, it wont connect to my home wireless network anymore (I'm on a friend's Windows computer to post this, so I know it's a computer issue, not my network).

It's possible that you some sort of runaway process. From the terminal command line run 

```
top
```

This will show what is using the resources. You can do the same thing using System Administration System Monitor but this uses a lot more resources itself than top. There is also an improved version of top you can run in a terminal called htop. You can install it via

```
sudo apt-get install htop
```

---

### Post by H2SO_four on 2009-06-12
> **shizumasa14 said:**
> It is fast when I first install ubu.  But slow after a day or so.  I have re installed like 7 times now.  Also, it wont connect to my home wireless network anymore (I'm on a friend's Windows computer to post this, so I know it's a computer issue, not my network).

Does something prompt you to reinstall? Do you have resource hungry apps always running? Does it "slow down" after you install specific things?  Did it just stop connecting to wireless all of a sudden? Or after you changed something? Help us help you! Your description is too vague.  Provide examples etc.

FYI, from a clean install with everything running properly, there is no reason why your system will run slower on day 2 or day 3 all by itself.

---

### Post by LowSky on 2009-06-12
> **shizumasa14 said:**
> I currently have an Acer Aspire 4730-4516 with Ubuntu 9.04

It runs slow as molasses! I have had the computer for less than 4 months. Any upgrades recomended. I want to replace my graphics card with an NVIDIA gpu, and I want to upgrade to either 4 or 8 gigs of RAM (The 64 bit version can handle 8 gigs right?)
    

this computer here?
[http://reviews.cnet.com/laptops/acer-aspire-4730-4516/4507-3121_7-33497653.html?tag=mncol;psum](http://reviews.cnet.com/laptops/acer-aspire-4730-4516/4507-3121_7-33497653.html?tag=mncol;psum)


you can only put 4GB of RAM in it, sorry its the PC's max, and its got a built in graphics card, intel to be exact, there is no way to replace it, well there is, but its called buying a better PC.


sorry but you computer cant be upgraded the way you want


and just saying its slow doesn't help, we need examples, like what is slow, what programs do you use, when does the slowdown occur... stuff like that. your hardware is more than enough it should be running fine


and posting the same topic over and over isnt cool
[http://ubuntuforums.org/showthread.php?p=7442621#post7442621](http://ubuntuforums.org/showthread.php?p=7442621#post7442621)
[http://ubuntuforums.org/showthread.php?t=1184162](http://ubuntuforums.org/showthread.php?t=1184162)

---

