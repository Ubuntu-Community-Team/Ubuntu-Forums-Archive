---
title: "Problems installing Edimax USB Wireless"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by Tdonohue on 2007-01-13
I am a new user to Ubuntu.  I am trying to install a wireless internet on Dell Inspiron 6000 laptop and cannot make it past what are probably the easiest steps.  I have a choice of a zyxel g102 and a Belkin (model f5d7010) cards, or a edimax 7318ug USB.  

I tried the Zyxel first with Ndiswrapper, but the card wouldn't show up using command 'lspci'.  So then I found that there were Debian linux drivers on the cd for the Edimax USB adapter.  The readme doesn't seem to make sense.

Build Instructions:  
====================
For 2.4 series kernel:
a. $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.
    
b. Use 'chmod' command to change access right of following script files :
   'load', 'unload', 'Configure'
 
c. run 'cp Makefile.4 Makefile'

d. $make config         # config build linux os version

e. $make all            # compile driver source code

f. $cp rt73.bin /etc/Wireless/RT73STA/	# copy firmware
  
g. $load                # load/insmod module(rt73.o)

Note: Script functionality:
    load            load module to kernel
    unload          unload module from kernel
    Configure       retrieve linux version
 
For 2.6 series kernel:
a.  go to 'STA/Module' directory.
    run 'cp Makefile.6 Makefile'
b. $make all
c. cp rt73.bin /etc/Wireless/RT73STA/	# copy firmware
d.  run '/sbin/insmod rt73.ko'  (as root)
        '/sbin/ifconfig rausb0 inet YOUR_IP up' 

I can unzip the file (untarball?), but can't go farther.  I can't go into a /module directory.  It doesn't seem to exist.  'cp Makefile.4 Makefile' doesn't do anything, says no such file.  there is only  rt73.ko rt73.bin load unload readme and some .dat file when i "ls" in this directory.

I assumed the Edimax with the linux drivers would be the easiest, but I can't understand what I'm doing wrong.  Can someone please help me get any of these wireless options working?  My ability to figure this out on my own is too difficult without having internet in Linux and no printer (trying to read about in windows, restart, log into Linux and apply it by memory. 

Any advise, regardless of the result, is graciously appreciated.  Thanks in advance.

---

### Post by rodica.balasa on 2008-01-18
I managed to make it work in gutsy, with edimax dirvers, here is the howto:
[URL="http://www.len.ro/work/tools/old-new-i8000-2"]
http://www.len.ro/work/tools/old-new-i8000-2[/URL]

---

### Post by jeffus_il on 2008-01-18
Try not to use the windows drivers with ndiswrapper, the native Linux drivers are better.
The Edimax EW-7318Ug uses a chip made by Ralink and needs the rt73usb kernel module as a driver.
 This comes with Ubuntu, I have the 2.6.24-4-generic kernel.

first ```
do lsmod | grep rt73
``` to see if the module is loaded into memory.
If not do a ```
sudo modprobe rt73usb
```
type ```
iwconfig
``` to see the device name
and proceed with your regular network configuration.

---

