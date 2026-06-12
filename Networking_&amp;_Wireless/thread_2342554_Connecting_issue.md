---
title: "Connecting issue"
date: 2016-11-07
forum: Networking &amp; Wireless
---

### Post by itak3d0wni on 2016-11-07
Ok I have a fresh install of ubuntu 16.04. I installed from live usb. when I try to connect to wireless or ethernet it won't connect. I have other wireless listed on available other than my own so it's detecting them. I can connect when to the Internet when I tether my phone network to it. I booted into a debian live usb and I can connect with it so I know it's not a hardware failure. But when i boot into ubuntu live usb it wont connect either. can it be a driver issue? thank you for any help.

---

### Post by Hadaka on 2016-11-07
Hi please open a terminal and do..
```
lspci -n | awk '/0200|0280/{print$3}'
iwconfig | awk '/Power /{print$2}'
```
post the output
iwconfig just post if it's on or off
thanks

---

### Post by itak3d0wni on 2016-11-07
I got:
10ec:8168
1814:0601

From the first line

lo  no wireless extensions
enp3s0 no wireless extensions
Management: on

From the 2nd.

Also my wireless card is a ralink rt2800

---

### Post by Hadaka on 2016-11-07
Thanks, ok let's start by seeing if we can get the "Power Management" off..
please open a terminal and do...
```
ifconfig
```
*Note the wireless name as in "wlan 0" or whatever 16.04 gave it.
then do..
#[COLOR=#ff0000]wls3 [/COLOR]is an EXAMPLE only. replace with your wifi name from "ifconfig"
```
sudo iwconfig [COLOR=#ff0000]wls3[/COLOR] power off
```
without booting then do..
```
iwconfig
```
*IF power management is OFF
then..
*To make perm :
*Open the editor..
```
gksudo gedit /etc/network/if-up.d/off-power-manager
```
*copy and paste these 2 lines in the editor..
```
#!/bin/sh
/sbin/iwconfig [COLOR=#ff0000]wls3[/COLOR] power off
```
*Save and close gedit
*Back to Terminal :
```
sudo chmod +x /etc/network/if-up.d/off-power-manager
```
```
sudo  systemctl restart NetworkManager.service
```
boot
*Disconnect wired connection and test wireless
thanks.

---

### Post by itak3d0wni on 2016-11-08
Ok. I got the power off but still not connecting

---

### Post by Hadaka on 2016-11-08
Great on the power off..its a start. Reading your first post, here is what
i "think" I understand...you have a new Ubuntu 16.04 load. You have no
wired or wireless access with Ubuntu. is this correct ? You also have other
devices and they cant connect either...now are you talking they cant connect to 
the router or the Ubuntu computer cant connect to ..tether to your phone?
Also, please power down your router for 2 minutes then power back up and connect
the wired connection and try to test.
thanks.

---

