---
title: "Xubuntu 17.04 - install wifi driver (inf file)"
date: 2017-08-13
forum: Networking &amp; Wireless
---

### Post by sprinterdriver on 2017-08-13
Hi.

I have installed Xubuntu 17.04 on a Dell Lattitude D620, and from what I read from the documentation, it should be possible to use driver files that originally was made for Windows (.inf file).

My question is - Does it matter what WIndows version that driver was made for? Also the documentation doesn't provide very detailed information on how to proceed, exept I know that I need to install some package to make it work - but what do I do after that?


Thanks

---

### Post by johndough2 on 2017-08-13
Hi

Can you ID the WiFi components that it has?
WLAN

Intel® 3945 WiFi 802.11a/g, Dell Wireless 1390 802.11g, Dell Wireless 1490 802.11a/g Dual-Band Mini-Cards, Internal Bluetooth (optional).

Then if it is the Intel maybe someone can help.

There is a wireless script to run and post results
[https://sourceforge.net/projects/wirelessscript/files/](https://sourceforge.net/projects/wirelessscript/files/)

Also run some updates, if you haven't already.

sudo apt update
sudo apt dist-upgrade

Maybe a utility or somepart of the WiFi toolset is missing.
sudo apt install wireles*  (this may list a lot of stuff, say NO & read thru the listing to see if anything is relevant).
sudo apt install iw* (this may list a lot of stuff, say NO & read thru the listing to see if anything is relevant).

---

### Post by jeremy31 on 2017-08-13
Please post results from terminal for ```
lspci -nnk | grep -iA3 net; rfkill list all
```
Please do not use ndiswrapper

---

### Post by sprinterdriver on 2017-08-13
So ndiswrapper is bad?

```
sprinterdrivr@sparr:~$ lspci -nnk | grep -iA3 net; rfkill list all
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
    Subsystem: Dell Latitude D620 [1028:01c2]
    Kernel driver in use: tg3
    Kernel modules: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel modules: ssb, wl
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```


unrelated to the problem for anyone else than me:
The laptop is placed in a way so in order to connect it by cable, I have to let some dors open in the house. Therefore I don't won't to lay out the cable before neccesary (modem/router located in a narrow staircase hanging on the wall)

---

### Post by jeremy31 on 2017-08-13
Go into BIOS settings and disable secure boot and see if that works.  My results with ndiswrapper were very poor

---

### Post by chili555 on 2017-08-13
> 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel modules: ssb, [COLOR="#FF0000"]wl[/COLOR]You have the wrong driver.

With a working internet connection, do:```
sudo apt purge bcmwl-kernel-source
sudo apt install firmware-b43-installer
```Reboot and enjoy your wireless.

---

### Post by Hadaka on 2017-08-13
Hi, from a working wired connection, a cable to the router.
Please COPY and paste one line at a time.
*Ignore any error or file not found do every line.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe -rf ssb
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
Remove wired connection, boot and test wireless
Thanks
#@ That chili555 guy is quick !

---

### Post by sprinterdriver on 2017-08-13
Thank you very much for help. I'm now connected through wifi ):P

I was following the steps privided by chili555, problem solved.

But I want to know how to tell that the driver is the wrong one?

---

### Post by chili555 on 2017-08-13
> But I want to know how to tell that the driver is the wrong one?Please see the very first thread in this sub-forum: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)> 14e4:4311                  firmware-b43-installer                firmware-b43-installer

Please use thread tools at the top to mark Solved.

Glad it's working!

---

