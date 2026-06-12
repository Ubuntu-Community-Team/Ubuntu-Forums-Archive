---
title: "Virtual box Karmic 32 bit printing and Adobe Air problem"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by dndrich on 2009-11-20
Ubuntupals:

I recently tried to install Adobe Air and Times Reader on a Karmic 64 bit computer. I was not successful. But, Adobe Air and Times Reader work fine on another Karmic computer I have running 32 bit. So, I thought, why not run Karmic 32 bit inside a virtual box on my 64 bit machine. So, as strange as it sounds, I now have a perfectly running Karmic 32 bit installation in virtual box on a Karmic 64 bit host computer. Despite this, there are two odd issues. First, I can't print to my network HP OfficeJet 6500 through the virtual Karmic. I have installed HPLIP gui, and it sees it no problem, but it won't connect. The host prints fine. Next, Adobe Air will not install in the virtual environment for reasons beyond me. I have the guest OS all updated, and restricted extras installed. Any ideas here?

---

### Post by dca on 2009-11-20
Have you tried tweaking this how-to for 64bit install of Air?
 
[http://kb2.adobe.com/cps/408/kb408084.html#Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04](http://kb2.adobe.com/cps/408/kb408084.html#Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04)
 
...for the reader thing, not too familiar you may try and see if it's compatible with nspluginwrapper
 
[http://plugindoc.mozdev.org/linux-amd64.html](http://plugindoc.mozdev.org/linux-amd64.html)
 
nspluginwrapper usually after install, you issue nspluginwrapper -i (path to plugin) command and you can run 32bit plugins in 64bit Linux.

---

### Post by dndrich on 2009-11-20
Thanks for the reply. I have tried those things for Adobe Air. Just can't get the Times Reader to run. So the thought was to do it in a virtual box, and no success, sadly.

---

