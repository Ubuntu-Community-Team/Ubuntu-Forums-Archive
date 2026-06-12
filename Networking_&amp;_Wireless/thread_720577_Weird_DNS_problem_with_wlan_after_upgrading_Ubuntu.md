---
title: "Weird DNS problem with wlan after upgrading Ubuntu"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by Cene on 2008-03-10
Hello,

Sorry for any possible typos to come, I hate typing on a laptop keyboard. ;)

So.. My main computer has been running Gentoo for the last year or so, but I still kept Ubuntu on my mother's laptop (mainly because compiling GNOME sucks like Britney Spears, and my mother likes GNOME). The laptop has been left without anything but the necessary updates so far after install of which I think was Ubuntu 6.10.

Yesterday I however decided to do a dist-upgrade with the upgrade tool that was delireved through the update manager. All went fine, except that after booting some problems with DNS occured. I've been using OpenDNS on my main box for as long as I can remember, but left the laptop with default settings and let my router decide what to do with it.

I get a connection up on device wlan0 and get the LAN IP from my router. I cannot however open any URLs or ping any network addressess anymore from the laptop, even after changing the nameserver entry in /etc/resolv.conf to use OpenDNS like my main box does. I can however ping any IP address, and surf the web by using direct IP addresses. This leaves me to think it is an issue with DNS.

Here's some info:

```
root@tarja:~# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"SpeedStream"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:A3:B9:EE:47   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@tarja:~# dmesg|grep bcm
[   31.040476] ndiswrapper: driver bcmwl5 (Broadcom,11/02/2005, 4.10.40.0) loaded
[   31.431945] wlan0: ethernet device 00:14:a5:f7:5b:de using NDIS driver: bcmwl5, version: 0x40a2800, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf

root@tarja:~# lsmod|grep ndis
ndiswrapper           179352  0 
usbcore               136088  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

root@tarja:~# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:14:A5:F7:5B:DE  
          inet addr:192.168.254.3  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fef7:5bde/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:846880 (827.0 KB)  TX bytes:83445 (81.4 KB)
          Interrupt:16 Memory:e8000000-e8004000 


root@tarja:~# ping google.com
ping: unknown host google.com

root@tarja:~# ping 64.233.167.99 #The IP address for google.com
PING 64.233.167.99 (64.233.167.99) 56(84) bytes of data.
64 bytes from 64.233.167.99: icmp_seq=2 ttl=249 time=202 ms
64 bytes from 64.233.167.99: icmp_seq=3 ttl=249 time=217 ms
64 bytes from 64.233.167.99: icmp_seq=4 ttl=249 time=220 ms
64 bytes from 64.233.167.99: icmp_seq=5 ttl=249 time=199 ms
64 bytes from 64.233.167.99: icmp_seq=6 ttl=249 time=220 ms

```

Edit: Okay, solved. I needed to tinker with /etc/dhcp3/dhclient.conf too to prevent dhclient from overwriting resolv.conf every time.. Why is changing DNS server so hard in Ubuntu, when it's said to be the easiest distro out there? In Gentoo it's enough just to edit resolv.conf. IMO that's way easier.

---

