---
title: "TP-Link WN321G (RT73/RT2500)"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by bouncer5 on 2008-02-12
Well I bought this as I was told it would work in linux, Linux finds it but thats, I dunno if theres driveres installed for it or what as its got a funny name like 54.......

---

### Post by rustybronco on 2008-02-12
Open a terminal and type in **lsusb** then look for the chipset. (RT73, RT2571, ECT.)

A few choices depending on what you find for a chipset.
[http://ubuntuforums.org/showpost.php?p=2395871&postcount=1](http://ubuntuforums.org/showpost.php?p=2395871&postcount=1)
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

a great tutorial by Kevdog [http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

---

### Post by bouncer5 on 2008-02-13
I got 

"Bus 001 Device 002: ID: 148f:2573 Ralink Technology Corp."

Altho in the hardware manager the driver it is using is rt73usb

I have been to the Ralink Website and downloaded the drivers which included the group "2573" I think that is my chipset

---

### Post by rustybronco on 2008-02-13
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070)
```
  Kyle M Weller wrote on 2008-01-10: (permalink) 
yes, I can confirm the rt73usb.ko driver does not work for "ANY RELEASE"
never did, although the rt73 driver from here:
[http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)
works fine. Wpa works great as well, unfortunately any wpa password longer
than 20 characters crashes Ubuntu and locks up the box, oops, nevermind,
just checked this forum thread:
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=28063#28063](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=28063#28063)
it seems the password length issue has been resolved for wpa with the rt73
driver from serialmonkey, basically here is how to install:
wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)
tar zxvf rt73-cvs-daily.tar.gz
cd rt73*
cd M*
make
sudo make install
sudo gedit /etc/modprobe.d/blacklist
append this to the end of the file:
# rt73 blacklisted drivers
blacklist rt2500usb
blacklist rt73usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist ipv6
now sudo /etc/init.d/networking restart and we shall be connected if
/etc/network/interfaces file is configured correctly, here is an example of
mine:
# WORKING STATIC AES/WPA CONFIG
#auto wlan0
#iface wlan0 inet static
#address 192.168.1.66
#netmask 255.255.255.0
#gateway 192.168.1.254
#pre-up ifconfig wlan0 up
#pre-up iwconfig wlan0 essid 2WIRE
#pre-up iwconfig wlan0 mode managed
#pre-up iwpriv wlan0 set Channel=9
#pre-up iwpriv wlan0 set AuthMode=WPAPSK
#pre-up iwpriv wlan0 set EncrypType=AES
#pre-up iwpriv wlan0 set WPAPSK=yourwpapasswd
#pre-up iwpriv wlan0 set TxRate=0

# WORKING DYNAMIC AES/WPA CONFIG
auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid 2WIRE
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set Channel=10
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK=yourwpapasswd
pre-up iwpriv wlan0 set TxRate=0
mtu 1500
There we go rt73 working perfectly, now, lets watch and see if the Ubuntu
developers can add this wonderful driver to Gutsy and Heron...
Kyle Weller
On Jan 10, 2008 12:03 AM, Piotr Makowski < oponek@*> wrote:

> I checked Hardy and there are still problems with some ralink cards...
> -> [https://bugs.launchpad.net/bugs/134660](https://bugs.launchpad.net/bugs/134660)
>
> --
> [Gutsy] Ralink 2573 usb adapter does not work out of the box
> [https://bugs.launchpad.net/bugs/139070](https://bugs.launchpad.net/bugs/139070)
> You received this bug notification because you are a direct subscriber
> of the bug.
> 
```
there was a post in that link about two different chipsets with that id, so i'd read it all...

---

