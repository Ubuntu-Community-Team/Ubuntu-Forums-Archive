---
title: "I may be an idiot......"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by new selearner on 2007-11-08
Hi all, 

I'm completely new to Ubuntu and have installed it dual boot style with XP.  After finally getting my hard disks to show up properly and be accessed from both OS', i think it's time to have a crack at my wireless problems.  In short - it doesn't work!!!  

I have a Belkin f5d7050 v4001, and I think i need the driver zd1211rw.  Only problem is that the only files I can find to download are one called zd1211-firmware-1.4.bz2, and one called zd1211memtoolv0.1.  I have tried the links from this site to [www.linuxwireless.org/en/users/Drivers/zd1211rw](www.linuxwireless.org/en/users/Drivers/zd1211rw), but cant see the link to dowload the file itself!!!!!! Am I being a blind fool or am I looking in the wrong place?

Thanks, any help would be greatly appreciated!

---

### Post by new selearner on 2007-11-08
forgot to mention, im using ubuntu 6.06 (that's dapper drake right?).

Thanks

---

### Post by Gregmond on 2007-11-08
> **new selearner said:**
> forgot to mention, im using ubuntu 6.06 (that's dapper drake right?).

Thanks

Not an expert myself, still learning, however Drivers have come a long way in the last couple of years. You are using a version of Ubuntu that is now 14 or 15 Months and 2 generations old. Whilst I understand that it is the LTS (Long Term Support) version, you may be better off with Fiesty Or Gutsy (just updated all my PC's to Gutsy). Note: I don't use wireless, so I may be totally on the wrong track and I am not sure where the drivers you seek are.

Goodluck :)

---

### Post by mpierce on 2007-11-08
Depending on which kernel version you are running with LTS, the drivers may already be included as modules. 

Look at the recent posts on wireless problems that have my name or do a search on posts with name, mpierce. 

You may only have to edit a file and tell your wireless card how it is being managed, essid, and WEP to get it to work. 

Hope this helps...

---

### Post by SpiritIsReality on 2007-11-09
howdy
[http://www.google.ca/search?hl=en&q=site%3Andiswrapper.sourceforge.net+zd1211rw&btnG=Search&meta=]("http://www.google.ca/search?hl=en&q=site%3Andiswrapper.sourceforge.net+zd1211rw&btnG=Search&meta=")
click Edit (top left of Firefox window) >(click) Find in This Page. Then at the bottom of the window type in zd1211rw and then if you have to, click next.(right beside where you typed in your chip.)
If I was me, I'd install gutsy.
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)
[http://www.google.ca/search?hl=en&q=ndiswrapper&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=ndiswrapper&btnG=Google+Search&meta=)
all the best
trails:lolflag:

---

### Post by new selearner on 2007-11-09
Thanks for all the replies, im considering upgrading to the latest version of ubuntu now - I didn't realise the release I was using was that old!!!!

I thought id post some output from the commands I've picked up to do with wireless - maybe someone can shed some light on whether the driver is loaded or not!  

(a lot of this may not be relevant but I thought i'd give as much info as possible):

sudo lshw shows the device as:

* - usb   UNCLAIMED
desription: generic usb device
product: USB 2.0 WLAN
vendor: Belkin
Physical id: 2
bus info:  USB@5:2
version: 48.10
capabilities:  USB -2.00
configuration: max power = 500mA speed =480.0Mb/s

lsusb shows:

Bus 005 Device 005: ID: 050d:705c Belkin components

iwconfig shows:

lo           no wireless extensions

sit0        no wireless extensions

*edit:  no wlan0 shown

System > Administration > Networking only shows unconfigured modem connection

I have also tried using windows drivers BLKWGU.sys, BLKWGUXP.sys and rt73.sys with ndiswrapper but it shows invalid driver (ndiswrapper -l).

Sorry if this is all useless info - i don't really know what im doing and thought maybe this would show where the problem lies!!

Thanks a lot for your patience!!!

---

### Post by SpiritIsReality on 2007-11-09
howdy
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)
could be some help here
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver))
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+050d%3A705c&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+050d%3A705c&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=050d%3A705c&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=050d%3A705c&btnG=Google+Search&meta=)
trails

---

### Post by madsmaddad on 2007-12-11
I also use a ZD1211 device - the 3com USB stick. It worked 'out of the box' in Feisty, and also when I upgraded to Gutsy. I did the upgrade over the wireless!  

I am also dual Boot feisty and XP, 

So yeah, I think an upgrade will sort your problem. 

I am still struggling to get Encryption working, but otherwise it is superb. It works first time every time, where sometimes the XP boot doesn't make a wireless connection and needs a reboot. 

Peter M.:)

---

### Post by Scotty Bones on 2007-12-11
Don't know how helpfully this will be, but i'm sure the process will be similar. This is how I got my linksys to work. NOTE - I'm pretty new at this myself

Download the Windows Driver setup util from the manufacturer's website (should be an .exe)
Use an extractor like WinRAR (I'm sure this could be done within Ubuntu, I'm just not sure how).  There should be several files in there that can be extracted
The file your looking for should be a .sys file. In my case it was  bcmwl5a.sys
In Gutsy open the Restricted Drivers Manager, hopefully you should see your wireless card listed there.  Check the enable box and point it to your driver.  Note you will need a connection to the net to install the driver from here.

I hope that this is helpful in some way.

---

### Post by Chadarius on 2007-12-28
If you are upgrading to 7.10, the card is supported out of the box. However, if you need it to connect to WPA encrypted wireless networks you will need to update the firmware. This is really easy.

Newer versions of the Linux kernel (kernel 2.6.18-rc1 and higher) already contain the latest zd1211rw drivers. You do not need to blacklist or compile any drivers. In fact, if you are using unencrypted or wep encryption you should have full support built directly into the 7.10 release. However, WPA is not supported without updating the firmware for this usb wireless card.
Updating the firmware to support WPA

[LIST=1]
[*]Download the firmware
[INDENT]Download zd1211-firmware-1.4.tar.bz2 from [http://sourceforge.net/project/showfiles.php?group_id=129083](http://sourceforge.net/project/showfiles.php?group_id=129083)[/INDENT]
[*]Uncompress and untar the file with the following command (or your favorite way to handle tar.bz2 files
[INDENT]```
tar -xvvjf zd1211-firmware-1.4.tar.bz2
```[/INDENT]
[*]Copy the firmware files to the proper location
[INDENT]```
cd zd1211-firmware
sudo cp zd1211_* /lib/firmware/zd1211

```[/INDENT]
[*]Unplug the F5D7050 device from the computer
[*]Make sure the driver is unloaded
[INDENT]```
sudo rmmod zd1211rw
```[/INDENT]
[*]Plug the usb device in again
[*]The driver should load using the new firmware and WPA will be supported. If for some reason the driver isn't loading either reboot, or run the following command:
[INDENT]```
sudo modprobe zd1211rw
```[/INDENT]
[/LIST]

---

