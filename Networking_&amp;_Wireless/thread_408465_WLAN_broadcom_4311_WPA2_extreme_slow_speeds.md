---
title: "WLAN broadcom 4311 WPA2 extreme slow speeds"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by GoBieN on 2007-04-13
hello folks,

with help from the wiki i got my wireless at home to work on feisty.

Setup automatically installed my wireless builtin adapter (pavilion dv6017ea), it recognized it as a broadcom 4311 but i did get a warning about missing firmware. Wich is normal i read on the wiki. with the script provided by the fwcutter package i was able to automatically download necessary firmware and i saw the led on my laptop go on. I'm using wpa2 encryption on my network and after editing the wpa_supplicant.conf file as described in the wiki i was able to connect to my wireless network.

However my connection is extremely slow, i'll give you an example:

```
stan@laptop-ubuntu:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=47.2 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=2.61 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=5.23 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=53.7 ms
64 bytes from 192.168.1.254: icmp_seq=5 ttl=64 time=96.4 ms
64 bytes from 192.168.1.254: icmp_seq=6 ttl=64 time=144 ms
64 bytes from 192.168.1.254: icmp_seq=7 ttl=64 time=41.3 ms
64 bytes from 192.168.1.254: icmp_seq=8 ttl=64 time=110 ms

```
Downloading something from the internet results in speeds like 5kb/sec and sometimes up to 11 kb/sec. truly not normal. I have a 54Mbit router and a 10Mbits internet connection. Under windows i get normal results (54mbit and fast speeds) on the same files and at the same location.

iwconfig says my rate is 11mb/sec wich is slow, but its set at auto rate, and if i set the at rate 54M i lose network connection.

Please help me get normal speeds ;)

Here some info:
```
stan@laptop-ubuntu:~$ uname -a
Linux laptop-ubuntu 2.6.20-14-generic #2 SMP Mon Apr 2 16:32:46 UTC 2007 x86_64 GNU/Linux

```
```
stan@laptop-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"dd-wrt"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:40:10:10:00:03   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=71/100  Signal level=-59 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

stan@laptop-ubuntu:~$ 

```
```
stan@laptop-ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid dd-wrt
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf
stan@laptop-ubuntu:~$ 
```
```
stan@laptop-ubuntu:~$ sudo cat /etc/wpa_supplicant.conf 
Password:
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
network={
    ssid="dd-wrt"
    scan_ssid=1
    psk="sxxxxxxxxxg"
}
stan@laptop-ubuntu:~$
```
```
stan@laptop-ubuntu:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
stan@laptop-ubuntu:~$ 

``````
stan@laptop-ubuntu:~$ lsmod | grep ieee8
ieee80211_crypt_tkip    13184  2 
ieee80211_crypt_ccmp     9472  1 
ieee80211softmac       34688  1 bcm43xx
ieee80211              37064  2 bcm43xx,ieee80211softmac
ieee80211_crypt         8064  3 ieee80211_crypt_tkip,ieee80211_crypt_ccmp,ieee80211
stan@laptop-ubuntu:~$ 

```
If any more info is needed i'm happy to look it up ...

thanks

---

### Post by bdogg64 on 2007-04-13
Have you tried using ndiswrapper? It may give you better performance. I have the same broadcomm 4311 card and it works great

Here is the link to the guide

[http://www.ubuntuforums.org/showthread.php?t=346083](http://www.ubuntuforums.org/showthread.php?t=346083)

---

### Post by GoBieN on 2007-04-13
As another prove of the slow speeds, while i'm downloading some debs, here is my ping results (a ping to my router ) !!!
> stan@laptop-ubuntu:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=6174 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=5698 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=5909 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=6267 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=5311 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=5605 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=6009 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=5403 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=7006 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=6380 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=5471 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=5676 ms

--- 192.168.1.1 ping statistics ---
19 packets transmitted, 12 received, 36% packet loss, time 18056ms
rtt min/avg/max/mdev = 5311.880/5909.615/7006.140/467.986 ms, pipe 7
stan@laptop-ubuntu:~$ 


---

### Post by GoBieN on 2007-04-15
> **bdogg64 said:**
> Have you tried using ndiswrapper? It may give you better performance. I have the same broadcomm 4311 card and it works great

Here is the link to the guide

[http://www.ubuntuforums.org/showthread.php?t=346083](http://www.ubuntuforums.org/showthread.php?t=346083)

Thanks, with ndiswrapper 1.41 it worked for me. great speeds to.

---

