---
title: "Linksys WPC54G ver3.0 issue"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by nistaani on 2006-11-27
Hi there everyone. I'm totally new to Ubuntu - 3days and counting but loving it so far.

Have an issue getting wireless to work and its the last hurdle.

Running a dell inspiron 5100 with Ubuntu 6.10 & a Linksys WPC54G ver3.0 wireless card.

I've had a read through a few relevant posts here and proceeded with the ndiswrapper option. The driver installed fine (as far as I'm aware) Power light is on and the wireless link light is blinking intermittently. Installed KWiFiManager which detects the card but can't find the network. My xp box finds the network with no problem.

Below are all the things I know relevant to the issue. if anyone can help, i'd be very grateful.

iwconfig

lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.

eth1 IEEE 802.11g ESSIDff/any
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power:25 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


iwlist scan

lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

sit0 Interface doesn't support scanning.

eth1 No scan results


sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


auto wlan0
iface wlan0 inet dhcp

---

### Post by nistaani on 2006-11-30
Anyone got any ideas on this?

If I can't get any further with this I reckon I'm just going to pick up a Dlink DWL G650.  Seems like the most compatible PCIMCA card and they are quite cheap.

---

### Post by macmichael01 on 2006-12-05
I am having the same problem with the same card that you have. I hope someone has a solution.

---

### Post by Ksmith3637 on 2006-12-11
me to.. running toshiba satellite with the wpc54g card. does not see it..

---

