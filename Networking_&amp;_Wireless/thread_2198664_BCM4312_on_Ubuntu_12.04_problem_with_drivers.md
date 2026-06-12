---
title: "BCM4312 on Ubuntu 12.04 problem with drivers"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by thexaxoo on 2014-01-09
Hello, 

For some days now I am trying to configure aircrack-ng on my system and I am not able to do so.The closest thing I have come to now is:
- use wlan card as normal but not being able to put it in monitor mode ( sudo aircrack-ng start eth1 (yeah when I switch to the wl driver, wlan0 becomes eth1 ))
   * using wl (broadcom sta) driver
- card can't detect any networks, monitor can be switched on and off
   * using b43
I have tried using different versions of b43-fwcutter, broadcom-wl and firmware-b43-installer (firmware-b43-lpphy-installer), but with no success.

I am hoping that someone can help me to be able to use my card as normal and to be able to crack networks (I have done it with BackTrack)

My system:

OS: Ubuntu 12.04.03
PCI-ID: 14e4:4315
Chip-ID: BCM4312 
Modes: b/g 
PHY Version: LP (r1) 
Supported: yes (2.6.33+) 
Alternative: wl 
uname -a: [http://pastebin.com/ZtKpBcYQ](http://pastebin.com/ZtKpBcYQ)
sudo lspci -vvn|grep 43 -A7: [http://pastebin.com/4QBg5dBz](http://pastebin.com/4QBg5dBz)

Tell me if you need any more info.

Thanks in advance!

---

### Post by tfrue on 2014-01-10
Well...I would suggest using BackTrack 5 R3 for using aircrack-ng suite as it comes with it and I have always had BackTrack work out of the box. Kali Linux is the 'new' BackTrack and works well, but I have had a lot of trouble getting it installed.

But if you don't want to do that, then try:
```
sudo apt-get update
```
```
sudo apt-get --reinstall install bcmwl-kernel-source
```

If that give's you an error, try:
```
sudo apt-get install linux-headers-generic
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install --reinstall bcmwl-kernel-source
```

Then let's test the driver so we don't have to restart the computer:
```
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
sudo modprobe wl
```

Good Luck,
Chris

---

