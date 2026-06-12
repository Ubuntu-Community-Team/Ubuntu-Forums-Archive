---
title: "Broadcom BCM4312 LP-PHY- Can't see my WiFi"
date: 2013-10-26
forum: Networking &amp; Wireless
---

### Post by markus.jansson on 2013-10-26
[SIZE=2]Hello!

Apparently Im having the same issue. My computer (hdd installed Lubuntu) can find most wlans, but not the one I would like to use. When I boot Knoppix, it has no problem connecting to that wlan. I did as you instructed, but now Im stuck with this situation. I cannot even choose to use that driver from this screen, that part is greyed out. Any suggestions on how to get it running smoothly?[/SIZE]

[IMG]http://s22.postimg.org/hum2abl75/330zlvp.png[/IMG]

---

### Post by varunendra on 2013-10-27
Welcome to the forums Markus ! :)

Please forget the above screen, even disable its notification if you can. The only option you can choose from it is to install the proprietary driver again which is not good for this card.

Assuming you have correctly purged the "bcmwl-kernel-source" driver and have "[linux-firmware-nonfree]("http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download")" package installed, please reboot > open a terminal (Ctrl-Alt-T) and run the following commands in it -
```
lsmod | egrep 'b43|wl'
dmesg | grep b43
sudo iwlist scan
```
post back the entire output here.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by sandyd on 2013-10-27
**moved to own thread**

---

### Post by markus.jansson on 2013-10-27
Here is what I got
[IMG]http://i40.tinypic.com/2r77wk9.jpg[/IMG]

---

### Post by varunendra on 2013-10-27
Thank you for the move and the image resize sandyd. :)

@ Markus,
See those "**Firmware file....[COLOR="#FF0000"]not found[/COLOR]**" errors? It means you haven't installed the required firmware yet. If you have a working internet connection (wired, modem etc.), please do -
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rv b43
sudo modprobe -v b43
```

If you don't have a working connection, manually download the package from here : [http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download)

Copy the downloaded file to your Lubuntu desktop, and double-click to install. If there are any errors while installing, report back the errors. If not, check if it installed correctly -
```
ls /lib/firmware/b43
```
Do you see a long list of files in the output? If yes, you should have your wifi working again. If not, there is a problem we need to fix.

Please report back the outcome and we'll do some more things if required.

---

### Post by markus.jansson on 2013-10-27
THANK YOU!
I thought that I had already installed those drivers, but apparently not. Now it works like charm.
You just made my www-surfing about 10x faster (I can use 4G now). :-) :-) :-)

---

### Post by varunendra on 2013-10-27
Great ! This should be a permanent fix, just remember not to try the proprietary driver (bcmwl-kernel-source) with this card.

And thanks for the feedback about the speed. :)

---

