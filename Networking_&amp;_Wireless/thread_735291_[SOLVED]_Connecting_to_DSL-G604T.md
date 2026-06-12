---
title: "[SOLVED] Connecting to DSL-G604T"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by davey boy on 2008-03-25
Hi there, i'm having a few troubles getting up and running with wireless internet, i'm trying to connect to a Dlink DSL-G604T router using a Dlink DWL-G122 B1 USB adapter (based on a rt2500 chipset) using WEP. This setup autodetects fine on Vista, and when plugged in using a cable in Ubuntu connects to the admin page of the router with no problems.

On using a fresh install of Ubuntu, Network manager detects the router as "G604T_WIRELESS", but trying to connect to this with my hexidecimal WEP key, the manager tries for a while then asks again for the WEP key. Turning WEP off on the router and again trying network manager tries and fails, and likewise setting up with manual settings.

I then tried connecting manually using a terminal window and entering the following:

```
sudo ifconfig wlan0 down 
sudo dhclient -r wlan0 
sudo ifconfig wlan0 up 
sudo iwconfig wlan0 essid "G604T_WIRELESS" 
sudo iwconfig wlan0 key xxxxxxxxxx 
sudo iwconfig wlan0 mode Managed 
sudo dhclient wlan0
```

which returns this:

```
There is already a pid file /var/run/dhclient.pid with pid 134519120 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:13:46:6b:d1:ac 
Sending on   LPF/wlan0/00:13:46:6b:d1:ac 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 
No DHCPOFFERS received. 
No working leases in persistent database – sleeping.
```

iwconfig wlan0 returns:

```
wlan0     IEEE 802.11g  ESSID:"G604T_WIRELESS"   
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:9B:A8:96    
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B    
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ifconfig wlan0 returns:

```
wlan0     Link encap:Ethernet  HWaddr 00:13:46:6B:D1:AC   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

and finally, iwlist wlan0 scan returns:

```
wlan0     No scan results
```

I've also tried NDISWrapper using the Dlink Windows driver, disabling ipv6 and trying all of the above on a fresh install to no avail.

Any tips as to where I'm going wrong would be greatly appreciated, if i'm missing any info, give me a shout and i'll post it.

---

### Post by davey boy on 2008-03-25
Reading through some more posts, I thought this might be useful, my /etc/network/interfaces file reads:

```
auto lo
iface lo inet loopback
```

---

### Post by davey boy on 2008-03-26
Cracked it, I installed a new driver suing NDISWrapper from [ftp://ftp.dlink.co.uk/wireless/dwl-g122_rev_Bx/dwl-g122_Bx_Drivers.zip]("ftp://ftp.dlink.co.uk/wireless/dwl-g122_rev_Bx/dwl-g122_Bx_Drivers.zip"), turned off WEP and i'm writing this in Ubuntu! Now, i've just got to figure out how to get WEP back on!

---

