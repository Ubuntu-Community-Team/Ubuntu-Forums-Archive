---
title: "wireless connectivity problems"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by Reversik on 2008-07-29
Ok I am running a 8187 Realtek Semiconductor Corp. so I'm pretty sure that it works for linux. Now I've tried a lot of the wireless configuration and such, also I have tried to get wifi managers but they don't seem to want to work. My router doesnt have a WEP or any type of key on it so it's not that, I just am looking for a bit of advice on what I should do. Everytime I look into the KNetworkManager and try to connect it won't and sometimes will. But I am looking for it to work all the time without the need of a ethernet cable.

---

### Post by pytheas22 on 2008-07-29
Is your wireless recognized at all?  If so, what is the output of:
```

iwconfig
iwlist scan
```

If it's not recognized, try following these [instructions]("http://rtl-wifi.sourceforge.net/wiki/Installing") for installing the Realtek drivers.  I'm not positive that they apply to your card, as I've never owned any Realtek wireless devices and am a bit confused as to which ones use which drivers, but I think that the ones at that site are what you need.

If the first site doesn't work, try [here]("http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy").

Finally, this [thread]("http://ubuntuforums.org/showthread.php?t=846249&highlight=RTL-8185&page=3") may be useful for reference.

---

### Post by dentaku65 on 2008-07-29
Try these commands in sequence, please change eth1 with your wi-fi dev if necessary/different:
```
sudo killall -9 dhclient
sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo iwlist scan
sudo iwconfig eth1 essid "<your_essid>"
sudo iwconfig
sudo dhclient eth1
sudo ifconfig eth1 mtu 1492

```

---

### Post by jkhh07 on 2008-07-29
I am having problems with my connection issue as well. 

[B]Broadcom 4328 wireless card a/b/g/pre-N running on an HP 6715b Business Notebook
Ubuntu 8.04 with Ndiswrapper[/B]

I can connect to my Belkin Wireless N router at home, _BUT ONLY through A non-secure connection_. When I enable security on my router using WPA1 Personal or WPA2 with PSK, I canNot connect. My computer picks up the signal and everything. I enter the network name, define type of authentication, and enter PSK but gets to a status of "waiting on network key from router" 

***I CAN connect*** to a WPA2 at work with PSK. Both PSK at work and home are 8 characters long. I have tried the exact same setup with both HP drivers and Dell Drivers.

HELP!!

---

### Post by pytheas22 on 2008-07-29
> I am having problems with my connection issue as well.
Broadcom 4328 wireless card a/b/g/pre-N running on an HP 6715b Business Notebook
Ubuntu 8.04 with Ndiswrapper

I can connect to my Belkin Wireless N router at home, BUT ONLY through A non-secure connection. When I enable security on my router using WPA1 Personal or WPA2 with PSK, I canNot connect. My computer picks up the signal and everything. I enter the network name, define type of authentication, and enter PSK but gets to a status of "waiting on network key from router"

I CAN connect to a WPA2 at work with PSK. Both PSK at work and home are 8 characters long. I have tried the exact same setup with both HP drivers and Dell Drivers.

HELP!! 

You have a completely different wireless card from the original poster in this thread and a different kind of problem, so I think it would be better if you started a new thread for your issue.  Please do that and let us know the URL, and I'll reply there.  Also, in your thread, please include the output of these commands (run them immediately *after* trying to connect to your WPA network at home):
```

dmesg
ndiswrapper -l
iwconfig
```

(dmesg will be long, but please provide it all).

It also wouldn't hurt if you ran the command:
```

iwlist scan
```

both at home and at work, and provided the output from the two scans.  That output will tell us what exactly is different (besides the network name) between the two networks.

Also, does your password at home contain any special characters, like blank spaces, $, ^...?  Sometimes they can cause problems.

---

### Post by Reversik on 2008-07-30
> **pytheas22 said:**
> Is your wireless recognized at all?  If so, what is the output of:
```

iwconfig
iwlist scan
```

If it's not recognized, try following these [instructions]("http://rtl-wifi.sourceforge.net/wiki/Installing") for installing the Realtek drivers.  I'm not positive that they apply to your card, as I've never owned any Realtek wireless devices and am a bit confused as to which ones use which drivers, but I think that the ones at that site are what you need.

If the first site doesn't work, try [here]("http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy").

Finally, this [thread]("http://ubuntuforums.org/showthread.php?t=846249&highlight=RTL-8185&page=3") may be useful for reference.

Ok now on that wiki page or real tek setup, how am I supposed to install the driver I'm used of just getting the app for adept or a code. The rest of the instructions I think I can follow pretty clear.

I went to this site to find the thing that makes it work for realtek which was the realtek site and I went to my usb type of wireless.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#1432](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#1432)

After I download that I don't know how to really install it I'm pretty new to linux , been through hell trying to get damned wireless working.

Would it be simple if I could get a Apt-install of it or something? Sorry if I seem unreasonable and a bit stupid but it's just a bit frustrating.

---

