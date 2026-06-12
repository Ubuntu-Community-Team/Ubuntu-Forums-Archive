---
title: "[SOLVED] Edimax EW-7128g RT61 Chipset - can't get it working"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by vilwarin on 2008-09-14
Hello!

I am really unlucky concerning wireless LAN cards and Linux.
I trashed my previous card (RT2500 Chipset), cause I simply couldn't get it working and got a new one, that said: driver support for Linux...

> Edimax EW-7128g with RALink RT61 Chipset

Now for three days I am trying to get it working on Ubuntu Hardy using the 2.6.24-19-generic Kernel ...

I tried both the Hardy driver rt61pci.ko,
but also compiled the RALink driver rt61.ko.
I deinstalled network-manager, configured the card manually using ifconfig, iwconfig and iwpriv. Finally I also tried the wicd daemon.

here's what is working and what is not.
 
[SIZE="4"]**rt61pci.ko**[/SIZE]
I can configure the card entirely.

> $ifconfig
wlan1     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.16.63  Bcast:192.168.16.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:16400 (16.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr XX-XX-XX-XX-XX-XX-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

> $iwconfig
wmaster0  no wireless extensions.
wlan1     IEEE 802.11g  ESSID:"MY CORRECT ESSID"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I also used iwconfig to set key, encryption mode and authentication mode. But I seem unable to connect. dmesg reads

> [ 4153.598353] wlan1: Initial auth_alg=0
[ 4153.598363] wlan1: authenticate with AP XX:XX:XX:XX:XX:XX
[ 4153.794805] wlan1: authenticate with AP XX:XX:XX:XX:XX:XX
[ 4153.994529] wlan1: authenticate with AP XX:XX:XX:XX:XX:XX
[ 4154.195446] wlan1: authentication with AP XX:XX:XX:XX:XX:XX timed out


When I use wicd I can even see! the AP and according to wicd status bar even connect. The AP is hidden WEP encrypted. Curiously enough I can connect to it with wicd no matter which key I select, so probaly I am not connect after all. I cannot ping the router.


[SIZE="4"]**rt61.ko**[/SIZE]

so I tried the restricted drivers that RALink offers on its webpage. I followed the README along with forum posts in this forum and successfully compiled the module.

Using this driver I basically get the same problems as above with one additional problem: I seem unable to set the ESSID. Using the RALink driver you have a special configuration file (rt61sta.dat), that comes with a couple of binaries. I configured it like this:

> [Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID="MY CORRECT ESSID"
NetworkType=Infra
Channel=0
AuthMode=SHARED
EncrypType=WEP
DefaultKeyID=1
Key1Type=0
Key1Str=MYHEXKEY
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
#WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0
NativeWpa=1

But I am curious whether this file is ever used, since the ESSID does not show in iwconfig. Of course I also tried ifconfig, iwconfig and iwpriv to set the values, the latter one even allows you to set the environment variables found in the rt61sta.dat config file. No difference ESSID resuses to be set.

> $iwconfig
ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-110 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> $ifconfig
ra0       Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.16.63  Bcast:192.168.16.255  Mask:255.255.255.0
          inet6 addr: XX::XX:XX:XX:XX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:184653 (180.3 KB)  TX bytes:0 (0.0 B)
          Interrupt:19 

Furthermore wicd also shows my AP, but in contrast to rt61pci module, does not let me connect to it (the key, encrypt type etc. is correct I tried it with the same card on windows). dmesg reads

> [ 5010.891847] Before wrapper, AuthMode=0, wepStatus=1, pCipher=1, gCipher=1, IEEE8021X=0
[ 5010.891857] After wrapper, the AuthMode=0! wepStatus=1!
[ 5011.492426] XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:
[ 5011.492467] XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:
[ 5011.503823] RT61: RfIcType= 3
[ 5421.932059] ra0: no IPv6 routers present

every time I try to connect. again no ping to the AP.
 
I cannot change the AP ESSID (which includes a space) nor the encrypt type or other things, since I am living in a dormitory.


There are many people with posts out there concerning rt61 chips, but none of those people seemed to have problems at my point. I am grateful for any idea or hint, what the cause could be.

thx!
vilwarin

---

### Post by pytheas22 on 2008-09-14
Please try running these commands, which will install a driver from the [serialmonkey project]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads"); these are usually the best for Ralink cards:
```

sudo -s
apt-get install build-essential rutilt
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
wget http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz
tar -xzvf rt61*
cd rt61*
cd Module
make
make install
```

Then reboot and see if the card works.  I think that it will work with wicd, but if not, you may need to use a special connection manager for Ralink cards called Rultilt, which will be under your System>Administration menu.

If this doesn't work, please post the output here of the commands:
```

lshw -C Network
lspci -nn
lsmod | grep rt
dmesg | grep -e rt61 -e ra
```

Ralink cards actually have very good Linux support (I'm disappointed that you threw out your rt2500 card, because I'm sure we could have made it work with few problems).  Unfortunately, the drivers that ship with Ubuntu for Ralink cards, while good for most devices, are still not as stable as they should be.  The drivers from serialmonkey are older and more reliable.  Why Ubuntu doesn't just use the serialmonkey drivers until the other ones are actually stable for everyone, I don't know.

---

### Post by vilwarin on 2008-09-15
*gasp* 
> PING 192.168.16.1 (192.168.16.1) 56(84) bytes of data.
64 bytes from 192.168.16.1: icmp_seq=1 ttl=64 time=25.3 ms

>Now writing with the wireless card connecting me to the Access Point<

I compiled the serial monkey driver and tried them. I think they are identical or at least very similar to the rt61pci drivers that come with Hardy. In fact I haven't tried them so far, as I read on the serial monkey page some days ago, that some of their drivers are default included with the mainline kernel.


rt2x00 enters mainline kernel - January 2008

> Hi All,

two days ago, January 24th, Linux Kernel 2.6.24 was released. This is the first mainline kernel that includes (sadly a somewhat buggy) rt2x00 release.

Our rt2x00 driver has reached a broader audience, and we all wish to congratulate the developers and most importantly all of our users who provided numerous bug reports and even fixes.

Now, lets continue to work towards a stabler driver!

Luis Correia
rt2x00 Project Administrator 

So wicd lead to exactly the same problems as with rt61pci (since they are probably pretty identical), which means I can find the AP I can connect, according to wicd status bar, but dmesg reads timed out, and at no point I am really connected.

So what did the trick was using rtutils, instead of network-manager, wicd or iwconfig, iwpriv. Those utils are not mentioned in any of the posts, tutorials and howtos I broswed in the last days. I guess I will reply to those, I can still find, and mention them.

Thanks! :)
*hug*

vilwarin

---

### Post by pytheas22 on 2008-09-15
I'm glad you fixed it :)

Actually the rt2x00 drivers are not the drivers that you installed.  rt61 is a "legacy" driver and was never included in the mainline kernel stack (it may have been in the Ubuntu kernel at some point, but I'm not sure).  rt2x00 is the "next-generation" set of Ralink drivers that has been included in the kernel since 2.6.24.  Unfortunately, rt2x00 is still (as the developers admit) buggy.  In contrast, the legacy drivers almost always work very well, which is why I recommended trying rt61.  The downside to them is that they only seem to work using Rutilt, which is not as well documented as it should be.

Ralink itself also provides Linux drivers (the driver that you first tried to use), and the serialmonkey legacy drivers (including rt61) are based on Ralink's.  But Ralink's were never developed as thoroughly as those of the serialmonkey project (I think that they don't even support 64-bit), so your best bet it to use serialmonkey.

Ralink, perhaps the most Linux-friendly wireless vendor, released drivers and documentation under the GPL a long time ago, so its devices almost always work very well once you figure out all of the confusing driver issues and decide which one you need to use.

---

### Post by vilwarin on 2008-09-16
yeah I see what you mean, so getting a card with RALink chipset was not the worst I could get. :)

for the last card, I also got it working 3 years ago thanks to the serial monkey project, but I remembered that I had to recompile the stack kernel with SMP and PREEMPT disabled and that after I did this, I got a lot of problems not having a mainline kernel and having to recompile every new kernel that comes out (I had no bootable kernel at some point). SO I wanted to escape this this time by finding a way/card that works with the stack kernel :)

about rutilt, there is a little outdated, but still useful howto here on ubuntu forums: [http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt](http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt)
and well as said in above post, I tried to mention it in forums, I could get write access to.

thanks for your quick and precise help!
marked the thread as [SOLVED]

vilwarin

---

