---
title: "Question concerning dual-booting and running programs from WINE."
date: 2009-07-22
forum: New to Ubuntu
---

### Post by mersaultnpepper on 2009-07-22
First off, I haven't even bought the laptop I want to dual-boot from, but I do have a model in mind.
Second off, this may or may not be the noobiest question that could be, but I am a human being, and any help would be appreciated. :) Trust me.
Anyway, if you partition your drives etc. etc. so you can dual-boot, can you run a Windows program, that's been installed in Program Files on the first partition, when you are booted up in Ubuntu solely using WINE?

---

### Post by alexlafreniere on 2009-07-22
No, you would have to run the installer in WINE and have a second instance running in your Ubuntu partition.

---

### Post by bacil on 2009-07-22
But  you can still run windows in VirtualBox or qemu from your partition and use what ever you have installed there. 

here is simple how to

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

it is for older version of ubuntu, but it works as well in jaunty

---

### Post by mersaultnpepper on 2009-07-22
> **alexlafreniere said:**
> No, you would have to run the installer in WINE and have a second instance running in your Ubuntu partition.
Hm. Yes, that is what I wanted to know.
Does that make dual-booting redundant then? Or is it truly worth it?

---

### Post by bacil on 2009-07-22
There are some situation when i need native widows. eg.logging to the network while authenticated by certificate. so its not redundant, but i guess you can live without it. depends what you going to use your windows for

---

### Post by mersaultnpepper on 2009-07-22
Would it seem logical to install all games on a Windows partition and mostly use Ubuntu?
A part of me wants to just do a clean install of just Linux... but a more naggy part of me just can't let go of that Windows install...
The laptop I want should have a 500g HD, so dual booting would be appropriate, right?

---

### Post by Mark Phelps on 2009-07-22
> **mersaultnpepper said:**
> Does that make dual-booting redundant then? Or is it truly worth it?

Two problems you're going to face if you choose Wine over dual-booting:
1) Not only does Wine not handle ALL MS Windows products, there are quite a few products and versions that do not work.  You need to check the CodeWeavers Application Compatibility database site, checking for your specific apps and versions.  If they are all rated Platinum or Gold, you're good to go; if they are Bronze or Garbage, you're wasting your time with Wine.
2) Games are a particular problem in Wine because you need good 3D graphics acceleration to use them, and 9.04 (thanks to AMD/ATI) dropped such support for LOTS of ATI cards, and Intel chipsets have problems as well.

So, basically, if you are going to continue to rely heavily on MS Windows, dual-boot is your best option.

---

### Post by mersaultnpepper on 2009-07-22
> **Mark Phelps said:**
> Two problems you're going to face if you choose Wine over dual-booting:
1) Not only does Wine not handle ALL MS Windows products, there are quite a few products and versions that do not work.  You need to check the CodeWeavers Application Compatibility database site, checking for your specific apps and versions.  If they are all rated Platinum or Gold, you're good to go; if they are Bronze or Garbage, you're wasting your time with Wine.
2) Games are a particular problem in Wine because you need good 3D graphics acceleration to use them, and 9.04 (thanks to AMD/ATI) dropped such support for LOTS of ATI cards, and Intel chipsets have problems as well.

So, basically, if you are going to continue to rely heavily on MS Windows, dual-boot is your best option.

Ok, in that case, I'll definitely dual-boot. Thanks guys. :)
I can't wait till I get my laptop, now!

---

