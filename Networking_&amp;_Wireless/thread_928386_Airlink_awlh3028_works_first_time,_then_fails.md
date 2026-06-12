---
title: "Airlink awlh3028 works first time, then fails"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by keraunoscopia on 2008-09-23
I've just installed an Airlink awlh3028 WiFi card under Ubuntu 8.04.  I used the gui ndiswrapper tool to load the Win98 driver from the CD that came with the card, and everything worked fine.  I was able to connect to a public access point.

However, I rebooted, and I'm no longer able to connect to the access point. "lshw -C network shows the "ndiswrapper+net8185" driver is claiming the card, as it should.  The only clue I have is that when I "ifdown wlan0" then "ifup wlan0", DHCP seems to be failing:

[INDENT]Listening on LPF/wlan0/00:21:2f:00:0d:30
Sending on   LPF/wlan0/00:21:2f:00:0d:30
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/INDENT]

How can I get the card working again?  Any suggestions would be very much appreciated.

Jeff

---

### Post by willca on 2008-09-24
Did you tell Ubuntu to load ndiswrapper at startup?

If not...then...

sudo ndiswrapper -m
edit /etc/modules and add ndiswrapper at the end.

Also, before you try my suggestion about ndiswrapper. Check if your wifi nic actually sees any wireless networks around.

sudo iwlist wlan0 scan

---

### Post by keraunoscopia on 2008-09-26
Hi willca - thanks for your help.  lsmod shows that the ndiswrapper module is loaded.  "iwlist wlan0 scan" yields "No scan results".

The strange thing is that after I installed ndiswrapper, everything was working fine, and a scan showed several access points.  The problem only started when I rebooted.

---

