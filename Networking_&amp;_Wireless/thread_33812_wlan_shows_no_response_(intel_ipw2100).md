---
title: "wlan shows no response (intel ipw2100)"
date: 2005-05-12
forum: Networking &amp; Wireless
---

### Post by marty_buren on 2005-05-12
Hi!

I installed Ubuntu 5.04 two days ago on my laptop. Everything despite my wlan adapter worked fine - though it was correctly recognized.

First I tried to set it up using the network settings GUI in Gnome. As this did not work I  had a glance at the console. To me everything seems to be installed perfekt, but I can not get any connection nor an association to an access point.

A few details:

```
root@nereide:/ # ifconfig eth1
eth1      Protokoll:Ethernet  Hardware Adresse my_HW_Addr.
          inet6 Adresse: fe80::204:23ff:fe74:bb95/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Basisadresse:0xe000 Speicher:e0203000-e0203fff

root@nereide:/ # iwconfig eth1
eth1      unassociated  ESSID:"my_SSID"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power:off
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key: my_wep_key   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
(ESSID and WEP key are correct)
```

root@nereide:/ # iwlist eth1 scan
eth1      No scan results

```
(wondering why there isn't any delay when scanning...)
```

root@nereide:/ # dmesg | grep ipw
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.0.2
ipw2100: Copyright(c) 2003-2004 Intel Corporation
ipw2100: Detected Intel PRO/Wireless 2100 Network Connection

root@nereide:/ # uname -a
Linux nereide 2.6.10-5-686 #1 Tue Apr 5 12:27:02 UTC 2005 i686 GNU/Linux

```
I've no idea what to do from now on. Any help greatly appreciated!

thanks
Marty

---

### Post by luca_linux on 2005-05-12
Try to update the driver with the latest one available at [http://ipw2100.sourceforge.net](http://ipw2100.sourceforge.net).
You can follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623).
But note that you should install the driver and firmware for ipw2100 instead of ipw2200 and change any string referring to "ipw2200" into "ipw2100" obviously.

---

### Post by marty_buren on 2005-05-15
I followed the Howto and installed Firmware and Drivers. I also deactivated my WEP encryption and still can't get a connection. Doesn't Ubuntu support ipw2100 out of the box? Any more ideas?

---

### Post by luca_linux on 2005-05-15
Are you sure you don't have any other kind of security protection such as MAC Address Filtering or hidden ESSID?

---

### Post by marty_buren on 2005-05-16
[QUOTE=luca_linux]Are you sure you don't have any other kind of security protection such as MAC Address Filtering or hidden ESSID?[/QUOTE]

Got both, but works like a charm with my windows boxes. I also tried deactivating these protections. No change.

I also can't get into my university network, where other linux notebooks get the connection.

Any idea what I have to check if everything is installed correctly or what else I could try?

thanks a lot
Marty

---

### Post by grakhul on 2005-05-16
Doesn't seem like your wireless card has any power.  Are the lights on?  and are both lights flashing at the same time?
also go into /etc/network/interfaces and post everything in that file here.

Make sure that when you go into your router, that for the time being disable any type of security.  Take all security down and have your wireless cloud set up as an open system.  This will allow you to troubleshoot quickly.  Once your wireless router is set to it's default settings (which will allow anyone to jump into your network.)  Then configure your laptop to connect to the router.  Once you can connect to the router, go back and set up your security. (wep - keys - hide your cloud - etc...)

---

### Post by marty_buren on 2005-05-16
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid Wireless FH
wireless-key 5769[...]



auto eth0

```

This is my /etc/network/interfaces I have for use at university. Obviously I can't change any security configuration here. At Home I tried disabling all security measures with no success.

My wireless chip seems to be powered up. The LED is on and from time to time flashing. (behaves that way, when searching for available networks in windows. when connected it should stay on. Got only one LED for wireless)

Driver update looks good - now v1.1.0

```

marty@nereide:~$ sudo dmesg | grep ipw
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.0
ipw2100: Copyright(c) 2003-2004 Intel Corporation
ipw2100: Detected Intel PRO/Wireless 2100 Network Connection

```

---

