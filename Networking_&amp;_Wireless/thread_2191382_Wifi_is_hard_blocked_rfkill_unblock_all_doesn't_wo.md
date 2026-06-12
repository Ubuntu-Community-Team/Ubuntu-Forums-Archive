---
title: "Wifi is hard blocked rfkill unblock all doesn't work"
date: 2013-12-02
forum: Networking &amp; Wireless
---

### Post by 3thejoker4 on 2013-12-02
I will give you all the information I know:

I had slackware64 14.0, couldn't get wifi to work, decided to erase it and install archlinux, attempted to use cfdisk, deleted everything, followed a common archlinux tutorial youtube video, ran into a problem while trying to install grub, it said something (can't remember now, really sorry), about it not being able to install it, so i just decided to continue with the next step of the installation.
 
When I restarted my pc, lilo NOT GRUB (which is logical, cause I didn't install it) was showing a boot option "linux 3.5.4", which is the kernel i upgraded to from 3.2.29, cause the old one was bugging (freezed sometime). So, i tried the same thing (to erase slackware), but this time with gdisk, which used gpt instead of mbr, it gave me the info of mbr being secured (I think), but that gpt was now being used. So, I go on with the rest of the installation in the same way, but it resulted in the same way.

So, I decided to install ubuntu (13.10 , 64bit). At the beginning of the installation, I thought "I'm just gonna connect to the wifi now, and install the damn thing" but the wifi wasn't enabled. "K I'll just hook it up to my lan, and get wifi working later". Installed ubuntu, started it up, wifi blocked, hardblocked yes, tried rfkill unblock all, the wifi lamp is always on, fn+f2 is the combo for the wifi on my keyboard, doesn't work.

Sorry if this is too long, but I thought I should be thorough because all of this could be helpful to you. By the way I'm sorry, but I don't know why wifi stopped working in slackware64, it did work for a while though.

I hope you can help me, using lan is a viable option, but I want to fix my wlan, I'm quite curious about what caused it to fail.

TL;DR: WLAN doesn't work, WLAN led indicator is on, tried rfkill unblock all, rfkill list all reports it is still hard blocked.

Thanks in advance guys.

---

### Post by Kirboosy on 2013-12-02
Hi I would recommend checking out the following thread.

[rfkill hard block my wireless when I switch it off/on]("http://ubuntuforums.org/showthread.php?t=1781350")

Also you could be suffereing from a faulty or dying WiFi card. What type of computer is it?

Hope that helps
~Caboose

PS You might want to break up your post into neat paragraphs. 

> 
I will give you all the information I know:

I had Slackware 14.0 (64 bit), couldn't get wifi to work, decided to erase it  and install Archlinux. I attempted to use cfdisk and deleted everything. I  followed a common archlinux tutorial youtube video but ran into a problem  while trying to install grub. It said something (can't remember now,  really sorry) about it not being able to install it so i just decided  to continue with the next step of the installation. When I restarted my  pc, lilo NOT GRUB (which is logical, cause I didn't install it) was  showing a boot option "linux 3.5.4", which is the kernel i upgraded to  from 3.2.29, cause the old one was bugging (freezed sometime). So, i  tried the same thing (to erase slackware), but this time with gdisk,  which used gpt instead of mbr, it gave me the info of mbr being secured  (I think), but that gpt was now being used. So, I go on with the rest of  the installation in the same way, but it resulted in the same way. 

I  decided to install ubuntu 13.10 (64bit). At the beginning of the  installation, I tried to connect to the wifi but the wifi wasn't enabled. I thought "K I'll just hook  it up to my lan, and get wifi working later". I finished Installing Ubuntu, started  it up, wifi blocked, hardblocked yes, 

I have tried the following
```
rfkill unblock all
```
The wifi  lamp is always on, fn+f2 is the combo for the wifi on my keyboard,  doesn't work. Sorry if this is too long, but I thought I should be  thorough because all of this could be helpful to you. By the way I'm  sorry, but I don't know why wifi stopped working in slackware64, it did  work for a while though.

I hope you can help me, using lan is a viable option, but I want to fix my wlan, I'm quite curious about what caused it to fail.

TL;DR: WLAN doesn't work, WLAN led indicator is on, tried rfkill unblock all, rfkill list all reports it is still hard blocked.

Thanks in advance guys.

---

### Post by coldraven on 2013-12-02
Before I learned of rfkill I had a similar problem. I fixed it by booting into the BIOS and selecting "Restore Default Settings".
Before you try that make a note or photo of any settings that you might need to reinstate.

---

### Post by 3thejoker4 on 2013-12-02
Eh, I tried a couple of things from the thread you posted, but they didn't quite work. I mean, some of them didn't report any errors, so the commands were executed, but wlan is still hardblocked.

I have a fairly new laptop, just a couple of month's old, I think it's an okay wifi card, would be surprising to be otherwise, but I guess it's possible.

The model is Asus x550CC.

Oh, I also forgot to say (it could be worth mentioning):

this is my output for rfkill list all:

0: phy0: Wireless LAN
     Soft blocked: no
     Hard blocked: yes
1: asus-wlan: Wireless LAN
     Soft blocked: no
     Hard blocked: no
2: asus-bluetooth: Bluetooth
     Soft blocked: no
     Hard blocked: no
3: hci0: Bluetooth
     Soft blocked: no
     Hard blocked: no

I though it might be peculiar to have to wifi thingies (as far as I'm concerned they're thingies, cause I don' really know how to name them).

---

### Post by 3thejoker4 on 2013-12-02
Okay, I will try that now, will report the results.

---

### Post by 3thejoker4 on 2013-12-02
It worked! Brilliant, thank you a lot, both of you. I'm still curious what the problem was in the first place, but considering that I was basically playing around with the mbr, and the bios and everything it could be anything. Thanks a lot guys, it feels nice to connect to the internet without much trouble.

---

### Post by QIII on 2013-12-03
*Moved to* ***Networking & Wireless***

---

### Post by neeraj_nigam on 2014-05-31
hello there i also have the same laptop with ubuntu 14.04 and i also face the same problem my wifi also HARD BLOKED from installtion of ubuntu but it works in windows...
plese tell me how you solve your problem.. thanks in advance

---

### Post by jeremy31 on 2014-05-31
> **neeraj_nigam said:**
> hello there i also have the same laptop with ubuntu 14.04 and i also face the same problem my wifi also HARD BLOKED from installtion of ubuntu but it works in windows...
plese tell me how you solve your problem.. thanks in advance

It is preferred that you start your own thread but please provide the results of ```
lspci
``````
lsusb
``````
lsmod
```

---

