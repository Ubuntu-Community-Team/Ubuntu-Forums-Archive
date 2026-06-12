---
title: "Asus A8V-E Delxue Mobo w/ Marvell libertas wifi problems"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by aberry5555 on 2007-06-10
Hi there, I'm having a couple of problems here using Ndiswrapper.  I have an Asus A8v-e deluxe motherboard that uses an onboard marvell libertas wifi chip. I've had this problem before when I was running on Edgy (recently did a fresh install to feisty), basically what happens is, as ndiswrapper is an included module in the kernel, all I have to do to get it working is

```
sudo ndiswrapper -i mrv8ka51.inf
```

and it will install the driver and seem to be fine.  Once I restart, however, I can use the internet (or any network-reliant app) for a few seconds and then my whole pc will freeze up. 

I've managed to fix this in edgy before but that was by uninstalling ndiswrapper in synaptic and installing the newer version from source on the ndiswrapper site. Unfortunately, however, now 
ndiswrapper seems to be built in to the kernel and I have NO idea, bar rebuilding the kernel, how to upgrade ndiswrapper.

Anyone had the same experience or at least some ideas?

Thanks :)

---

### Post by bigken on 2007-06-11
Im having the same problem as soon as I try to browse the internet the whole thing freezes :(

My board is the P5GD2 Deluxe

---

### Post by aberry5555 on 2007-06-11
I'm going to try and compile it from source off the ndiswrapper site and uninstall any ndiswrapper that's already there, though I'm not sure it's possible since it's already compiled in the kernel. That seemed to work in Edgy. For such a heavily used component it should really be a much newer version in the Repos and especially if it's inbuilt.

Also does anyone know if there are repositories I can add that will let me install a latish kernel without ndiswrapper installed and that will still work with edgy? I'm not a complete newbie but I've never compiled a kernel myself and, lame as it sounds, I havn't got the time to learn.

Thanks in advance, I hope!!

---

### Post by aberry5555 on 2007-06-12
Big Ken, try this: [http://ubuntuforums.org/showthread.php?t=470829](http://ubuntuforums.org/showthread.php?t=470829)

---

