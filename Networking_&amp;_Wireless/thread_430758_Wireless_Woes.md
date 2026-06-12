---
title: "Wireless Woes"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by Krymore on 2007-05-02
I'm running Fiesty on a Dell Latitude D610 with a BCM4309.  I've been trying to get the wireless card to work for months (could never get it to work in Edgy either) and I just don't know what else to do.  I tried the bcm43xx-fwcutter and that seemed to do absolutely nothing.  I've tried all the ndiswrapper HowTo's I could find, although none of them seemed to be specifically for the 4309, and none were successful.  Through a series of unfortunate circumstances I can only use my laptop to connect to wireless networks, meaning that since my wireless card isn't playing nice with Linux, I can only get stuff on it by downloading things on my Win2k PC and transfering it via iPod.  I no longer have the XP disk, so unless I can figure out some way of finally getting this working it seems like my only options would be to buy a new copy of XP (do not want) or buying a second wireless device that hopefully decides to play nice with Ubuntu.  Neither of those sound particularly appealing to me, so can anyone give me some insight as to what I should do to get this thing working?

---

### Post by Dr. No on 2007-05-04
I also have a Dell Latitude D610 with Broadcom 4309. I am also using Feisty.

The Wifi LED was never on. I just found something:

I have removed the bluetooth hardware. Then I did put the laptop into hibernate mode and then started again. Just before the password screen shows up the LED is ON. The very first time. After login the eth1 interface works. It can be configured and connects to my AP. After the laptop is switched off and rebooted it doesn't work anymore. 

One needs to boot, login, then hibernate, then start again. Crazy.

Dr. No

---

