---
title: "WLAN Issue:  Wepkey 64bit Vs 128bit"
date: 2005-05-20
forum: Networking &amp; Wireless
---

### Post by ichoudhury on 2005-05-20
Hi,
     I installed Hoary Hedgehog 5.04 to a desktop (Gateway) and a Laptop IBM T30.  Desktop has a Cisco Aironet 350 PCI adapter installed and Laptop (Intel High Rate Wireless LAN Mini-PCI...). 

Both Ubuntu installation recognizes the cards and works fine against this AP (Cisco) configured with 64bit key.   But not to another AP which uses 128bit key.  I have to be able to connect to the AP using 128bit key (vital for webfarm administration).   

In either case, I am dual booting Windows 2003 and XP (laptop), I connect to the AP (128bit) just fine, but not under Linux.

Again...
Ubuntu automatically recognized both card and works fine when I am using the 64bit AP....but not when using 128bit.  Obciously the card has no issue (WLAN status also shows 100% quality).  But in Windows 2003 or Windows XP, I can connect to the 128bit AP.   

Any ideas?

---

### Post by momo66 on 2005-05-20
try using iwconfig to setup your wep key.  

do a man iwconfig to get more details.

```
iwconfig eth2 essid <whatever> enc [1] BEAD5BA5EDF00DF00DFEEDF00D restricted
```

** Note F<zero><zero>D

you can also use key instead of enc. (man iwconfig)

I am not sure where Ubuntu stores the keys.

you can try defining the KEY in /etc/sysconfig/network-scripts/ifcfg-eth2

add these 2 entries

ESSID=your essid
KEYn=your 26 hex character key.

---

### Post by ichoudhury on 2005-05-23
Thank you for the suggestion... in fact iwconfig is all I use now as the GUI program is flaky and slow :roll: 

In fact, right now I am posting this msg from that box in question but on the other network.  From this network, I cannot do apt-get type of activity and very restricted browsing over a proxy.  

Only differece between this network (the one I am in) Vs the other one is 128bit encryption is enabled in the other AP (which works fine under Windows 2003 (dual boot).

---

### Post by ichoudhury on 2005-05-23
iwconfig output...  (when pointing to the 128bit wepkey enabled AP

eth0      IEEE 802.11-DS  ESSID:"HERCULES"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0F:17:8C:6E:B0
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:open
          Power Management:off
          Link Quality=151/160  Signal level=-52 dBm  Noise level=-97 dBm
          Rx invalid nwid:95  Rx invalid crypt:6750  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:12703043   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"HERCULES"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0R:3E:8B:71:B1
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:open
          Power Management:off
          Link Quality=151/160  Signal level=-52 dBm  Noise level=-97 dBm
          Rx invalid nwid:95  Rx invalid crypt:6750  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:12703043   Missed beacon:0


Here's what I get when I try to grab an IP

# dhclient3 eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
wifi0: unknown hardware address type 801
sit0: unknown hardware address type 776
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:0e:3e:a8:1p:a7
Sending on   LPF/eth0/00:0e:3e:a8:1p:a7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by ichoudhury on 2005-06-02
momo, 
      I started getting the IP by doing what you've suggested...


iwconfig eth0 essid name enc  <key>   (actually I did not include restricted).

but loose connection everytime I reboot.  So probably have it connect that way on startup.

---

