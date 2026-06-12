---
title: "SSTP VPN 'connected' but no internet traffic, Ubuntu 14.04 LTS"
date: 2015-07-06
forum: Networking &amp; Wireless
---

### Post by Recipe Ferrum on 2015-07-06
Hello everybody!

I have been rambling around the forums a lot lately and have yet to find anything applicable or comprehensive on this subject. 

I need to connect to a virtual windows machine in sweden, and while I have managed to download and install the appropriate SSTP files and the VPN connection reads 'connected' and the little lock icon shows up, I have no internet. No forums, basic websites or anything, much less access to the specific machine I am trying to get to. 

One thread seemed promising, but ultimately fizzled out (and was about OpenVPN anyway). 

Any help would be appreciated, as I am more of a googler than a guru of any kind. 

Here are the basics: 

WITHOUT VPN

```
 
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0

PING ubuntuforums.com (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=55 time=125 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=55 time=125 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=55 time=126 ms

--- ubuntuforums.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 125.442/126.011/126.716/0.528 ms

```

WITH VPN

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
192.168.0.20    0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
195.238.77.197  192.168.0.1     255.255.255.255 UGH       0 0          0 wlan0

ping: unknown host ubuntuforums.com

```

Thanks so much!

---

### Post by ddesanti on 2015-07-06
Hi:
When you setup a VPN connections is to be have a secure connections between computers. It adds a layer of encryption to your connection. Have you setup the virtual machine in Sweden for VPN connectivity?, if so, are you able to ping it?.

---

### Post by Recipe Ferrum on 2015-07-06
Thanks for your prompt response!

I did not personally set up the virtual machine, but I have accessed it before from another PC (which I do not have access to). 

I tried pinging it with poor results, most of the time the ping was unsuccessful (100% packet loss) but there were a few that got through. 

I also got a 'destination host unreachable' errror

3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms
pipe 3

Also FYI, I am attempting to use Remmina Remote Desktop Protocol, if that is of any importance.

---

### Post by ddesanti on 2015-07-07
Could you please display how your VPN connection is setup.

---

### Post by Recipe Ferrum on 2015-07-10
general tab in configuration is all default settings

box checked at bottom of VPN tab to ignore certificate warnings, gateway, user name and password all correct and verified by recipient party

IPv4 settings all default (automatic vpn addresses only), DNS servers 8.8.8.8 and 8.8.4.4

Advanced settings under VPN tab have the following:

MSCHAP and MSCHAPv2 are the only checked boxes under Authentication

Allow BSD data compression, Allow deflate data compression and Use TCP header compression all checked under Security and Compression

Send PPP echo packets checked under Echo section

---

### Post by Recipe Ferrum on 2015-08-05
UPDATE: Have been unable to resolve, though the underlying problem of remote access was solved by installing TeamViewer.

---

