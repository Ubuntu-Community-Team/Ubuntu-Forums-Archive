---
title: "Enjoying Ubuntu but how do I connect to my wireless? (Newb)"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by NewTechGuy on 2008-09-29
Ok I'm new to all of Linux but I managed to dual boot Ubuntu with XP Pro and I'm loving this OS. I had to reinstall my drivers to get XP to connect to my wireless and it now works but Ubuntu still wont connect. Any info I have found online has been from 2006 so I'm a little weary of using it. Any help or nudge in the right direction is much appreciated.

Info:
Laptop: Gateway 7330GZ
Router: Belkin G plus Mimo (password protected if that matters.. I do have the name/pass tho obviously).
Network adapters: 1394 net adapter and Broadcom 802.11G

Not sure if that will help at all but figured I'd throw it in.

Thank you,
NewTechGuy

---

### Post by NewTechGuy on 2008-09-30
anyone...

---

### Post by Bucky Ball on 2008-09-30
Check System->Hardware Drivers. Is the Broadcom B43 Driver in there? If it is, then you should be able to use that in conjunction with b43-fwcutter which can be found in Synaptic Package Manager (also under System). From memory it may give you the option to download b43-fwcutter when you click the box for the restricted driver.

update: Looks like your card does work with B43. Do not install ndiswrapper until you have tried this avenue. It is a lot more involved and if this works (and it should) it will take a couple of clicks as long as you haven't got ndiswrapper installed already. :)

---

### Post by NewTechGuy on 2008-09-30
It doesn't show any drivers in the list. Do I have to download the B43 then or just type something into the terminal?

---

### Post by Bucky Ball on 2008-09-30
Find and install b43-fwcutter from Synaptics and go from there. If you wanted to go the terminal route, you would just type:

```
sudo apt-get install b43-fwcutter
```

... should work. Sudo make you root for that command (su=superuser; do=do - superuser do) :)

Good luck and let us know.

ps: Run this in a terminal to see if your card is compatible first. Just copy and paste. If your card is identified, go with the above:

```
lspci -nn | grep 14e4
```pps: for your interest, if you type:

```
lspci -man
```... you will find a bunch of options you can replace -nn with. lscpi -l will list all pci devices for instance. ;)

---

### Post by NewTechGuy on 2008-09-30
your apt get function came back with a "couldn't find package b43-fwcutter"... I assumed it was trying to download it even though I have no internet connection so I transferred the b43-fwcutter that I found online to that computer and ran```
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
export FIRMWARE_INSTALL_DIR="/lib/firmware"

``` From that same folder.. all of which seemed to go well.

lspci -nn | grep 14e4 Came back with this:

```
01:06.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
01:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```

I still show no drivers.. What are my next steps? Thanks again for the help.

---

### Post by NewTechGuy on 2008-09-30
..

---

### Post by Bucky Ball on 2008-10-01
Sorry, needed sleep. What shows up under Hardware Drivers now? And yes, the grep command shows your card is good to go with this driver. 

dmesg | grep b43

That will show if it is installed, which I don't think is the case just yet.

[quote=NewTechGuy]apt get function came back with a "couldn't find package b43-fwcutter"... I assumed it was trying to download it even though I have no internet connection[/quote] That is indeed the case, but also, your 'apt get' should be 'apt**-**get', with a hyphen. Have you a hardwire you can use for this procedure to get you online? You may be able to load what you need from the live cd but couldn't help you with that.

[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

This will outline the correct commands for what you are trying to do in the terminal. I have never seen anything like the command below from your previous post in Ubuntu before, but that doesn't mean it is wrong:

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
```What source did you get your untar and install method from? You might find this helpful:

[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

:)

---

