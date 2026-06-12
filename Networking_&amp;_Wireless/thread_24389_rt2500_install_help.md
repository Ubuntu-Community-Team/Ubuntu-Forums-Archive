---
title: "rt2500 install help"
date: 2005-04-06
forum: Networking &amp; Wireless
---

### Post by kamakazieKiwi on 2005-04-06
Hi,

I'm hoping someone out there can give me a walk through on how to get an rt2500 wireless card up and running in hoary.  What I have been doing so far just hasn't been working, and it would be easiest if someone could walk me through from the start assuming I have  a fresh install of hoary, once I know how it should be done it is easy enough for me to spot where I have gone wrong (most likely on multiple occasions).

Everything else works fine, unlike any of the other distros I have installed on this system (well I don't yet know about getting 5.1 sound out of my card, but thats for later), and if I can get the wireless working I will be a definite ubuntu convert!

Thnx.

---

### Post by lordofkhemenu on 2005-04-06
#: ndiswrapper -i /path/to/the/driver/Rt2500.INF
#:ndiswrapper -m
add a line *ndiswrapper* to /etc/modules
 Use the networking applet (System|Administration|Networking) to activate and configure wlan0
add *auto wlan0* to /etc/network/interfaces


Anybody else feel free to elaborate or correct the order of my steps (I'm doing from memory...I read the ndiswrapper site instructions and haven't had to fsck with it since).

---

### Post by kamakazieKiwi on 2005-04-07
Well I thought that is what I had done, and last night it just didn't want to work. I also tried installing the rt2500 dirvers but had no joy there either.

This morning I tired again following your instructions (which are the same as the others I had found) and it seems to be ok.  I'm at work and away from my wireless point, but I can now at least see the device.

Thanks for the help  :-)

---

### Post by smiting2000 on 2005-04-09
how do you install ndiswrapper? the instructions on their site don't seem to work for me.  i may be doing something wrong but could someone tell me exactly what i need to do to install it?

thank you

---

### Post by pieter hollenberg on 2005-04-10
would like to install the native linux drivers of ralink instead of ndiswrapper

does anybody have a clear howto for this ?

---

### Post by Yaniv on 2005-04-12
I've written a howto for the native drivers, including WPA support. find it here [http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo/](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo/)

---

### Post by pieter hollenberg on 2005-04-12
I am trying, but I get an error when using the command "QMAKE" !

I need the RAconfig but it doesn't work because of " qmake"  page 3.

where can I find this qmake ?

---

### Post by pieter hollenberg on 2005-04-12
found out in the readme that qmake is part of the QT development kit of trolltech.com

after downloading qt-x11-eval-3.3.4 I don't understand how to install it.

the install file is too difficult for a newbie.

how did you install qt ? 

is there a deb of ubuntu package of qt-x11 ??

---

### Post by ganatronic on 2005-04-12
I got stuck installing that version of qmake also. 

So instead I just went into synaptics and got a qt kit. I can't remember exactly what it was called. But I just searched "qt" and installed the one that seemed to fit the description. It was within the first half of the results. Once I get off work (in five hours) I can post the actual name of it. It did the trick.

---

### Post by markthecarp on 2005-04-12
[QUOTE=lordofkhemenu]#: ndiswrapper -i /path/to/the/driver/Rt2500.INF
#:ndiswrapper -m
add a line *ndiswrapper* to /etc/modules
 Use the networking applet (System|Administration|Networking) to activate and configure wlan0
add *auto wlan0* to /etc/network/interfaces


Anybody else feel free to elaborate or correct the order of my steps (I'm doing from memory...I read the ndiswrapper site instructions and haven't had to fsck with it since).[/QUOTE]

The first step described here failed for me untill I saved all the files in...

mark@stingray:~/downloads/wifi-drivers $ l /media/cdrom0/DRIVER/WinXP/
rt2500.cat  Rt2500.INF  rt2500.sys

to

mark@stingray:~/downloads/wifi-drivers $ l
rt2500.cat  Rt2500.INF  rt2500.sys

btw, "l" is an alias for "ls", not "ls -l". I then su'd to root and did "ndiswrapper -i <pathtowhereisavedit>" I now get the following from...

mark@stingray:~/downloads/wifi-drivers $ ndiswrapper -l
Installed ndis drivers:
rt2500  driver present, hardware present
mark@stingray:~/downloads/wifi-drivers $ iwlist wlan0 scan
wlan0     No scan results

I do not have a wireless ap or router. winders detects two in one spot about two blocks away....oh I need cigs, must venture out....

-mark

---

