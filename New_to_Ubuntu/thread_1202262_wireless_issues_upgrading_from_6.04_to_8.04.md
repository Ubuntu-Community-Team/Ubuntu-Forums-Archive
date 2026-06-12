---
title: "wireless issues upgrading from 6.04 to 8.04"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by stednick on 2009-07-02
Hi

I recently upgraded to hardy heron and it was a flawless upgrade except for now there are two Network Connection icons in my toolbar (see attached image).

The wireless card is recognized and networks are detected:

zach@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

wlan0     IEEE 802.11b+  ESSID:"STAB13A09"  Nickname:"acx v0.3.36" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off 
          Link Quality=0/100  Signal level=50/100  Noise level=50/100 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

zach@ubuntu:~$ ifconfig 
wlan0     Link encap:Ethernet  HWaddr 00:40:05:b1:3a:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:11 Base address:0x1000 

zach@ubuntu:~$ sudo lshw -C network 
  *-network               
       description: Wireless interface 
       product: ACX 100 22Mbps Wireless Interface 
       vendor: Texas Instruments 
       physical id: 1 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:40:05:b1:3a:09 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+ 
zach@ubuntu:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 

wlan0     Scan completed : 
          Cell 01 - Address: 00:02:6F:34:40:D5 
                    ESSID:"instaconnect-viking-003" 
                    Mode:Master 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=59/100  Signal level=52/100  Noise level=3/100 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s 
          Cell 02 - Address: 00:1A:C4:9C:25:09 
                    ESSID:"2WIRE106" 
                    Mode:Master 
                    Frequency:2.422 GHz (Channel 3) 
                    Quality=0/100  Signal level=47/100  Noise level=50/100 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s

I have tried booting from the older kernel but the problem remained.  Any ideas or would it be better to do a fresh install at this point?

I am running a Dell Latitude Cpx H500GT with a D link 650 wireless card.

Thanks in advance

---

### Post by nandemonai on 2009-07-02
Are they both network manager applets? Or is one a network monitor applet?

---

### Post by stednick on 2009-07-02
They are both network manager applets.  One icon appears to be the old network manager from 6 while the other icon appears to be the newer manager from heron.  The older one allows manual configuration but then gives an error message that the interface does not exist.  The newer icon brings up the network settings menu, allows a network to be chosen, and then nothing happens.  It seems to me that there are some dependencies that were not transferred over when I upgraded but I cannot seem to resolve this by booting in the older kernel.

---

### Post by nandemonai on 2009-07-02
Can you please post the output of this from terminal:

```
apt-cache policy network-manager
```

---

### Post by stednick on 2009-07-02
zach@ubuntu:~$ apt-cache policy network-manager
network-manager:
Installed: 0.6.6-0ubuntu5.8.04.1
Candidate: 0.6.6-0ubuntu5.8.04.1
Version table:
***0.6.6-0ubuntu5.8.04.1 0
   500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
   100 /var/lib/dpkg/status
0.6.6-0ubuntu5 0
   500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages

---

### Post by nandemonai on 2009-07-03
Very odd. The only things I can really think to try is 

1. Update the system now you're on hardy (should be current anyway but the version in hardy-updates for network-manager is 0.6.6-0ubuntu5.8.04.2). 

2. Check to see if network manager is in startup applications / sessions (system -> preferences) more than once and remove one if so.

3..... ? Not too sure. I haven't run into this problem before myself on an upgrade. Seems kind of odd. Maybe someone else can chime in with some other suggestions.

---

### Post by superprash2003 on 2009-07-03
post output of **sudo dhclient wlan0**

---

### Post by stednick on 2009-07-03
zach@ubuntu:~$ sudo dhclient wlan0
[sudo] password for zach:
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp](http://www.isc.org/sw/dhcp)

Listening on LPF/wlan0/00:40:05:b1:3a:09
Sending on LPF/wlan0/00:40:05:b1:3a:09
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by superprash2003 on 2009-07-04
your wlan0 is not getting an ip address although it seems to be connected to a network.. you should try setting up a static ip via network manager.. here's a guide with screenshots [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by stednick on 2009-07-10
Thanks superprash,

I used some of that tutorial and rewrote part of /etc/network/interfaces and I got it to work.

---

