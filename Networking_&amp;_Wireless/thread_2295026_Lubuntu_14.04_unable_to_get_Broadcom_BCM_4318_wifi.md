---
title: "Lubuntu 14.04 unable to get Broadcom BCM 4318 wifi working"
date: 2015-09-15
forum: Networking &amp; Wireless
---

### Post by brus brother on 2015-09-15
I have researched and tried for days to get Broadcom 4318 wifi working on a Compaq Presario V2000.
I was successful on LM 17.2 Xfce since that installed automatically once I used the package manager and installed firmware-b43-installer.
That doesn't seem to work for Lubuntu.
LM 17.2 is too laggy for this machine which only has 512mb Ram and a 40 GB HD. So I am desperate to get the wifi working. I have wired connection.
I just did a fresh install of  Lubuntu and would appreciate any help in sorting this out before I muck up the current installation.

---

### Post by Bucky Ball on 2015-09-15
Install b43-fwcutter if not already installed then have a look [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_Internet_access"). Follow the instructions from the top of that page to install the b43 driver. Any luck?

---

### Post by brus brother on 2015-09-15
I will do that but I am pretty sure I have done it in the past few days (once or twice)
Additional drivers shows the STA broadband but my BCM4318 doesn't require that driver.
I have tried using it but it didn't work either.
Just tried following the steps outlined again but still nothing.
Edit:
The wireless light is ON but no connection noted in Networks and no wifi
SOLVED:
nm-applet and now I can see connections and connect.
Why is this not part of the install?

---

### Post by gam01hr on 2016-03-05
Many thanks. Solved.
I have had problem with the wlan adapter not found. Your recepie works well for me.
ubuntu: ubuntu 14.04 LTS
manufacturer: HP
model: Compaq nx6110
> 
b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
b43-phy0 ERROR: You must go to [http://wireless.kernel.org/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver vesion. Please carefully read all instructions on this webside.

> 
$ lspci -vnn -d 14e4:
02:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1356]

> 
sudo apt-get install firmware-b43-installer

plus restart, solved my problem.:D

---