### Post by Mr_THX on 2005-04-12
[QUOTE=ganatronic]I got stuck installing that version of qmake also. 

So instead I just went into synaptics and got a qt kit. I can't remember exactly what it was called. But I just searched "qt" and installed the one that seemed to fit the description. It was within the first half of the results. Once I get off work (in five hours) I can post the actual name of it. It did the trick.[/QUOTE]


Yeah I am gonna need to know what that is because I compiled the qt kit from their site and it seemed to work alright after I got it set up.  Once I did the qmake though for the rt500 file I got a bunch of errors.  Even though I followed their directions, there is a 100% chance I messed something up.

---

### Post by kamakazieKiwi on 2005-04-13
try qt3-dev-tools

I needed WPA which I couldn't do with ndis wrapper.  my final solution has been to reinstall and follow the guide to installing the native rt2500 drivers again. This time it seems ok. 

Also, at least for amd64, there wasn't a kde-base, it was kdebase.

---

### Post by magicfab on 2005-04-14
[QUOTE=Yaniv]I've written a howto for the native drivers, including WPA support. find it here [http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo/](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo/)[/QUOTE]

It would have saved me a couple of hours last night if it had been linked from the rt2x00 web site HowTo page. I just wrote to the author to request the link.

---

### Post by ganatronic on 2005-04-15
Good idea. That HowTo is much better than the Debian one they have listed.

---

### Post by magicfab on 2005-04-15
[QUOTE=ganatronic]Good idea. That HowTo is much better than the Debian one they have listed.[/QUOTE]
 I have revised the HowTo and confirm that it works. I have started another thread on this.

---

### Post by im_ka on 2005-05-02
[QUOTE=Yaniv]I've written a howto for the native drivers, including WPA support. find it here [http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo/](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo/)[/QUOTE]

works like a charm with my cheapo conceptronic card. thanks a lot, this is a great relief!

i even advertise your howto on my blog ;)

---

### Post by Guy on 2005-05-25
[QUOTE=Yaniv]I've written a howto for the native drivers, including WPA support. find it here [http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo/](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo/)[/QUOTE]


wile trying to go with the "howto" i stopd at step 3.

it said: E: Couldn't find package linux-headers-2.6.10-4-386

i tried also another repository. but didn't find.

how can i go on ?

i have ubuntu 5.04 hoary hedgehog on a toshiba laptop.

thank you for your time.

---

### Post by cdean on 2005-05-28
[QUOTE=Guy]wile trying to go with the "howto" i stopd at step 3.

it said: E: Couldn't find package linux-headers-2.6.10-4-386

i tried also another repository. but didn't find.

how can i go on ?

i have ubuntu 5.04 hoary hedgehog on a toshiba laptop.

thank you for your time.[/QUOTE]
 Make sure that you've enabled the online repositories.

---

### Post by devillion on 2005-05-29
[QUOTE=lordofkhemenu]#: ndiswrapper -i /path/to/the/driver/Rt2500.INF
#:ndiswrapper -m
add a line *ndiswrapper* to /etc/modules
 Use the networking applet (System|Administration|Networking) to activate and configure wlan0
add *auto wlan0* to /etc/network/interfaces


Anybody else feel free to elaborate or correct the order of my steps (I'm doing from memory...I read the ndiswrapper site instructions and haven't had to fsck with it since).[/QUOTE]

This worked for me...sort of. Now my card (Belkin F5D7010) shows up under Networking, and i can enable it, but it can't get out to the net. What tests can i run to see where the error lies? And by, "add a line", what do you mean? I skipped these steps because my card seemed to be working, and because i didn't understand them. (i now see it is not working :P)

The wiki page on this subject did not even get my card detected, but this more simpler version did, for whatever reason. Thank you lordofkhemenu.

Sorry to bump this thread (sage? :P)

---

### Post by leperisland on 2005-07-06
Hello,

I'm not sure wether I should be using the rt2400 or rt2500 drivers. I have an Asus wifi-b card that goes into a custop port on mu Asus 87N8X-E motherboard.

Any help would be greatly appreciated. I tried the rt2400 installation and it seemed Ok & I can see it in my network admin list but the card won't light up & doesn't function.

thanks,

Caroline

---

### Post by leperisland on 2005-07-06
[QUOTE=cdean]Make sure that you've enabled the online repositories.[/QUOTE]

If you can't get online - is there a way of downlaoding 7 running these repositories or have I completely missed the point?

ta,

Caroline

---

