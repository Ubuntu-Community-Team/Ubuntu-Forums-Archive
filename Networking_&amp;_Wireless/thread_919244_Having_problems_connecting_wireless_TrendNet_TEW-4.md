---
title: "Having problems connecting wireless TrendNet TEW-424UB    USB"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by Randall L. on 2008-09-13
I am having problems getting an internet connection set up on Ubuntu. (v. 7.10) The problem is that I don't have a hard connection to this computer either. I have checked multiple forums and have tried to get it to work already.
The drivers I used I got from here:
[http://trendnet.com/downloads/list_subcategory.asp?SUBTYPE_ID=1049](http://trendnet.com/downloads/list_subcategory.asp?SUBTYPE_ID=1049)

Help would be appreciated

Thanks,
Randall

---

### Post by Randall L. on 2008-09-13
Bump

---

### Post by Randall L. on 2008-09-13
bump again

---

### Post by Randall L. on 2008-09-15
bump. Any suggestions from anyone?

---

### Post by speed32219 on 2008-09-19
I just bought it last night.  I was just looking at installing it.  Have you got it working yet?

---

### Post by speed32219 on 2008-09-26
I have it almost working.  I installed ndiswraper-common, utils and one other file using synaptic package manager.  I then downloaded the current driver from Trendnet.  I can see it on the system, the green light in the center ot the device worked once I installed the driver and the system found it.  Everthing looks good, just can't get it to transmit a packet. Checked the device using XP and it worked fine.  Going to do a little research over the weekend.

---

### Post by portach king on 2008-10-04
Any update? I just bought one today. Using ndiswrapper I can get the device working by installing drivers from the disk but I can't get it to connect over a secure network (it hangs on "Waiting for Network Key"). It will connect if I turn security off but thats not something I plan on leaving that way.

---

### Post by Randall L. on 2008-10-23
k, so I got mine working! :). However NDISWRAPPER requires that I enter my WEP key ever time and if u have the exact same wireless adapter then u will need to first get the device to work using NDISwrapper and then when u try run this command

Sudo iwconfig wlan0 essid <Access Point Name> ap <Access Point MAC Address> key <Key in Hex>
This should cause the green dots on NM applet when connecting to both go green and bring but some bars
after that run
sudo dhclient wlan0 
and it should output
renewal in "some amount of seconds" 

I just messed around with these 2 commands in terminal and eventually got it to work that way hope it helps! :)

---

### Post by speed32219 on 2008-10-24
Here is a step by step I used to get the Trendnet 424UB working
using Open Source Code.
The main contributor was **pjasnos**, so thank you sir.

I first removed all drivers I down loaded for the Trendnet wireless and also removed ndiswrapper totally from system using Synaptic package manager found in System/Administration. Then using terminal do the following:

wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up 

NOTE: Make sure patch is applied and no errors in terminal,
if you get an error that patch is not installed then
 run sudo apt-get install patch and continue on.  You will also
get some errors when running ./makedrv, just ignore them.



I added the following full path to wlan0up to my /etc/rc.local
(just before exit 0 line) for auto start during boot.

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/home/YOUR NAME HERE/rtl8187b-modified/wlan0up
ifconfig wlan0 up
dhclient wlan0
exit 0


exit 0

Note:  You can reboot now and it should be almost working.

Now go into System/Administration/Network and you should
see a wireless entry.  Go in and setup your network using WEP (I used 128 bit ascii) and DHCP. (I can only get DHCP working right now)


Just in case you don't have the Trendnet 424UB installed during boot create a shell script that uses WEP as follows:

sudo gedit netup.sh

Then copy and paste the following 3 commands.

sudo iwconfig wlan0 essid **YOUR SSID**
sudo iwconfig wlan0 key **YOUR WEP KEY**
sudo dhclient wlan0

Save the file

You should be finished.  Now, my speed is not that great and I am
experiencing some dropped packets, but it may be my server
placement.  I am working on that next.

Good luck and remeber this is not ndiswrapper.

---

