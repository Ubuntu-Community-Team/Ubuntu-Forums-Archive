---
title: "Wi-Fi Not Working"
date: 2015-03-16
forum: Networking &amp; Wireless
---

### Post by mandarpowale on 2015-03-16
Hi, 

I installed Ubuntu Server 14.04.2 on my office laptop's partition to dual boot with existing Windows 7(HP pavilion dv6). I setup the wi-fi connection properly during the setup

But when I first booted in to the server's command line and tried to execute 'sudo apt-get update' , it fails to download anything. How do I solve this problem? I want to install gui so practice CLI from an ebook. I want to be able to download the xwindows environment using sudo apt-get install ubuntu-desktop.

Ty in advance
Mandar

---

### Post by kc1di on 2015-03-16
You are most likely missing the driver for your wireless card: it would help if we knew what card is installed in your machine.

in a terminal type:```
lspci
``` Then ```
lsmod
``` also ```
rfkill list 
```

post the outputs of those commands.

---

### Post by slickymaster on 2015-03-16
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by kc1di on 2015-03-16
Ok Guys, 

you need to go to the additional driver tool found by going to software center > edit> Software Sources>additional drivers

install the b43 driver from there.  when it finished reboot and you should be good to go. 
good luck

---

### Post by mandarpowale on 2015-03-17
> **kc1di said:**
> You are most likely missing the driver for your wireless card: it would help if we knew what card is installed in your machine.

in a terminal type:```
lspci
``` Then ```
lsmod
``` also ```
rfkill list 
```

post the outputs of those commands.

how do i take a screenshot, since I am running a console. I have been unable to install the desktop environment due to lack of wi-fi.

---

### Post by mandarpowale on 2015-03-17
I did lspci and it yielded 

> [I]08:00.0 Network controller: Qualcomm Ahteros AR9285 wireless Network adaptor (pci Express)(rev01)

[/I]lsmod yielded

> [I]cfg80211    494330 4 ath, ath9k_common, ath9k, mac80211
[/I]

I could not execute rfkill list since it requires internet to install it.

---

### Post by kc1di on 2015-03-17
Take a look at the ASK ubuntu post  - last answer see if that will fix the problem.
[http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285]("http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285")

also the following tweak may help:
```
echo "options ath9k nohwcrypt=1" | sudo tee  /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

