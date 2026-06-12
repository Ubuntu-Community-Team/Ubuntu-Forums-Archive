---
title: "[SOLVED] Ath0?  Wifi0?  Neither works."
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by chikin03 on 2008-08-21
Me and Ubuntu Networking have a troubled past.  Most of all, I just want to completely uninstall and reinstall the network components so that it works as out of the box.  As it is, my attempts to fix it have been unsuccessful.

D-Link or Cisco (so it's not weird, but it is only a single card) wireless card in desktop.  There is onboard ethernet, unconnected. 
Latest stable Ubuntu, 2.6.24-19
Trying to connect to a broadcasted wireless SSID, WPA1-PSK TKIP
wpa_supplicant is installed
ndiswrapper, madwifi, and a restricted wireless driver were all installed back in better days.
Recently I uninstalled NetworkManager.  Configuring the interface with the Network Connection applet always returns "This interface does not exist"

I'm almost too discouraged to type this.  

Here are the results of some diagnostic commands as I try to follow "Manual Network Configuration without NetworkManager":

lshw -C network:
```

  *-network
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1b...
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.2.0 firmware=1.1-0 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:07:02.0
       logical name: wifi0
       version: 01
       serial: 00:15...
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
```

sudo more /etc/wpa_supplicant.conf:
```

network={
	ssid="myAP"
	scan_ssid=0
	proto=WPA
	key_mgmt=WPA-PSK
	psk="mypass"
	pairwise=TKIP
	group=TKIP
}
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

```

when I run sudo dhclient -r wifi0, a note says:

```

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
...
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0
Sending on LPF/wifi0/
Sending on  Socket/fallback

```

sudo wpa_supplicant -w -Dmadwifi -iwifi0 -c/etc/wpa_supplicant.conf fails like this:
```

ioctl[SIOCSIWPMKSA]: Invalid argument
ioctl[SIOCSIWMODE]: Invalid argument
ioctl[SIOCGIWRANGE]: Invalid argument
ioctl[IEEE80211_IOCTL_SETPARAM]: Invalid argument
ioctl[SIOCSIWAP]: Invalid argument

Could not configure driver to use managed mode
Failed to initialize driver interface

```
ifconfig -a:
```

ath0      Link encap:Ethernet  HWaddr 00:15:...  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5608 errors:1595 dropped:1595 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:464058 (453.1 KB)  TX bytes:677620 (661.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:1b:...  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f7fe0000-f8000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:694681 (678.3 KB)  TX bytes:694681 (678.3 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15...
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:698055 errors:0 dropped:0 overruns:0 frame:1498153
          TX packets:238694 errors:592 dropped:1595 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:101914142 (97.1 MB)  TX bytes:18432516 (17.5 MB)
          Interrupt:19 


```

In particular, I'm not sure if I'm supposed to use wifi0 or ath0 as my device.  Surely the fourth code box is key?  What are the wrong parameters I'm using and what should they really be?

If I replace wifi0 with ath0 above, the LPF/wifi0 becomes LPF/ath0/the_mac_address, and there are 3 lines:
```

DHCPRELEASE on ath0 to 192.158.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address
```

I change this file all the time, so hopefully it doesn't make a difference: /etc/network/interfaces
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface wifi0 inet dhcp
auto wifi0
```

In fact, I've put the full config in there and didn't have any luck. 

The router should be at 10.0.0.1

Can anyone see what is wrong?  Thanks for the help.

---

### Post by chikin03 on 2008-08-22
after endlessly running through wifi troubleshooting lists, manual configuration guides, and madwifi wikis, it's possible I'm slightly closer to fixing it.  

At this point, a major symptom seems to be that there is no one dot -> two dot animation in the network-manager-gnome applet, when switching AP's in roaming mode.  In addition, signal reception is exaggerated from ~20% into 98-100%.  Connection to the unsecured AP near me yields the same effects (no animation, nothing).  

Anyone recognize that?

---

### Post by cooke77 on 2008-08-22
Whe you uninstalled "Network Manager"...you also uninstalled the 'required Driver'.
That's why you're getting the 'this interface does not exist' error.
It may even help...IF you was to 'connect' everything.....through your LAN card. (Your LAN card just might 'recognize' your WiFi..for you.)

---

### Post by chikin03 on 2008-08-22
The interface was working for a long time with that error occurring.  It may be a symptom of the instability that I keep running against, but it's definitely not everything.  You're right that the driver was uninstalled.  I had run lshw before post 2, and saw there was no driver=.  Now it is driver=ath_pci (this is also when I relented and reinstalled net-man-gnome).  

I don't understand how to combine eth and ath, but I will keep it in mind as a keep looking for walkthroughs.

---

### Post by chikin03 on 2008-08-23
Solved.  Steps that may have made a difference:

* Downloaded newest madwifi, transferred via USB key.  Make, make install in sudo
* Transferred and reinstalled madwifi-tools, wireless-tools, network-manager-gnome
*** Cleared information in "Edit Wireless Networks" (right click the bars).  This deleted key information, prompting autoconfiguration.

---

