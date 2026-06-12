---
title: "new HP mini"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by jaceh14 on 2010-01-21
hey all, i just got myself a new hp mini 210, and i'm dual booting windows 7 and ubuntu 9.10. i have a couple of driver issues in ubuntu. one is that it is not recognizing my wifi hardware, and i'm just curious if anyone else has this problem or if anyone has any tips on getting this to work. also my touchpad is working, but the left and right buttons don't. any tips would be greatly appreciated. thanks a bunch!

jace

---

### Post by mikewhatever on 2010-01-21
It would help if you post more info about your wireless and touchpad then hp mini 210. If you don't know these specs, run **sudo lshw**, or install hardinfo or similar.

---

### Post by JiuJitsu500 on 2010-01-22
I have an HP mini 110 and after pdating through a wiredconnection and getting all that straight.... my Wifi still didn't work. My friend had the sameissue with an HP 1000... Something about UNR and wifi with HP don't jive at first...

But, try going to synaptic package manager and look up "bcmwl" and find the "bcmwl-kernel-source." Install that and reboot. Alternately, in a terminal "sudo apt-get install --reinstall bcmwl-kernel-source" and reboot.

It worked on mine and the buddy's... if not there are other options gimme a minute and I'll post the link (it's in the Ubuntu webpages).

---

### Post by JiuJitsu500 on 2010-01-22
[Here]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks") it is. But, because the 210 is new, it's not listed :(

But, try the 110 fix because I think the wifi hardware is the same :)

As for the touchpad... I do not know..... Hope I helped with the wifi though...

---

### Post by MsKK on 2010-01-22
I also have a HP Mini 210 and also had the problem but I solved it easily by going to System > Hardware Drivers and then the comp scanned and offered to install a Broadcom driver which works perfectly :) 

With the touchpad, however, I still have the same issue as you

---

### Post by cbrman on 2010-02-13
The touchpad works this way:

          $ sudo su


          # echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe


          # reboot
(via: [http://greendevnet.blogspot.com/2009/10/ubuntu-910-karmic-koala-no-touchpad.html](http://greendevnet.blogspot.com/2009/10/ubuntu-910-karmic-koala-no-touchpad.html))

The wiffi is in progress. I'll do it!

---

### Post by Bonita Applebum on 2010-02-14
Testimony & Thanks:

I purchased the HP Mini 210-1091 yesterday, and set up dual-boot w/Windows 7 and Ubuntu 9.10.  Using the fixes described in this thread for the wifi (special thanks to Jiu Jitsu) and touchpad, I've found that everything works like a charm!  

For those who might be on the netbook market, I've also had very recent experience w/ the Acer Aspire One 751h, which had a nightmarish set of required fixes, given the GMA500 chipset it was cursed with.  Even with the fixes, video on the 751h is less than ideal.  On the Mini, however, it's just right.

---

