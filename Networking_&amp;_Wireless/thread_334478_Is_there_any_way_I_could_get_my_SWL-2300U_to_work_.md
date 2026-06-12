---
title: "Is there any way I could get my SWL-2300U to work in Ubuntu."
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by Condoulo on 2007-01-09
I would like to use Ubuntu, but my wireless card doesn't work in it, and right now I can't just go out and buy another Wireless card. So I am wondering if there was ANY way to get my Netopia SWL-2300U that Bell South sent in to work. 

Please explain the instructions in a numbered order if you can.

If you can help, I would greatly appreciate it.

Oh, I tried using ndiswrapper, but that didn't work for me. Or maybe I did it wrong.

---

### Post by teaker1s on 2007-01-09
terminal for pci connected

[COLOR="Red"]sudo lspci[/COLOR]

if it's usb

[COLOR="Red"]sudo lsusb[/COLOR]


post output 
brand name means nothing in linux, chipset is everything

---

### Post by Condoulo on 2007-01-09
I typed it, and here is what I got:

Bus 001 Device 006: ID 055d: a230 Samsung Electro-Mechanics Co.

---

### Post by teaker1s on 2007-01-09
okay well looking around it would appear that it will work on linux but there are several people having problms with it in ubuntu.
firstly can you post the link to the guide you used for ndiswrapper so I can try to work out what's happening please.

secondly if you could copy and paste these commands in terminal I will try to figure out what has gone wrong or is missing with ndiswrapper-please post output from terminal

[COLOR="Red"]sudo modprobe ndiswrapper[/COLOR]
[COLOR="Red"]
sudo ndiswrapper -l[/COLOR]

[COLOR="Red"]iwconfig[/COLOR]

---

### Post by Condoulo on 2007-01-09
I'll try those commands. :)

Also, It's sorta hard since I am currently using a Windows PC to connect to the internet right now. (I was lucky the output last time was short)

---

### Post by teaker1s on 2007-01-09
just these then

[COLOR="Red"]sudo modprobe ndiswrapper

sudo ndiswrapper -l
[/COLOR]

---

### Post by Condoulo on 2007-01-09
Ok, I tried the ndiswrapper commands you gave me, it said "installing driver", but when I went to see the list, is said both of them I used were invalid.

---

### Post by teaker1s on 2007-01-09
it's a small L not i   ;) 
[COLOR="Red"]sudo ndiswrapper -l[/COLOR]

---

### Post by Condoulo on 2007-01-09
I know, and that listed the installed drivers. It said that the file I tried was a invalid driver.

---

### Post by teaker1s on 2007-01-09
really so why did it say installing then?
okay now we are getting somewhere;) 

where did you get driver from? if it was ndiswrapper own it needs ditching for the manufacturers one off cd or downloaded,you may need to install cabextract or unzip if it's in an exe file and not just inf and possibly sys file

---

### Post by Condoulo on 2007-01-09
Well I got the driver from driverguide (I couldn't find the CD, it's been over a year since I needed it).

driverguide.com to be more specific

---

### Post by Condoulo on 2007-01-09
Where would I get Cabextract or unzip?

---

### Post by teaker1s on 2007-01-09
the easiest I'd guess by downloading and burning
ubuntu alternate iso 
it has more packages and
[COLOR="Red"]gksudo synaptic[/COLOR]
hit edit tab and Add cdrom
hit reload and search packages

then you will need the windows driver-if your isp supplied check with them otherwise it's a samsung product from what I can find maybe they or netopia can supply a driver8)

---

### Post by Condoulo on 2007-01-13
hmmmm... I still haven't been able to get it to work. =/

---

### Post by teaker1s on 2007-01-14
it would appear from my looking round that this hardware is not supported at all well with linux, the only other suggestions that I've found are linux-wlan-ng suggested by someone using suse linux

[ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/)

in all honesty you may be better buying a new adapter that works with linux out the box as I'm unable to find anything useful or anyone reporting success with google

---

### Post by Condoulo on 2007-01-16
Know any good guides for using Linux-Wlan-ng?

---

### Post by teaker1s on 2007-01-16
Okay looking through synaptic the packages are available without having to compile unless you find that you need later version compiled for your model-not sure

**wired ethernet internet connection required**

you need to uncomment any commented out sources by
[COLOR="Red"]sudo gedit /etc/apt/sources.list[/COLOR]

and remove any commented out ones by removing   [COLOR="Red"]# 
[/COLOR]

[COLOR="Red"]gksudo synaptic[/COLOR]

hit reload tab

search for[COLOR="Red"]
linux-wlan-ng
linux-wlan-ng-firmware
network-manager-gnome[/COLOR]

panel click
system
administration
networking

make sure interfaces are not configured by removing ticks
remove ethernet cable
reboot
next to volume is network-manager-gnome applet which you need to left click and if it's worked you will see wireless networks

if not you may need firmware directly from project website and possibly need to remove ubuntu package and compile source if above won't work

---

### Post by Condoulo on 2007-01-17
Only one problem, I don't have a ethernet cable, or one long enough to connect to the Computer I'm trying to get the Wireless On.

---

### Post by teaker1s on 2007-01-18
choices really are:-
1)move the computer or buy longer ethernet cable
2)download deb packages directly from repositories with web browser- if possible-haven't ever tried. Burn to cd and click install.
3) or if you burn ubuntu alternate iso it has linux-wlan-ng package  you would need to still download firmware from project site.
4)download source and firmware onto cd and compile it, as long as it doesn't have dependency issues it should compile. If it has dependency issues then you will have to find every package and download to cd and install before it will work

[http://www.linux-wlan.org/]("http://www.linux-wlan.org/")

---

### Post by Condoulo on 2007-02-12
I recently got a new DWL-G122 Rev B. And it works like a charm in Ubuntu. :) Thanks for all the help though.

---

### Post by teaker1s on 2007-02-13
:popcorn: your welcome and enjoy your ubuntu:KS :KS :KS :KS

---

