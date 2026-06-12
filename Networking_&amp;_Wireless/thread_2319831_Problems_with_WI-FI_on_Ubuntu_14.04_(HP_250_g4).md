---
title: "Problems with WI-FI on Ubuntu 14.04 (HP 250 g4)"
date: 2016-04-07
forum: Networking &amp; Wireless
---

### Post by danny_boy on 2016-04-07
Hello everybody,

Since I installed Ubuntu 14.04 on my new HP 250 g4 laptop I've been experiencing random wi-fi signal dropouts (pages seem to load forever even though the wifi icon shows that I'm connected). I'm also frequently asked for wi-fi password.

The same goes for Linux Mint 17.02 which is installed as a second OS on the same laptop.

What's interesting, my wife has got Ubuntu 14.04 installed on her netbook (Samsung N150 Plus) and it runs flawlessly. (I've tried to compare wireless-scripts on our both machines but I couldn't find anything different that could possibly explain my problem).

I also noticed that it is common problem for this particular Ubuntu distribution but going through countless number of threads and not being able to find solution I finally decided to ask professionals for help with this because, to be honest, it's getting quite unbearable.

I'm also attaching wireless-info.txt.

Thank you in advance

---

### Post by danny_boy on 2016-04-08
Bump

---

### Post by Hadaka on 2016-04-08
Hi, From a working wired connection open a terminal then copy and paste..
```
sudo iw reg set PL
sudo sed -i 's/^REG.*=$/&PL/' /etc/default/crda
```
then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo  modprobe -rf wl
```
Next
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove 
sudo apt-get autoclean
sudo modprobe -vv wl
```
remove wired connection..boot..test wireless.
Your wireless report also shows you have a low signal level to your current connection.
```
Quality=38/70  Signal level=-72 dBm
```
acceptable is 50/70..excellent is 70/70
Check the antenna connections on your router and on your wifi card.
thanks.

---

### Post by danny_boy on 2016-04-08
[SIZE=2][FONT=arial]Thank you very much Hadaka but unfortunately after executing [/FONT][FONT=arial]```
sudo  modprobe -rf wl
``` command I am unable to proceed with next steps because I can't connect the network. 

Any ideas why this could happen? Did I mess something up? I started the whole process wireless and only after```
 sudo  modprobe -rf wl
``` I plugged in the wire.[/FONT][/SIZE]

---

### Post by Hadaka on 2016-04-08
Hi, yes that likely happened because the first instruction i gave was..
```
From a working wired connection open a terminal then copy and paste..
```
you must have been attempting to do this from a wireless connection.
and that command,,,```
 sudo modprobe -rf wl
```
removes the wireless driver, Please re read the instructions from
the fisrt line.
thanks

---

### Post by danny_boy on 2016-04-09
Thank you one more time Hadaka. I really appreciate your patience and your support. I did the whole process from the beginning using wired connection. Unfortunately the problem persists. At first, it seemed that everything worked just fine but after 20 minutes or so I began to be asked for wi-fi password and my wireless disconnects at random intervals. Shall I post wireless-info again?

---

### Post by Hadaka on 2016-04-09
Hi, thanks for the update, yes please run wireless script again.
also please post the output of..
```
sudo dpkg -s bcmwl-kernel-source
```
thanks.

---

### Post by danny_boy on 2016-04-09
sudo dpkg -s bcmwl-kernel-source
```
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 7856
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.30.223.248+bdcom-0ubuntu0.2
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d*sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>
```

---

### Post by Hadaka on 2016-04-09
Hi, you have the latest driver..
```
Architecture: amd64
Source: bcmwl
Version: 6.30.223.248+bdcom-0ubuntu0.2
```
You signal Quality is still very low on your access point..
```
wlan0     Scan completed :
          Cell 01 - Address: <MAC 'noria' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"noria"
```
and you are the only one on this channel and freq.
```
1   APs on   Frequency:2.462 GHz (Channel 11)
```

Your signal is so low that your wifi card goes into the roam mode, looking for a better singnal,.
How far are you from your router? Did you check the antenna connections at the router and on the wifi card ?
*If you have configured your router for N mode only,5GHz, it needs to be set to b/g/n.
##### dmesg #############################

[ 8135.639223] CPU: 2 PID: 424 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-30-generic #36~14.04.1-Ubuntu
[ 8135.639293]  [<ffffffffc09d9245>] wl_notify_roaming_status+0xc5/0x140 [wl]
[ 8135.639322]  [<ffffffffc09d88b4>] wl_event_handler+0x64/0x1f0 [wl]
[ 8139.629682] CPU: 2 PID: 424 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-30-generic #36~14.04.1-Ubuntu
[ 8139.629804]  [<ffffffffc09d9245>] wl_notify_roaming_status+0xc5/0x140 [wl]
[ 8139.629835]  [<ffffffffc09d88b4>] wl_event_handler+0x64/0x1f0 [wl]
[ 8143.724141] CPU: 2 PID: 424 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-30-generic #36~14.04.1-Ubuntu
[ 8143.724208]  [<ffffffffc09d9245>] wl_notify_roaming_status+0xc5/0x140 [wl]
[ 8143.724236]  [<ffffffffc09d88b4>] wl_event_handler+0x64/0x1f0 [wl]
[ 8183.598312] ERROR @wl_dev_intvar_get : error (-1)
I am out of ideas and regret not offering a suggestion that resolved this issue. sorry i was unable to help.
thanks.

---

### Post by danny_boy on 2016-04-09
OK. Thanks a lot.

---

