---
title: "[SOLVED] Option 3G Wireless (Globetrotter) card not recognized"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by pwaldo on 2008-11-03
Hi all,

I have been able to get my Globetrotter card working finally.  The problem was that when the card is inserted, it looks like a USB memory stick that contains Windows install software.  This functionality must be disabled before the card will be a modem.  There is a utility to switch the mode on this card.  You can get it by doing the following:

[LIST=1]
[*]Add this repository to your /etc/apt/sources.list: ```
deb http://ppa.launchpad.net/martijn/ubuntu intrepid main
```
[*]Get the package: ```
sudo aptitude install rezero
```
[/LIST]

Hope this helps out!

---

### Post by rephreak on 2008-11-03
Hi,

Im happy if you can explain how to add that repository. Because Im new in linux. This is my first time using Ubuntu 8.10.

Its look like I need internet connection to add that repository, but i can't do that if my modem (Option ICON2 USB) not work.

Would you write step by step for the solution?

Thanks, and sorry for my bad english.

---

### Post by Arabiest on 2008-11-04
Thank u.

This might help with my Branddeluxe C100 GSM card and my SMC Wirless Adapter.

I will try it soon.

---

### Post by pwaldo on 2008-11-04
> **rephreak said:**
> Hi,

Im happy if you can explain how to add that repository. Because Im new in linux. This is my first time using Ubuntu 8.10.

Its look like I need internet connection to add that repository, but i can't do that if my modem (Option ICON2 USB) not work.

Would you write step by step for the solution?

Thanks, and sorry for my bad english.
Hi rephreak,

I'm not sure if my procedure will work for you, as it appears we have different cards.  When you plug your card in, do you get a CD icon where the name is REZERO?  If so, this may work for you.

The first thing is to open a terminal.  Use your menus and run Applications|Accessories|Terminal.  In this terminal, type or paste this command.  This adds the repository where rezero lives.
```
sudo sh -c 'echo "deb http://ppa.launchpad.net/martijn/ubuntu intrepid main" >> /etc/apt/sources.list'
```

Next, you need to update your repository info:
```
sudo aptitude update
```

Now get the rezero utility
```
sudo aptitude install rezero
```

Once you do this and insert your card, it should be accessable to network manager.  Good luck!

---

### Post by Guranic on 2008-11-06
My globetrotter GT MAX READY 7.2 card won't show up as a 3g modem, Ubuntu 8.10 opens up mounted CD. I installed rezero but still, it won't work like I wanted to. I did just installation using apt, is there something I need to do with rezero, commands? Any suggestions? "CD" is mounted /dev/sr1 -> /media/cdrom1. What should I do?

---

### Post by pwaldo on 2008-11-07
> **Guranic said:**
> My globetrotter GT MAX READY 7.2 card won't show up as a 3g modem, Ubuntu 8.10 opens up mounted CD. I installed rezero but still, it won't work like I wanted to. I did just installation using apt, is there something I need to do with rezero, commands? Any suggestions? "CD" is mounted /dev/sr1 -> /media/cdrom1. What should I do?
Did you try removing and reinserting the card?
Rebooting?
Another thing I had to do was add "blacklist option" to /etc/modprobe.d/blacklist.  This prevents the vendor driver (that doesn't work) from loading.

HTH!
Paul

---

### Post by Guranic on 2008-11-07
> **pwaldo said:**
> Did you try removing and reinserting the card?
Rebooting?
Another thing I had to do was add "blacklist option" to /etc/modprobe.d/blacklist.  This prevents the vendor driver (that doesn't work) from loading.

HTH!
Paul

First thing I tried was reboot.. The card still shows up as a cdrom drive. I have no idea what to do next....

---

### Post by snupie37 on 2008-12-29
Hello,

i've also a globetrotter icon 7.2 3g hsdpa modem from qualcomm. my provider is the austrian webprovider 3 (drei.at). i had also problems to get the modem working under ubuntu linux, because it is recognized as usb storage device. This modem has two modes. so it is necessary to set the correct mode (modem mode).

to do this, i used the tool usb_modeswitch by josua dietze ([http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)). you will need the program (usb_modeswitch) and the config (usb_modeswitch.conf). you can also download the sources, but it works with the given binary good enough. copy the config file to /etc and the program to /usr/local/bin. set the correct rights and start the program. after that the modem has the correct mode and the connection will do.

after that set the needed new entry within the network manager (vs. 0.7 is used in ubuntu 8.10). a wizard creates an entry with the correct values. you can also set the pin if needed.

additional habe a look with lsusb and ls /dev/ttyUsb* to check which usb devices you have. lsusb returns the vendor id and the product id. they are used by the above tool. one thing is that you eventually need the usbserial module. have a look with lsmod and modprobe usbserial ...


snupie37

---

