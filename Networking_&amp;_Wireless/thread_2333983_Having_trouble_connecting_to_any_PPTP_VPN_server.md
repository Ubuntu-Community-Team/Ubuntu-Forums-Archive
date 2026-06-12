---
title: "Having trouble connecting to any PPTP VPN server"
date: 2016-08-15
forum: Networking &amp; Wireless
---

### Post by skyler440 on 2016-08-15
I have a PPTP server setup on a remote router which I know works. I can connect and disconnect my MacOS computer all day without a problem. I am having so many issues trying to get a PPTP VPN connection working reliably in linux. I have spent a day yesterday trying all sorts of things, but just left with frustration. 

I tried this first on Raspbian with no luck, and now I'm trying to do the same on my Ubuntu 14.04 laptop, and getting the same error, so it must be something I am doing wrong. 

I am even having this problem if I use the graphical VPN setup, it may work the first time, but if I try to disconnect and reconnect, issues arise.

After installing pptp-linux, I used the pptpsetup command to configure the VPN settings:
```
sudo pptpsetup --create home --server home_IP_FQDN --username username --password PASSWORD_HERE  --start
```
The VPN connected up fine, and I obtained an IP address.
```
using channel 7

Using interface ppp0

Connect: ppp0 <--> /dev/pts/2

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xd2aeac5> <pcomp> <accomp>]

rcvd [LCP ConfReq id=0x1 <auth chap MD5> <mru 1450> <magic 0x3d07fa45>]

sent [LCP ConfAck id=0x1 <auth chap MD5> <mru 1450> <magic 0x3d07fa45>]

rcvd [LCP ConfRej id=0x1 <asyncmap 0x0> <pcomp> <accomp>]

sent [LCP ConfReq id=0x2 <magic 0xd2aeac5>]

rcvd [LCP ConfAck id=0x2 <magic 0xd2aeac5>]

sent [LCP EchoReq id=0x0 magic=0xd2aeac5]

rcvd [CHAP Challenge id=0x1 <5ff458fb69918371fddc1efba8f14669>, name = "Home"]

sent [CHAP Response id=0x1 <38408a477f44989c0924dec12b73c5f1>, name = "UserName"]

rcvd [LCP EchoRep id=0x0 magic=0x3d07fa45]

rcvd [CHAP Success id=0x1 "Welcome."]

CHAP authentication succeeded: Welcome.

CHAP authentication succeeded

sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]

rcvd [IPCP ConfReq id=0x1 <addr 192.168.88.6>]

sent [IPCP ConfAck id=0x1 <addr 192.168.88.6>]

rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]

sent [IPCP ConfReq id=0x2 <addr 0.0.0.0>]

rcvd [IPCP ConfNak id=0x2 <addr 192.168.89.7>]

sent [IPCP ConfReq id=0x3 <addr 192.168.89.7>]

rcvd [IPCP ConfAck id=0x3 <addr 192.168.89.7>]

local  IP address 192.168.89.7

remote IP address 192.168.88.6
```

Now to disconnect the VPN, I typed ```
sudo poff -a
```
When I want to reconenct the VPN, I type```
 sudo pon home updetach debug
``` and here is where I start having issues:
```
using channel 8

Using interface ppp0

Connect: ppp0 <--> /dev/pts/2

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc421318f> <pcomp> <accomp>]

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc421318f> <pcomp> <accomp>]

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc421318f> <pcomp> <accomp>]

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc421318f> <pcomp> <accomp>]

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc421318f> <pcomp> <accomp>]

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc421318f> <pcomp> <accomp>]

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc421318f> <pcomp> <accomp>]

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc421318f> <pcomp> <accomp>]

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc421318f> <pcomp> <accomp>]

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc421318f> <pcomp> <accomp>]

LCP: timeout sending Config-Requests

Connection terminated.

Modem hangup

Waiting for 1 child processes...

  script pptp xxxxx.duckdns.org --nolaunchpppd, pid 5426

sending SIGTERM to process 5426
```

On a reboot, ```
pon home updetach
``` will half of the time work, other times give me the error. However, if the command is followed by a poff -a, it will never work. Any suggestions?
I followed [these instructions]("https://devtidbits.com/2013/02/19/using-a-point-to-point-tunnelling-protocol-virtual-private-network-pptp-vpn-client-on-a-raspberry-pi/") for VPN setup. The issue is not unique to my mikrotik, I have received similar results on free PPTP VPN services. I will edit the post for any command output or configuration files needed.

---

### Post by TheFu on 2016-08-15
Besides knowing that PPTP shouldn't be used since 1999, I cannot help. 
[https://www.schneier.com/blog/archives/2012/08/breaking_micros.html](https://www.schneier.com/blog/archives/2012/08/breaking_micros.html)  There are free, easy-to-use tools to crack PPTP - "script kiddies" can use them.

This might not be the answer you seek, but switching to almost any other "VPN" would be the first suggestion.  L2TP, IPSec, OpenVPN ... would be where I started.  I use L2TP today, but have used openvpn and even ssh-tunneling previously.  ssh isn't really useful for normal users.  Avoid using DNS for any remote system resolution. Use IPs.

If running a VPN service and want to look at all the client machine traffic, then PPTP is useful.

---

### Post by QIII on 2016-08-15
Skyler440 --

Please use default font and color unless you need to draw attention to something specific.

Also, please use code tags for all commands you have executed as well as the response from the terminal.

To use code tags, you can:

1.  Click the # symbol above the text input box, place your cursor between the code tags and either type or C&P your text.

2.  Type or C&P your text, highlight it and then click the # symbol.

3.  Type [noparse]```
[/noparse] at the beginning of your text and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by perminder.mehta on 2017-01-20
I am having some problem in sending a PPTP request from Ubunto client in command line to the server. 
Can you please post how to send the request. I am new in PPTP behaviour

---

