---
title: "Going quitely mad .."
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by johnbl on 2008-02-21
My laptop running &# works great bar a very slow start up process..
But the bane of my life is wifi, I've a Netgear wgr614 v7 setup - and that appears to work fine. In that my PHONE [ Nokia N95 ] can hook up to it, browse the web et al.

But the laptop ... hair pulling commences!

iwconfig get's this;

eth1      IEEE 802.11g  ESSID:"interserve" 
Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:5F:63:26 
Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
Retry limit:7   RTS thr:off   Fragment thr:off
Power Management:off
Link Quality=78/100  Signal level=-33 dBm  Noise level=-83 dBm
Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:36

I seem to have followed every howto I can find, latest ipw driver loaded,  but net result is zip.. Has worked, once, when first set up. I recabled - moved the access point to the recommended ' high point in the room ' et al - and as the phone atests, it works upstream from the access point to the internet but simply not down to the laptop.

Does any of the above make sense to anyone out there who could shine some light on just what I'm doing wrong.

Thanks

John

---

### Post by Vadi on 2008-02-21
Try using WICD ([click]("http://wicd.sourceforge.net/")). Sometimes it's better at connecting than the default tool.

---

### Post by HermanAB on 2008-02-21
So what is your problem?  Is the problem that the WiFi adaptor won't connect or that your system can't get a valid IP address? Or is the connection dropping...

You got to give some more info.

---

### Post by wieman01 on 2008-02-22
Please post:
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces

---

### Post by johnbl on 2008-02-22
john@interserve3:~$ sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:2F:5F:63:26
                    ESSID:"interserve"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-37 dBm  

john@interserve3:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:b8:fd:3e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:28:4b:2d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : WEP-40 TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : WEP-40 TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 320ms ago

john@interserve3:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

iface eth1 inet dhcp
wireless-essid interserve


auto eth0

---

### Post by johnbl on 2008-02-22
> **Vadi said:**
> Try using WICD ([click]("http://wicd.sourceforge.net/")). Sometimes it's better at connecting than the default tool.

Valdi,
Thank you for that suggestion. Have laoded Wicd and it ' sees ' the Wifi point OK,[ has correct id MAC of the access point ]  see's no other - I know there are some but whatever. Connects wired no problem. Wifi - NADA, still!

It seems that if it can see the damb thing, it can't be out of range - it's maybe 4M laterally and 2 vertically away - Signal strength on the various reports seems ok.

Any ideas?

Thanks

John

---

### Post by Vadi on 2008-02-22
Could you please post on their forums: [http://wicd.sourceforge.net/phpbb](http://wicd.sourceforge.net/phpbb)

The people who make it are experts at wireless and will help you figure out what's wrong. I don't know much myself, just a user like you heh.

---

### Post by wieman01 on 2008-02-22
John, 

This might be it. Please do the following:
> sudo gedit /etc/network/interfaces
Then edit it and make it read:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
Then restart the PC and see if you can connect. If not, please try:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
This relates to a pretty common bug. You NIC "ipw2200" works great with Ubuntu (usually). There is no need for WICD.

---

