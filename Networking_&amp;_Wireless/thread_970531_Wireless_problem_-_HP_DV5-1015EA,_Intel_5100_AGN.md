---
title: "Wireless problem - HP DV5-1015EA, Intel 5100 AGN"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by breandan_anraoi on 2008-11-04
I have a wireless problem with the latest Ubuntu. I had been using Hardy briefly, then some of the pre-release versions of Intrepid on a HP-DV5 1015EA laptop. My wireless card didn't work with Hardy (hence moving to early intrepid versions as soon as possible), and initially it worked with Intrepid but then one of the upgrades did something funny and I kept having to run 
```

sudo modprobe iwl4965
```

to get the wireless to work.

Now, it has stopped working completely, although I can connect to wired ethernet network but it is extremely awkward.

I've tried everything I could find on any thread on the internet about intrepid wireless problems but nothing works. I have no network manager applet to even look at the status of networks etc.
```

breandan@eddie:~$ nm-applet

** (nm-applet:7460): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:7460): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

```
breandan@eddie:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:ba:09:fe
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:b9:d1:78
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=10.200.0.51 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:dd:be:36:18:11
       capabilities: ethernet physical

```


```

breandan@eddie:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"NUIGWiFi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:93:10:FD:E4   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-41 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

```
breandan@eddie:~$ sudo dhclient wlan0
[sudo] password for breandan: 
There is already a pid file /var/run/dhclient.pid with pid 7392
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:16:ea:ba:09:fe
Sending on   LPF/wlan0/00:16:ea:ba:09:fe
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```



```
 /etc/network/interfaces



# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

Any help would be much appreciated, I have reached the limit of my technical abilities!

---

### Post by breandan_anraoi on 2008-11-12
hopeful bump, still not working

---

### Post by sledgeas on 2008-11-18
I am getting the same errors as above, and nm-applet crashes

gentoo
networkmanager-0.7.0_rc2
networkmanager-vpnc-0.7.0

from an rbu overlay..

```
dbus-launch nm-applet 

** (nm-applet:16662): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:16662): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

---

### Post by smaring on 2008-11-30
I have an HP Pavilion dv7 running a 8.10 with this card in it.  Everything WAS fine for a very long time.  Then I rebooted, presumably after some updates, and now I get the same sort of thing.  Everything looks like it is fine, except I don't see ANY access points in my list anymore.

---

### Post by abdusamed on 2009-11-04
i got a 5100 AGN INTEL wireless card.. been tryin to install it for the past 1 and a half year.. FED UP LIKE HELLL!!! WHY IS IT SOO HARD TO INSTALL IT?? i booted windows 7 .. worked on first hit.. no porbz!

---

