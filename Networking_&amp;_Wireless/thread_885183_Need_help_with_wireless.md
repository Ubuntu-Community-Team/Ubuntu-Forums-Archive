---
title: "Need help with wireless"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by mordecai83 on 2008-08-09
hello,

I'm having trouble with getting my wireless to work. I'm running hardy and have an intel 4965AGN on my laptop. I have tried to search how to get it working but it seems it should work "out of the box", however with me it did not. I have tried installing the windows driver with ndiswrapper and this is what i get:
```
netw5x32 : driver installed
	device (8086:4229) present (alternate driver: iwl4965)

```
however when I do an iwconfig it doesn't show any wireless options:
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

pan1      no wireless extensions.

```
as you can see it doesnt have a wlan0. On the ndiswrapper site it says that you should remove the alternate driver cuz that's the one that gets loaded. And i think that's the one that is the problem. So how do i unload or remove the iwl4965 driver? i tried blacklisting but that doesn't work.

Also i tried the instructions on [this]("http://ubuntuforums.org/showthread.php?t=872663") thread but it only gets me as far as showing my card under wlan0 when i do an iwconfig. Then wireless is enabled in the network manager but i cannot see any networks. And when i reboot it all is undone.

I would really appreciate some help here because im stuck, i don't know what i could try next. Plz be as clear as possible if you give instructions cuz im a bit of a noob (this is my first time using linux)

thanx in advance

---

