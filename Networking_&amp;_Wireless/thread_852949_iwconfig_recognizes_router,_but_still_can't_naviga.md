---
title: "iwconfig recognizes router, but still can't navigate"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by drumanart on 2008-07-08
****
Hello everybody.
With my new installed HARDY version I have problems to connect to my router using the wireless card. 
Before I had UBUNTU GUTSY installed and the wireless connection worked fine.

Here is what I get from a terminal when I type **iwconfig:**

martin@martin-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"WLAN_86"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:01:38:65:26:6B   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have to reconfigure the wireless connection each time I restart the computer because of some reasen the configuration at /etc/network/interfaces is not recognized when the system reboots.

To get to the iwconfig output I type using a command line:

martin@martin-desktop:~$ sudo iwconfig wlan0 essid WLAN_86 mode Managed channel 03
martin@martin-desktop:~$ sudo iwconfig wlan0 key s:X000138649986 open



Any idear why I can't navigate?

---

