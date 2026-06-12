---
title: "Realtek rtl8188SU"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by cam4 on 2014-05-19
using a n150 wifi usb adapter, f9l1001 model name.
Not showing on ifconfig.
shows under lsusb. 
Really frustrating please help.

---

### Post by kurt18947 on 2014-05-20
Hi

No expert here but I've had a little experience with Realtek wifi devices.  The site wikidevi says this about f9l1001:

[https://wikidevi.com/wiki/Belkin_F9L1001](https://wikidevi.com/wiki/Belkin_F9L1001)

If you do "lsmod", is r8712u listed?  Here is a script that shows many useful items when trouble shooting wireless problems:

[http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)

I seem to recall the rtl8188SU being a bit of a challenge.  Realtek appears to not have kept up support for this chip set with current kernels.  The latest shown for Realtek's driver is 3.0.2, Ubuntu 14.04 is 3.13.x

[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

My solution for wireless problems has become to buy one that works out of the box.  I've had very good luck with TrendNet's TEW-649UB which uses a realtek 8192SU chip and is driven by the r8712u module as well but it works.  I don't know that this device would be good for laptops running on battery, it can get fairly warm when used heavily so it might shorten battery charge life.  Any device using Ralink/Mediatek's rt5370 chipset seems to work without tweaking though my signal strength is not the greatest.  These adapters can be found for less than $15.

Perhaps someone more knowledgeable or experienced can help further.

---

### Post by pdc on 2014-05-20
folks often warn of older posts; however chili responded for this device here [http://ubuntuforums.org/showthread.php?t=1705004](http://ubuntuforums.org/showthread.php?t=1705004) and at that stage was recommending a firmware install would cure the issue; 

the commands then were:

> sudo mkdir /lib/firmware/RTL8192SU
wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

__________________________________________________________

from this Debian thread; [https://wiki.debian.org/rtl819x](https://wiki.debian.org/rtl819x) (I was looking to see if a module for this device was in the linux kernel; and it is; and has been for a while);

it says 

> r8712u (supported devices)

    Supports USB devices based on the [COLOR="#008000"]RTL8188SU[/COLOR], RTL8191SU and RTL8192SU chips.

    Introduced in Linux 2.6.37,6 enabled at linux-2.6 2.6.37-1~experimental.1.  

and they go on to say

> Non-free firmware is required for all drivers, which can be provided by installing the [COLOR="#0000FF"]firmware-realtek[/COLOR] package.

the link they give on debian for that is [https://packages.debian.org/search?keywords=firmware-realtek](https://packages.debian.org/search?keywords=firmware-realtek)

I would have thought one could download that; but click to get it from the architecture for your device; I would have thought the firmware is essentially the same as in Chili's post

all advice is given in good faith; only you can do things to your computer

---

