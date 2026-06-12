---
title: "[SOLVED] Gutsy Intel 3945ABG timeout problem; detected/pinging just fine. Net manager"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by Durito on 2007-11-06
I'm running Gutsy Gibbon (which, being my first Ubuntu install on this machine, is otherwise fantastic) on an Thinkpad T60, and having internet connection problems. The network manager shows available unencrypted access points, and seems to connect just fine. Being used to managing wireless from the command line, this was pleasant. However--almost no internet connectivity. The connection times out when connecting to websites via browser, although occasionally a live bookmark will load. However I can ping just fine, as evidenced by:

```
PING googlemail.l.google.com (209.85.139.83) 56(84) bytes of data.
64 bytes from www.gmail.com (209.85.139.83): icmp_seq=1 ttl=246 time=19.7 ms
64 bytes from www.gmail.com (209.85.139.83): icmp_seq=2 ttl=246 time=21.0 ms
64 bytes from www.gmail.com (209.85.139.83): icmp_seq=3 ttl=246 time=18.3 ms
64 bytes from www.gmail.com (209.85.139.83): icmp_seq=4 ttl=246 time=20.7 ms
64 bytes from www.gmail.com (209.85.139.83): icmp_seq=5 ttl=246 time=18.2 ms

--- googlemail.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 18.287/19.620/21.033/1.146 ms

```Traceroute, however, gets about halfway to google and then returns a "no reply" response. Any ideas? I recall at some point seeing a closed Launchpad bug report that described the problem and suggested that the problem might lie in the Network Manager. The access point seems to be working fine, as I'm using it now under Windows. Outputs are as follows:

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:19:D2:07:D3:D1  
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe07:d3d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:789 errors:7 dropped:709 overruns:0 frame:0
          TX packets:779 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:471899 (460.8 KB)  TX bytes:358594 (350.1 KB)
          Interrupt:22 Base address:0x4000 Memory:edf00000-edf00fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1728 (1.6 KB)  TX bytes:1728 (1.6 KB)


```iwconfig:

```
eth0      IEEE 802.11g  ESSID:"Top Pot Doughnuts"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:05:40:4C   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=90/100  Signal level=-42 dBm  Noise level=-43 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:702   Missed beacon:0


```lspci:

```
 yadayadayada Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

```lshw:

```
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:d2:07:d3:d1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.125 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g

```Thanks!

---

### Post by Durito on 2007-11-06
Update question: How would I go about disabling the network manager?

---

### Post by Durito on 2007-11-06
So, acting on the suspicion that Network Manager was the culprit, I ran ```
sudo apt-get remove network-manager
```
and then appended the following to /etc/network/interfaces file 
```
auto eth0
iface eth0 inet dhcp
``` 

which was presumably there before and removed when I removed network-manager. Now I'm managing my wireless from the command line, and everything's working just dandy. So, maybe I'll try wicd, as some of this machine's other users aren't as comfortable with the terminal. Thoughts?

---

