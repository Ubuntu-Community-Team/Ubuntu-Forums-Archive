---
title: "Beginner - wifi not working after install ubuntu 20.04 LTS / Lenovo"
date: 2021-04-19
forum: Networking &amp; Wireless
---

### Post by josefjuch on 2021-04-19
Hi,
I tried to install WIFI driver by couple manuals but I was not successful.
Ethernet is working correctly without any settings. 
I put here some info and thanks everyone for a help.

[IMG]https://i.ibb.co/8rybKdW/all.png[/IMG]
 
sudo dmidecode | less > [ATTACH]288344[/ATTACH]

---

### Post by CelticWarrior on 2021-04-19
Welcome.

This is the sticky thread you should have read: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

> [COLOR=#000000]I tried to install WIFI driver by couple manuals but I was not successful.[/COLOR]

That being the case you should also post what you did.

---

### Post by josefjuch on 2021-04-19
Oh. sorry.

First commands don't help with restart --> [ATTACH]288345[/ATTACH]

---

### Post by praseodym on 2021-04-21
Huh, no device shown. Lets see

```
lspci -nnk
cat /sys/bus/sdio/devices/*
cat /sys/bus/sdio/devices/*/uevent
```

---

### Post by josefjuch on 2021-04-22
Hi, thanks for reply.
I am idiot. Problem was in disabled wifi in BIOS. I don't know how it is possible but in any case I didn't set it manually ... why should I did ...
One day I was fighting with Linux Manjaro but booting into system was very random and with erors etc. I tried a lot of settings and recommendations. 
Second day I lost with Linux Mint ... installation was without problems but booting and loading OS was similar as in Manjaro case. 
Third day I successfully installed Ubuntu on the first time and everything works instead of WIFI(solved) and Touchpad.
My mistake that I didn't check WIFI in BIOS but in live OS it was working so I have different opinion about root cause. 

Now it looks that I have issue only with touchpad but I will create new topic.
Once again thanks.

---

