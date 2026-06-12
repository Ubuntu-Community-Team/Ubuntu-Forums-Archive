---
title: "wireless settings"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by rahimamiah on 2009-03-08
I have installed factory wireless drivers but still don't have no wireless connection.

I have used  sudo apt-get install wpagui to install wpagui and also used sudo gedit /etc/wpa_supplicant.conf to find and enter the password.

When I used  wpa_gui
Failed to open control connection to wpa_supplicant.
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect

A box came up said "could not get status from wpa_supplicant and all the spaces under surrent status for adopters, network , ssid , ip address are blanked out.

Do you know what have I done wrong ?

---

### Post by redbob on 2009-03-08
Usually, at first install, wireless device is power down.
Type the following command:
> lshw -C network
Then
> iwconfig

---

### Post by rahimamiah on 2009-03-08
Please read the following

lshw -c network
*-network:0
description: Ethernet interface
product: BCM4401 100Base-T
vendor: Broadcom Corporation
physical id: 5
bus info: pci@0000:02:05.0
logical name: eth0
version: 01
serial: 00:00:f0:71:c3:41
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.100 latency=64 module=ssb multicast=yes
*-network:1
description: Wireless interface
product: PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: Intel Corporation
physical id: 7
bus info: pci@0000:02:07.0
logical name: eth1
version: 05
serial: 00:0e:35:1e:de:f8
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 52:1c:72:c5:8f:19
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 unassociated ESSIDff/any
Mode:Managed Channel=0 Access Point: Not-Associated
Bit Rate:0 kb/s Tx-Power=20 dBm Sensitivity=8/0
Retry limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0



What do i do next ?

---

### Post by redbob on 2009-03-10
Well, I have a notebook, my wireless card is Broadcom B4311, as you have... the first thing you must do is power on your wireless device. Type this:
> sudo iwconfig eth1 power on
There's other thing you must do:
- Enable Broadcom Device by "System > Admin > Hardware Drivers". If it's already enabled, let's go to next step;
- I put a script im my rc.local, so everytime I turn on my notebook, it power on wireless device. Look:
> modeprobe -r b43 b44 ssb wl
modprobe ieee80211_crypt_tkip
modprobe wl
/etc/init.d/networking restart
You may save this commands into a batch file (extension *.sh) and insert it into /etc/rc.local

---

