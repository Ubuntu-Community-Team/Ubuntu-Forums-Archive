---
title: "WPA2, DHCP - Stalls on DHCP request"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by cfusting on 2007-02-04
I've tried a number of methods to connect to my wireless AP including network-manager and various other GUI methods. I have no problem connecting under windows 2000, the SSID is picked up in scans and I simply type in the password to connect. Network manager failed due to the fact it did not offer WPA2 security in the options when creating a new connection. I've since reverted to manual connection but I am stalling during DHCP:

cfusting@duck:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:02:2d:93:0f:0f
Sending on   LPF/eth1/00:02:2d:93:0f:0f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15

Included is the usual data, any help is appreciated.

cfusting@duck:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:307  Rx invalid frag:18
          Tx excessive retries:3  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


cfusting@duck:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:03:82:D7:85  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::201:3ff:fe82:d785/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13898 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18856499 (17.9 MiB)  TX bytes:1391946 (1.3 MiB)
          Interrupt:11 Base address:0xac00 

eth1      Link encap:Ethernet  HWaddr 00:02:2D:93:0F:0F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1272 (1.2 KiB)  TX bytes:1272 (1.2 KiB)


cfusting@duck:~$ cat /etc/modprobe.d/ndiswrapper
cat: /etc/modprobe.d/ndiswrapper: No such file or directory

From wpa_supplicant.conf:

network={
	ssid="WWC_Private"
	scan_ssid=1
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP
	group=CCMP
	psk="26294c7344093fd05c88c9c045ff86ddfac270e2e96674b58033278fc91ba967"
}


From /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
#pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
#post-down killall -q wpa_supplicant


Any help is appreciated. You'll not that wlan0 is commented out, as it seems my wireless card is eth1. Hope you can make more sense of this than I did!
-Chris Fusting

---

### Post by jml on 2007-02-04
I'm not a wireless expert, but I have a few suggestions to try.  If possible, first try to connect by disabling encryption on the access point and the computer with the wireless card.  If you can connect that way, then you know that at least it is not a driver, or hardware problem.  Second point, you state that your access point uses WPA2 encryption.  I don't think network manager supports WPA2 encryption, (if I am wrong on this point, I'm sure someone here will correct me.)  Reviewing your WPA_SUPPLICANT config file:

From wpa_supplicant.conf:

network={
ssid="WWC_Private"
scan_ssid=1
proto=RSN
key_mgmt=[COLOR="Red"]WPA-PSK[/COLOR]
pairwise=CCMP
group=CCMP
psk="26294c7344093fd05c88c9c045ff86ddfac270e2e9667 4b58033278fc91ba967"
}

shows you are setting up a WPA-PSK encryption key not a WPA2 one.  This may be your problem, because the correct encryption key needs to be passed to your wireless access point before  DHCP will assign an IP address.  You might try switching your wireless access point to WPA-PSK encryption instead of WPA2.  If these suggestions don't help, try searching this forum for the terms WPA2.  You might find some helpful ideas there.  Good luck.

Joe

---

### Post by cfusting on 2007-02-04
The AP is actually my school's router, so I can't fiddle with it. However, I have reviewed the sample wpa_supplicant.conf file. I came up with a script that I thought would work, but gives me the same error.

network={
	ssid="WWC_Private"
	scan_ssid=1
	proto=RSN
	key_mgmt=WPA-EAP
	pairwise=CCMP
	group=CCMP
	password="wwcwireless"
}

I should note I am using an Orinoco gold card. I figure its ok because it connects under other OS' and seems to be alive according iwconfig.
-Chris

---

### Post by jml on 2007-02-04
Your card may be the problem.  If my memory is correct, the Orinoco Gold card is an 802.11 b card.  Its a very good card and very Linux friendly, but it does not support WPA encryption.  This is something that you cannot fix with different configurations.  Its a hardware/firmware issue.  

Your only choice is to get a different card.  There are several cards that are both Linux friendly, and support WPA encryption.  I'm not sure how many support WPA2 encryption.  So if you must use WPA2 to connect at school, make sure the cards I recommend support WPA2.  The two cards I personally use to connect to WPA encrypted access points are the NetGear WG511T and the Cisco Aironet 802.11 a/b/g cards.  These are cards that use the Atheros chip set which is very Linux friendly. 

 I would recommend that you not use the standard network utility supplied by Ubuntu (System--->Administration--->Networking)  I would download and install two applications.  network-manager and network-manager-gnome.  Unlike the default utility, network-manager supports WPA encryption, and is much better at detecting and switching between different wireless access points.  Hope this helps.

Joe

---

### Post by cfusting on 2007-02-04
Thanks for the info. It does seem odd that my card can connect under windows 2000 and not *nix, if its a hardware issue anyway.

---

### Post by jml on 2007-02-04
If your card can connect at school with Windows 2000, then it is not a hardware/firmware issue with the card.  It may be an issue with Ubuntu not supporting WPA2 encryption.  Hopefully someone else may have a solution for you.  Good luck.

Joe

---

### Post by zava on 2007-02-07
I have similar problem, except i'm using only WPA TKIP. I'm using Ubuntu 6.10,orinoco gold card and my router is SMC7804BRA. From the router, I see the router sending DHCPOFFER so the problem is not in encryption. (if I misspell password the router don't send DHCPOFFER)

I've tried with WEP and WPA without succeed. Static IP settings don't help. I also replaced orinoco_cs driver (which comes with Ubuntu installation packet) with new wlangs49_h1_cs driver from this forum - no help. 

I also tried different settings in AP.
Network adapter works fine in Windows.

```

xxxxx@xxxxx-laptop:~$ sudo ifup eth2
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth2/00:02:2d:0d:c0:45
Sending on   LPF/eth2/00:02:2d:0d:c0:45
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

xxxxx@xxxxx-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:25052  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:"Jwlan"  Nickname:"Linux"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:04:E2:AC:55:14   
          Bit Rate=11.5343 Mb/s   Tx-Power=16 dBm   Sensitivity:1/3  
          RTS thr:off   
          Power Management:off
          Link Quality=62/92  Signal level=-40 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:51
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

xxxxx@xxxxx-laptop:~$

```

Any ideas?

- zava

---

### Post by Brunellus on 2007-02-09
I can confirm this issue with my setup.  dhclient seems to connect only by luck in feisty.  Not at the affected machine now, but will edit this post/post again when I have detailed output.  Interface is known to work under orinoco_cs, but hostap and prism2 are loaded by default.  Under Edgy, hermes was loaded by default as well as orinoco and hostap.


  Have blacklisted prism2_cs and hostap_cs with no appreciable effect.

---

