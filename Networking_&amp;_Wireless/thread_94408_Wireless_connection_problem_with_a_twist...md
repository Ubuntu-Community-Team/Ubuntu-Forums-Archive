---
title: "Wireless connection problem with a twist.."
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by theissen2 on 2005-11-23
Hi....my first post...bear with me.  I have 5.04 installed on a separate partition...everything works fine until i try to connect to the 'net. In network settings i get  <interface wlanO is active> and <interface ethO is active>....but nothing when i open firefox. This is on a pc and windows xp works fine, of course, when i boot it up. Any ideas? There were some posts with wireless problems, but none that i saw where the wireless was working and still no connection.     thanx in advance....

---

### Post by aznboi on 2005-11-23
try using gtkwifi to find and connect to a wifi network, plus for my laptop i have it my eht0 disabled and it works fine. but u might not need to disable it.

---

### Post by cdubks88 on 2005-11-24
Does whatever AP/router that you're using run WEP/WPA?

If so, the wlan device may be up, but you may not be connected......I connect automatically when I boot the machine at home once the initial connection is made in a day, but whenever I go to school and use another router, I have to manually tell the system to connect to the new router and get me an IP.....

just thinking it sounds an awful lot like you're not ever getting an IP....what it the result when you do ifconfig?

C.

---

### Post by towsonu2003 on 2005-11-24
try disabling both then enabling wlan0 only. also, if using firewall, don't forget to configure it. In firestarter, you do that by Preferences>Network Settings>change first to your interface...

---

### Post by theissen2 on 2005-11-24
yea, tried all of the above.....re-installed the whole shmear......still no.
It's gotta be something simple i've missed........i'll keep trying....i'm a newbie to pc's, but i've done this many times on macs, so it's a definite learning experience.........thanx for the help........

---

### Post by theissen2 on 2005-11-24
ok...i'm blank about using gtkwifi......i type it into the terminal as root?.. nothing happens for me....

---

### Post by Lambert on 2005-11-24
post the output of the commands 

iwconfig

and 

ifconfig

---

### Post by theissen2 on 2005-11-24
Here is the output of iwconfig and ifconfig:

iwconfig
lo       no wireless extensions          etho    nowireless extensions

  wlan0   IEEE 802.11g/b+     ESSID : "corega"   nickname:acx100 vO.2.Opre8
  mode:Auto Frequency:2.412 GHZ   Access point:74:26:3A:39:90:81  Bitrate: 1Mb/s
  Tx-Power:15 dBm  Sensitivity =1/3  Retry min limit:7  RTS thr :off
  Power Management:off  Link Quality:0  Signal level:0 Noise level:0 Rx invalid nwid:0
  Rx invalid crypt:0 Rx invalid frag:0  Tx excessive retries:0 Invalid misc:0
  missed beacon:0  sit 0  no wireless extensions


ifconfig
lo  Link encap:local loopback  inet addr:127.0.0.1  Mask:255.0.0.0 inet 6 addr: ::1/128
  scope:Host  UP LOOPBACK RUNNING MTU:16436 Metric:1  Rx packets:4126 errors:0 dropped:0
  overruns:0 frame:0 Tx packets:4126 errors:0 dropped:0 overruns:0 carrier:0 collisions:0
  txqueuelen:0  RX bytes:324651(317.0KiB)  TX bytes:324651(317.0 KiB)
wlan0
  Link cap: Ethernet HWaddr: 00:12:OE:OD:A4:B5  inet6 addr:fe80::212:eff:fe0d:a4b5/64
  Scope: Link  UP BROADCAST RUNNING MULTICAST MTU:1500   Metric:1
  RX packets:0 errors:0 dropped:0 overruns:0 frame:0 TXpackets:17 errors:0 dropped:0
  overruns:0 carrier:0 collisions:0  txqueuelen:1000 RX bytes:0(0.0b)
  TX bytes:4482 (4.3 KiB)  Interrupt: 18 Base address:0 x 8000

  Hope someone there can make more sense out of this than i can...thanx again....

---

### Post by Lambert on 2005-11-25
Is your router set up for dhcp? If so try this command

sudo dhclient wlan0

As earlier post said, you're not getting an ip assigned to the deivce and ifconfig confirms this. 

1st thing I'd like you to try is reset your router and see if you get any results.

If no go then try this.


sudo ifconfig wlan0 down

sudo ifconfig wlan0 address 192.168.X.X up

where .x.x equals an ip address in the range of your router. ex...192.168.0.4

then try to ping your router

ping <router's_ip>

Try to ping [www.google.com](www.google.com)

ping [www.google.com](www.google.com)

Post back your results and if you know what you did to get this working. There seem to be quite a few posts lately about no ip assigned.

---

### Post by theissen2 on 2005-11-25
I tried the sudo wlan0 thing and i got  "host name lookup failure"

---

### Post by Lambert on 2005-11-25
try this

 sudo ifconfig wlan0 address 192.168.X.X netmask addr 255.255.255.0 up

You may want to double check your netmask. If you have an xp box connected to the network you can do this by

start>run type cmd [enter] then ipconfig /all

---

### Post by theissen2 on 2005-11-26
for the DCHP sudo dhclient wlan0   command i got:

sit0 unknown hardware address type776
listening on LPF/wlan0/00:12:0e:0d:a4:b5
sending        same
sending on socket fall back
5 bad IP checksums seen in 5 packets
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7, then 15, 13, 14, 8, 4
No DHCPOFFERS received
No working leases in persistent data base-sleeping

---

