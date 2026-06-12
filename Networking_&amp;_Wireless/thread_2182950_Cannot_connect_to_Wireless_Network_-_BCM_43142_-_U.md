---
title: "Cannot connect to Wireless Network - BCM 43142 - Ubuntu 13.10"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by kanishkdudeja on 2013-10-23
I used this thread to fix my wireless connection for the Card BCM43142 on Ubuntu 13.10[URL="http://askubuntu.com/questions/289609/dell-3721-wifi-problem-ubuntu-13-04/289614#289614"]

http://askubuntu.com/questions/289609/dell-3721-wifi-problem-ubuntu-13-04/289614#289614[/URL]

It worked only once. Now whenever i try to connect to my wireless connection, it keeps on showing the connecting symbol. And there is no response.

Can you please help me out?

---

### Post by Mike_Pearson on 2013-10-23
I've been banging by head against this wall too. But have found this soution:-

Install the correct driver for this wireless card. 
Then remove the &#8220;incorrect&#8221; driver (bcmwl) which Ubuntu installed  by default. $ sudo apt-get update
$ sudo apt-get install firmware-b43-installer
$ sudo apt-get remove bcmwl-kernel-source
$ sudo reboot


 Please note My problem was on a Compaq nx6325 with Broadcom BCM4311  but I note from my trawling thu the problem pages and forums this seems to have worked for others
Good luck
P.S. The Terminal hung at one point but I rebooted and repeated the instructions and followed the prompts

---

### Post by varunendra on 2013-10-24
Hello Kanishk !

While being connected to internet (via cable, modem etc.), please do -
```
sudo modprobe -rv wl b43
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe -v b43
```
..or just do a reboot after installing the "linux-firmware-nonfree" package (sometimes the "wl" driver refuses to unload, causing conflict and system hang while modprob'ing b43, a reboot will fix it).

If you don't have an internet connection available on that system, manually download the package from [here]("http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download"), copy it to your Ubuntu desktop, and double-click to install. Reboot and done.

@ Mike,
This part needs a 'small' correction for this particular card (BCM4312) -
```
$ sudo apt-get install [COLOR="#FF0000"]firmware-b43-installer[/COLOR]
```
It should be -
```
sudo apt-get install firmware-b43-lpphy-installer
```
..because this card uses a "**L**ow **P**ower" firmware. Rest of your instructions are correct, mine is just a bit different to achieve the same thing. :)

---

