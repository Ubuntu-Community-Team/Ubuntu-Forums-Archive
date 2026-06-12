---
title: "ati drivers installed but not active"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by franticmonkey on 2009-12-30
Hello folks i just installed ubuntu 9.10 i386 got everything working apart from ati drivers for some reason theyve installed but not activated. Using an ati hd3850 card 
Im still pretty new to linux so it be something simple that im not doing or just missed something out included a screenshot of message i get incase its needed thanks

---

### Post by MelDJ on 2009-12-30
try uninstalling the driver and use the driver from the ati site

---

### Post by franticmonkey on 2009-12-30
ty ill give it a go

---

### Post by Redundant Username on 2009-12-30
I had this problem to, but i fixed it. The new ati drivers probably don't support your card, so it's best to use envyng.
 Go to the terminal and type:
```
sudo apt-get install envyng
```
and then type envyng into the terminal to run the installer.

---

### Post by Mark Phelps on 2009-12-30
> **Redundant Username said:**
> ... The new ati drivers probably don't support your card, so it's best to use envyng...

You're missing something here ... All the envy programs do is provide a front-end for doing ATI & Nvidia driver installations/removals.  The drivers that get installed are the same ones that exist at the ATI & Nvidia sites. The envy developer does not provide his own video drivers.  

When I was able to use restricted drivers, I confirmed that (at least, for the ATI drivers).

So, if the ATI drivers "don't work", envy will not solve that.

---

### Post by Redundant Username on 2009-12-30
But envyng installs the proper version for your card.

---

### Post by halitech on 2009-12-30
> **Redundant Username said:**
> But envyng installs the proper version for your card.

hopefully it does

Looks like the HD3850 is supported so downloading the file from here, make it executable, open a terminal and run 
```
sh ./ati-driver-installer-9-12-x86.x86_64.run
```
then run ```
sudo aticonfig --initial
``` and reboot.

Driver download:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

Driver install instructions:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat911-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat911-inst.pdf)

---

