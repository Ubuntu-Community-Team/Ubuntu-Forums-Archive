---
title: "[SOLVED] Total noob help, Dell D500 wifi issues"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by creepface on 2008-09-06
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Okay, so I got this guy in this machine, and I can NOT make it to work, after reading guides and how-tos ive failed on my own.

please help me?

---

### Post by creepface on 2008-09-06
bump

---

### Post by creepface on 2008-09-06
anyone out there?

sudo ifconfig wlan0 up

no such device flag thing comes up.

halp

---

### Post by creepface on 2008-09-06
does anyone use this forum?

ive looked everywhere and i still cannot find a fix...

---

### Post by creepface on 2008-09-06
help, there is no way to use this notebook outside of my home without enabling/installing the wifi system

---

### Post by creepface on 2008-09-06
Ive tried most everything
this is my first install of ubuntu
someone HAS to have had this same issue and can help me out, all the tutorials and how-to's dont work...

I dont want to reinstall windows!

---

### Post by falcon61102 on 2008-09-06
Those cards are imfamous for having some issues out of the box with Ubuntu but once you install the drivers they work great.  If you could, post the results of:
```
sudo lshw -C network
```

That will give some details on the hardware so we can get this fixed.

---

### Post by falcon61102 on 2008-09-06
Also, if you can remember, list which How-To's you tried.  

Depending on what all you did in each How-To, you may inadvertantly caused a conflict which is now causing it to not work so we'll have to back track a bit and then fix everything.

---

### Post by creepface on 2008-09-06
well i got the card working but it wont accept my SSID password.

wtf

---

### Post by falcon61102 on 2008-09-06
Do a search for in the forums for WPA or WEP and you should come back with some threads that may help you with that.

---

### Post by creepface on 2008-09-06
> **falcon61102 said:**
> Also, if you can remember, list which How-To's you tried.  

Depending on what all you did in each How-To, you may inadvertantly caused a conflict which is now causing it to not work so we'll have to back track a bit and then fix everything.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)

this one got the wifi card "working"

im currently looking for the WEP fix thing.

as this is a paperweight without wifi

---

### Post by falcon61102 on 2008-09-06
You did this command during the install?
```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Also, take a look at this page:
[https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager)

Near the bottom you'll see a section about Hidden SSID's, that may be someting to look at.

---

### Post by creepface on 2008-09-06
> **falcon61102 said:**
> You did this command during the install?
```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Also, take a look at this page:
[https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager)

Near the bottom you'll see a section about Hidden SSID's, that may be someting to look at.


my SSID isnt hidden and when i ```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
``` i get "ENABLED=O"
as a result

now the wificard has obtained a 92% signal from the router, and properly displays the SSID but it is not accepting the WEP password

its 5 letters, and ive tested the password on 2 other computers (vista+xp) and they are both using that password now (how im typing to you) so the WEP key is not incorrect.

---

### Post by creepface on 2008-09-06
> **creepface said:**
> my SSID isnt hidden and when i ```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
``` i get "ENABLED=O"
as a result

now the wificard has obtained a 92% signal from the router, and properly displays the SSID but it is not accepting the WEP password

its 5 letters, and ive tested the password on 2 other computers (vista+xp) and they are both using that password now (how im typing to you) so the WEP key is not incorrect.

took a screenshot as pictures speak louder than words sometimes

---

### Post by creepface on 2008-09-06
> **creepface said:**
> took a screenshot as pictures speak louder than words sometimes

well looks like im a total noob and i figured it out on my own.

thanks for all your help!

---

### Post by falcon61102 on 2008-09-07
You got it to work?  How did you go about that?  I'm curious so if I run into this in the future I'll have a better idea.

---

### Post by creepface on 2008-09-07
> **falcon61102 said:**
> You got it to work?  How did you go about that?  I'm curious so if I run into this in the future I'll have a better idea.

well

I was selecting the WRONG key type
just make sure you are selecting the correct keytype

---

### Post by falcon61102 on 2008-09-07
Lol... it happens.  Glad you got it working though.

---

### Post by creepface on 2008-09-07
> **falcon61102 said:**
> Lol... it happens.  Glad you got it working though.

me too, I love this.
its like a breath of fresh air.

although my work PC needs to remain XP
and my gaming pc is staying on Vista
this laptop is now my ubuntu netbook
to save myself from buying an EEE

---

### Post by falcon61102 on 2008-09-07
Well, you can marked this thread SOLVED if you go up to Thread Tools at the top of the forum and enjoy your laptop.

---

