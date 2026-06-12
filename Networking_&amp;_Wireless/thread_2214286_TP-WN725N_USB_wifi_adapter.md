---
title: "TP-WN725N USB wifi adapter"
date: 2014-03-31
forum: Networking &amp; Wireless
---

### Post by daniel131 on 2014-03-31
Hello.

I am getting kind of tired of all this ubuntu stuff. First it wasnt possible to find and use the wireless card inside the computer:
[http://ubuntuforums.org/showthread.php?t=2213355](http://ubuntuforums.org/showthread.php?t=2213355)

Now i have gotten an TP-WN725N but when i try to install the driver (with Wine) the computer cant find or see that the tiny usb-stick is inserted.
Here is the usb: [http://www.tp-link.com/lk/products/details/?model=TL-WN725N#spec](http://www.tp-link.com/lk/products/details/?model=TL-WN725N#spec)

Please, I really want this to work.

I have tried this:
[http://linuxforums.org.uk/index.php?topic=11065.0](http://linuxforums.org.uk/index.php?topic=11065.0)

but nothing good happened...
Please help me out.

---

### Post by chili555 on 2014-03-31
With the device inserted, please open a terminal and run and post:```
lsusb
lsb_release -d
uname -r
```Thanks.

---

### Post by daniel131 on 2014-03-31
Hi again chili555! :D

lusb:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
With the USB-receiver inserted i also get this line:
```
Bus 001 Device 004: ID 0bda:8179 Realtek Semiconductor Corp. 

```

lsb_release -d
```
Description:    Ubuntu 12.04.4 LTS
```

uname -r
```
3.11.0-18-generic
```

I am so glad that you are willing to help me again!

---

### Post by chili555 on 2014-03-31
With a working internet connection by ethernet, USB modem, tethering or whatever means, open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
```Then follow the process I outlined here: [http://askubuntu.com/questions/377470/tp-link-wn725n-unable-to-get-drivers-to-work-with-13-04-after-upgrade-worked-o](http://askubuntu.com/questions/377470/tp-link-wn725n-unable-to-get-drivers-to-work-with-13-04-after-upgrade-worked-o)

I compiled the driver I mentioned there and it indeed covers your device:```
$ modinfo 8188eu.ko
filename:       8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     40E40A23FEAFB235042D25F
alias:          usb:v2001p330Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8179d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp0179d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]8179[/COLOR]d*dc*dsc*dp*ic*isc*ip*
<snip>
```As always, post back if you get stuck.

---

### Post by daniel131 on 2014-03-31
I did all the commands without so much success.. 

The good thing though is that when i insert my wifi-usb the cumputer reacts, a little window that says "You are not connected to the network". But then nothing happens. But earlier nothing happened so maby better? I am still unable to klick "enable wireless" and all that jazz... Bah..
(I did reboot after the commands)

the lsusb doesnt show a different resault from before. Bah..

Can it be something about my earlier installation? : 
[http://linuxforums.org.uk/index.php?topic=11065.0](http://linuxforums.org.uk/index.php?topic=11065.0)

---

### Post by chili555 on 2014-03-31
Let's take some diagnostics and see what's (not) happening under the hood. With any ethernet cable detached, please run:```
dmesg | grep -e 8188 -e rtl  >  wifi.txt
iwconfig  >>  wifi.txt
rfkill list all  >>  wifi.txt
nm-tool  >>  wifi.txt
```Hook up the ethernet, open your user directory, find the file wifi.txt and post it here.

---

### Post by daniel131 on 2014-03-31
okey,
without ethernet but with the TP-LINK (usb) inserted:
[http://paste.ubuntu.com/7186269/](http://paste.ubuntu.com/7186269/)

without the TP-LINK inserted:
[http://paste.ubuntu.com/7186293/](http://paste.ubuntu.com/7186293/)

---

### Post by chili555 on 2014-03-31
Let's blacklist the Intel:```
sudo -i
echo "blacklist iwl3945"  >> /etc/modprobe.d/blacklist.conf
modprobe -r iwl3945
exit
```Flip the switch or key combination to enable wireless. Any change?

We needn't see any readings with the USB disconnected.

---

### Post by daniel131 on 2014-03-31
Hm, I am not sure i understand what you mean? What is wrong? What could be the sulution?

---

### Post by chili555 on 2014-03-31
> **daniel131 said:**
> Hm, I am not sure i understand what you mean? What is wrong? What could be the sulution?I edited my post. Please check again.

---

### Post by daniel131 on 2014-03-31
HALLELUJAH!!! THANK GOD! OH CHILI555 YOU JUST MADE MY WEEK!!
I am so gracefull and thankfull! Thank you big time!
Now I really can start enjoying my Ubuntu laptop! Great! :D

---

### Post by chili555 on 2014-03-31
Awesome news! Reach up there to Thread Tools and mark Solved.

You have compiled the driver for your current running kernel only. When Update Manager installs a newer kernel version, recompile:```
cd ~/Desktop/rtl8188eu-master
make clean
make
sudo make install
sudo modprobe 8188eu
```Please retain the file and these instructions for that time.

Have fun!

---

### Post by daniel131 on 2014-03-31
So when should i do this you say? I just notice that when it stops working?

---

### Post by chili555 on 2014-03-31
When Update Manager installs a later kernel, known in Ubuntu World as linux-image, it invariably asks you to reboot to complete the update. If you do and the wireless isn't working, recompile. If that still doesn't do it, call on me.

---

### Post by daniel131 on 2014-03-31
Great, thanks a lot! :D

---

