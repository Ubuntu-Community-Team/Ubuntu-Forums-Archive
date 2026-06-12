---
title: "RT2500 Wireless Card CONSTANTLY losing connection, need help!"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by quadomatic on 2007-12-11
Hey,

I've been using a Zonet ZEW1601 PCI Wireless card in Ubuntu for a while now. The wireless chipset it uses is an RT61.

Ever since I upgraded to Gutsy, I've had problems with constantly losing my connection over some amount of time. Sometimes it takes minutes to lose my connection, other times it takes hours, but I always lose my connection.

I've tried the drivers that are there by default, and I've tried ndiswrapper using the stickied guide ([http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)) with the official Ralink Windows drivers that work flawlessly for me in Windows XP, and I still lose my internet connection. NOTHING seems to work.

Is there anything else I can do to try and get my wireless to work? I don't know what else to do.

I found these Serialmonkey drivers though:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

Are they the same drivers that Ubuntu uses by default?

Thanks

---

### Post by super.rad on 2007-12-14
No they're not the same drivers that ubuntu uses and yes they should sort out your problem as I use an RT61 card and had the same problem with wireless signal dropping until i installed the serialmonkey drivers and it's working perfectly now.
If you dont already have linux-headers and build-essential installed run the following from the terminal to install them.
```
sudo aptitude install linux-headers-`uname -r` build-essential
```

Then download the CVS hourly tarball from the website, open a terminal and change directory to wherever you downloaded it.
Extract the drivers
```
tar -xvzf rt61-cvs-daily.tar.gz
```
Change directory again into the newly extracted folder
eg
```
cd /home/superrad/downloads/rt61-cvs-yyyymmddhh/Module
```
note: yyyymmddhh corresponds to the numbers
found on the extracted directory.
Then run the following in the terminal
```
sudo make
```
and once that finishes
```
sudo make install
```
Go to System > Administration > Network and configure your network settings if they aren't already.
Finally restart and it should be done and won't lose signal again.

---

### Post by wieman01 on 2007-12-14
One thing that you could try is to change the wireless channel on the router. Networks around you might interfere with yours.

---