### Post by webx on 2005-08-04
OK, getting a native driver to work with my Belkin F5D7050 USB card has been an absolute nightmare.  Sure, I have ndiswrapper working fine, but that means I can't do any sort of auditing.  I have followed the steps on the wiki page ([https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)) and I"ve still got nothing.  The driver compiles fine, it passes the insmod test.. and no errors on modprobe but for one reason or another, I get no driver found when I start up the RAConfig utility.   :?

A screenshot showing the RAConfig tool's error, along with the last few commands I executed in the terminal window is here: [http://tinyurl.com/826rn](http://tinyurl.com/826rn)

Any help is greatly appreciated.

Thanks in advance,
Bill (webx)

---

### Post by mutejute on 2005-08-18
[QUOTE=webx]OK, getting a native driver to work with my Belkin F5D7050 USB card has been an absolute nightmare.  Sure, I have ndiswrapper working fine, but that means I can't do any sort of auditing.  I have followed the steps on the wiki page ([https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)) and I"ve still got nothing.  The driver compiles fine, it passes the insmod test.. and no errors on modprobe but for one reason or another, I get no driver found when I start up the RAConfig utility.   :?

A screenshot showing the RAConfig tool's error, along with the last few commands I executed in the terminal window is here: [http://tinyurl.com/826rn](http://tinyurl.com/826rn)

Any help is greatly appreciated.

Thanks in advance,
Bill (webx)[/QUOTE]
 i have the same problem with webx. i followed the rt2500 howto and everything went ok until i ran network-admin. my wireless device is not listed, only eth0 and modem showed up. if i run Raconfig, it displays no driver found.  i tried reinstalling/compiling different versions of the driver but still no luck.

if i run ifconfig, i cant see ra0 or any wireless device. iwconfig says 'no wireless extensions'.

thanks.

---

### Post by SpaulS on 2005-08-18
I am running with a rt2500 wireless card, and the instructions at:

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

worked quite well.

I noticed on your screen shot you tried to start RaConfig before you brought up the network interface. Try:

sudo ifconfig ra0 up

or

sudo ifup ra0

Then RaConfig should work.

---

### Post by mutejute on 2005-08-19
[QUOTE=SpaulS]I am running with a rt2500 wireless card, and the instructions at:

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

worked quite well.

I noticed on your screen shot you tried to start RaConfig before you brought up the network interface. Try:

sudo ifconfig ra0 up

or

sudo ifup ra0

Then RaConfig should work.[/QUOTE]
 how do i know if my rt2500 is working? if i run "sudo ifconfig ra0 up", i get this message:

ra0: ERROR while getting interface flags: No such device

i think my rt2500 is not enabled or detected thats why i cant see the device when i run system-->administration-->networking.

i followed the instructions from Rt2500WirelessCardsHowTo and all went fine except the RaLink card doesnt show up at the Networking window.  So if I run RaConfig2500, it will show "Device driver not found".

Please help. Thanks in advance.

---

### Post by desenfrenada on 2005-09-03
I had exactly the same problem as mutejute, until I found 
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=43](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=43)

The poster used the 2570 driver, which worked for him (and me).

EDIT: sry mutejute, I overlooked you use a card not an usb device. My USB WLAN stick does work with the 2570 driver.

---

### Post by thebigfatgeek on 2005-10-25
I am running Breezy, and use a Belkin G USB stick (F5D7050). I got the drivers isntalled with ndiswrapper, but when I activate it in System->Administration->Network, it is not displayed there. Using dmesg I get an error  "usb 3-2: reset high speed USB device using ehci_hcd and address 4". Running depmod -a stops that nonsense and dmesg then comes up with the message

" wlan0: ndiswrapper ethernet device 00:11:50:46:86:64 using driver rt2500usb, configuration file 050D:7050.0.conf"

and I can then configure the unit in System->Administration->Network, and it will work fine, until I reboot.

On reboot the system hangs when loading hotplug until I disconnect the USB unit.  After login I can go back to System->Administration->Network and reactivate the card and carry on working, but that is a bit silly.

How can I resolve the issue?

Thanks

---

### Post by `GooZ´ on 2005-11-10
I have got this chipset, and in hoary I couldn't get it to work either, but in breezy it works like a charm

---

### Post by jago25_98 on 2006-01-16
I don't have the rt2500 module and [https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo/) doesn't mention it.

Where do I get that module? [http://prdownloads.sourceforge.net/rt2400/rt2500-1.1.0-b3.tar.gz?download](http://prdownloads.sourceforge.net/rt2400/rt2500-1.1.0-b3.tar.gz?download) doesn't insert into 2.6.10-k7 even though /usr/src/linux is linked to the source that matches the running kernel

---

