---
title: "strange wireless connect, xubuntu 7.10"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by kissson on 2008-01-18
my system is a duron800 sis740 with a rt2500usb by Amigo
now booted with a xubuntu 7.10 livecd
the usb wireless 'thumb' can correctly detected, and it can list wireless network detected in the top right corner

i use manual configuration,(clicking the network list generated automatically wont work, keep on asking and asking and asking my wep key:confused::confused::confused:)
sudo ifconfig wlan0 down (due to the bug:( need to down the interface first to eat the setting)
then i use the network manager gui to config my ssid, wep ascii key as well as dhcp
then:
sudo ifconfig wlan0 up
iwconfig correctly showing the ssid , AP's mac, and I can see
Link Signal level=-46 dBm (connected?)
Tx, Rx all 0 and dhclient cant receive any dhcp offer

and ifconfig now display a new interface call wlan0:ava, it have a same mac address:confused: with wlan0...
wlan0:ava, encap ethernet, inet addr:169.254.7.154, Bcast 169.254.255.255, Mask /16

how come, I don't think it can work, if there are 2 interfaces having the same mac address in a network

added 'auto wlan0' to /etc/network/interfaces
it become:
iface wlan0 inet dhcp
wireless-key s:12345
wireless-essid abcde
auto wlan0
AND so on

then ctrl-alt-backspace, key in command, ifconfig wlan0
still no ip offered

I am sure the network is working, because all windows based computer is using it at the moment

throw out some help please
thanks

---

### Post by Hightide on 2008-01-18
have you tried Kevdogs tutorial as a starter. Its excellent

[http://ubuntuforums.org/showthread.php?t=571188&highlight=kevdog](http://ubuntuforums.org/showthread.php?t=571188&highlight=kevdog)

:)

---

### Post by clsgis on 2008-01-18
I had pretty much the same problem on ubuntu-7.10 today.  ndiswrapper loads the driver and recognizes the device.  GUI network manager asks for the WEP key over and over, and sends several DHCPDISCOVERs, but never gets any DHCPOFFERs.

Then I got another root shell and typed

iwconfig wlan0 essid mylan
iwconfig wlan0 key d00bed00be
dhclient wlan0

and it got a DHCP offer and bound an address in less than a second.  Apparently the Network Manager GUI is having trouble feeding the WEP key to the driver.  Looks like a GUI bug to me.  Use the shell until they fix it.

---

### Post by kissson on 2008-01-19
solved
the rt2570 on xubuntu 7.10 really messed up
thx all

inspire from this
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

```

sudo su

aptitude install build-essential linux-headers-`uname -r`
aptitude clean
cd /usr/src
wget http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz
tar -zxvf rt2570-cvs-daily.tar.gz
cd ./rt2570-cvs-*/Module
make
strip -S rt2570.ko
make install

lshw -C network ## configuration: wireless=IEEE 802.11g
ifconfig wlan0 down ## original interface assigned with logical name wlan0 by xubuntu 7.10
modprobe -r rt73usb
modprobe -r rt2570
modprobe -r rt2500usb
modprobe -r rt2x00lib
echo 'blacklist rt73usb' >> /etc/modprobe.d/blacklist
##echo 'blacklist rt2570' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
rm -rf /lib/modules/`uname -r`/ubuntu/wireless/rt2x00/rt73usb
rm -rf /lib/modules/`uname -r`/ubuntu/wireless/rt2x00/rt2570
rm -rf /lib/modules/`uname -r`/ubuntu/wireless/rt2x00/rt2500usb
rm -rf /lib/modules/`uname -r`/ubuntu/wireless/rt2x00/rt2x00lib
## maybe more
depmod -a

modprobe -v rt2570 ## now it is from '/lib/modules/`uname -r`/extra/' but not '/lib/modules/`uname -r`/ubuntu/wireless/rt2x00/'

ifconfig -a ## now I got a new interface rausb0
lshw -C network ## wireless=IEEE 802.11g becomes wireless=RT2500USB WLAN

ifconfig rausb0 up
iwconfig rausb0 essid 'essid-name'
iwconfig rausb0 key s:mykey
dhclient rausb0

```

now the default network manager of xubuntu shows only wired network
but actually wireless is working

---