### Post by jkhh07 on 2008-07-30
*[I]_STARTED NEW THREAD:_*[/I] ***Hardy 8.04 Wireless Networking for N-Routers / Broadcom Wireless Cards ***
[http://ubuntuforums.org/showthread.php?p=5487704#post5487704](http://ubuntuforums.org/showthread.php?p=5487704#post5487704)

---

### Post by pytheas22 on 2008-07-30
> Would it be simple if I could get a Apt-install of it or something? Sorry if I seem unreasonable and a bit stupid but it's just a bit frustrating.

Don't feel bad about being confused; compiling drivers from source is not beginner-friendly stuff.  But unfortunately, in your case, it's probably the only way to get the wireless to work, as there is no package available for download via apt-get.

The wiki page assumes that you have access to a wired ethernet connection in order to download the stuff you need to compile the driver for wireless.  If it's totally impossible to get a wired connection, there are still ways to do what you need, but it would be much easier if you can find somewhere to plug in temporarily.  Please let me know if that's possible, and I'll give you specific instructions on which commands you need to run to make the wireless work.

---

### Post by Reversik on 2008-07-30
Yea, I have a ethernet cable right by me , I have a desktop which has the modem and router plugged into it.

---

### Post by pytheas22 on 2008-07-30
Alright, good.  Try running these commands then and see if it helps:

First, go to [http://rapidshare.com/files/92812937/rtl818x-mod2.6.24.tar.bz2.html](http://rapidshare.com/files/92812937/rtl818x-mod2.6.24.tar.bz2.html) and download that file.  Save it to your desktop.  Right-click on it and select "extract here."

Then run:
```

sudo -s
apt-get install build-essential subversion module-assistant
module-assistant prepare
mv /lib/modules/`uname -r`/kernel/net/ieee80211 ~/ieee80211.MOVED
modprobe -r ieee80211
cd Desktop/rtl-wifi
make
insmod ieee80211/ieee80211_crypt-rtl.ko
insmod ieee80211/ieee80211_crypt_wep-rtl.ko
insmod ieee80211/ieee80211_crypt_tkip-rtl.ko
insmod ieee80211/ieee80211_crypt_ccmp-rtl.ko
insmod ieee80211/ieee80211-rtl.ko
insmod rtl8187-newstack/r8187.ko
```

now wait a few seconds and then post the output of:
```

iwlist scan
```

and report back.  If iwlist scan yields results, then we can install the driver permanently.

---

### Post by Reversik on 2008-07-30
Here is what I got when I used your code, I not sure if something went wrong in it but I think I might be sure...

root@world:~# sudo -s
root@world:~# apt-get install build-essential subversion module-assistant
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
subversion is already the newest version.
module-assistant is already the newest version.
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd libshp1 libdns32 libqt3-mt-sqlite liblua5.1-0
  libadns1 wireshark-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@world:~# module-assistant prepare
Getting source for kernel version: 2.6.24-19-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd libshp1 libdns32 libqt3-mt-sqlite liblua5.1-0
  libadns1 wireshark-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
root@world:~# mv /lib/modules/`uname -r`/kernel/net/ieee80211 ~/ieee80211.MOVED
mv: cannot stat `/lib/modules/2.6.24-19-generic/kernel/net/ieee80211': No such file or directory
root@world:~# modprobe -r ieee80211
root@world:~# cd Desktop/rtl-wifi
bash: cd: Desktop/rtl-wifi: No such file or directory
root@world:~# make
make: *** No targets specified and no makefile found.  Stop.
root@world:~# insmod ieee80211/ieee80211_crypt-rtl.ko
insmod: can't read 'ieee80211/ieee80211_crypt-rtl.ko': No such file or directory
root@world:~# insmod ieee80211/ieee80211_crypt_wep-rtl.ko
insmod: can't read 'ieee80211/ieee80211_crypt_wep-rtl.ko': No such file or directory
root@world:~# insmod ieee80211/ieee80211_crypt_tkip-rtl.ko
insmod: can't read 'ieee80211/ieee80211_crypt_tkip-rtl.ko': No such file or directory
root@world:~# insmod ieee80211/ieee80211_crypt_ccmp-rtl.ko
insmod: can't read 'ieee80211/ieee80211_crypt_ccmp-rtl.ko': No such file or directory
root@world:~# insmod ieee80211/ieee80211-rtl.ko
insmod: can't read 'ieee80211/ieee80211-rtl.ko': No such file or directory
root@world:~# insmod rtl8187-newstack/r8187.ko


I followed your directions directly and extracted it here which was apparenlty the desktop which I see in the command. So I'm not quite sure why it says no such file or directory.

---

### Post by Reversik on 2008-07-30
Even though that didn't go through from the looks I put in iwlist scan and got 

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:BA:D4:B9
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/64  Signal level=50/65
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000002c41610b595

---

### Post by pytheas22 on 2008-07-30
Yes, the code didn't work.  Did you download the file from [http://rapidshare.com/files/92812937/rtl818x-mod2.6.24.tar.bz2.html](http://rapidshare.com/files/92812937/rtl818x-mod2.6.24.tar.bz2.html) and extract it?  If you did it properly, there should be a folder on your desktop named rtl-wifi.  I think that's the problem.

But I didn't realize that you can see networks now at all (I guess I read your first post too fast).  Can you connect with this command (as someone already suggested):
```

sudo iwconfig wlan0 mode managed channel 6 essid "linksys"
sudo dhclient wlan0
```

try it a few times and see if it connects you.

---

### Post by Reversik on 2008-07-31
> **pytheas22 said:**
> Yes, the code didn't work.  Did you download the file from [http://rapidshare.com/files/92812937/rtl818x-mod2.6.24.tar.bz2.html](http://rapidshare.com/files/92812937/rtl818x-mod2.6.24.tar.bz2.html) and extract it?  If you did it properly, there should be a folder on your desktop named rtl-wifi.  I think that's the problem.

But I didn't realize that you can see networks now at all (I guess I read your first post too fast).  Can you connect with this command (as someone already suggested):
```

sudo iwconfig wlan0 mode managed channel 6 essid "linksys"
sudo dhclient wlan0
```

try it a few times and see if it connects you.

I extracted the file you told me to download and then extract it to "Here" which would be the desktop but apparently it's not reading that? I'll try to do th connect when I am back on my kubuntu.

---

