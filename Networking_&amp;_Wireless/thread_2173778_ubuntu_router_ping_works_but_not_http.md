---
title: "ubuntu router: ping works but not http"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by kwiadnyana on 2013-09-11
Hi,

I wonder if anyone can give me some pointers to my current problem:

I have setup a router using Ubuntu 12.04 (on an HP mini netbook), pretty much following the tutorial as shown in:
[http://rbgeek.wordpress.com/2012/05/14/ubuntu-as-a-firewallgateway-router/](http://rbgeek.wordpress.com/2012/05/14/ubuntu-as-a-firewallgateway-router/)

Now in the LAN, my computer (win7) is unable to access any website, except the website on the router itself (webmin page). I can do "ping yahoo.com" successfully, but if I try to open an outside page, it would just wait and wait and wait. I did try doing an FTP to an external site, I could login, but when I do a "dir" command, it came back with data packet error. FYI, DHCP seems to have handed out addresses correctly.

I tried doing a tcpdump and (being pretty new to this stuff) my guess is that the "ping" packet is a different type of packet than the HTTP and it is getting through without any hindrance.

Telnet at port 80 seems to be another thing to try but I am not sure why telnet kinda barked at me when I tried it.

Any suggestions as to how to debug this problem?

Thanks
Ketut

---

### Post by The Cog on 2013-09-11
Can you run this tcpdump command and then try both a ping and a web browse to the same web site from one of the internal PCs please. That should give us a good idea what's happening.
```
sudo tcpdump -npi any
```
If the browser just hangs, a wait of around 5 seconds before stopping tcpdump should do OK. Post the tcpdump output here. 

Note that the tcpdump output will contain your public IP address. You may want to do a search and replace on it to avoid making it public knowledge before posting the trace. I would suggest replacing it with "1.2.3.4" so that the trace still looks sensible.

---

### Post by kwiadnyana on 2013-09-13
OK finally I am able to be back to my post. Thanks for your reply, Cog. I must add that my eth3 is not a regular 'Ethernet' connection. It is actually a cable modem, a CISCO 2100 Cable Modem, that is connected **via USB**. So, maybe that makes a whole world of difference.

Anyway, 'tcpdump -npi any' is cluttered with all kinds of ubuntu one request (with BOOTP packets?), so I did only on eth1 (LAN) whose address is 192.168.1.1. The result is as follows (my dns is google, 8.8.8.8):

Ping yahoo.com:
```


22:35:04.995257 IP 192.168.1.56.55632 > 8.8.8.8.53: 56313+ A? yahoo.com. (27)
22:35:05.038649 IP 8.8.8.8.53 > 192.168.1.56.55632: 56313 3/0/0 A 98.139.183.24, A 206.190.36.45, A 98.138.253.109 (75)
22:35:05.041261 IP 192.168.1.56 > 98.139.183.24: ICMP echo request, id 13411, seq 1, length 64
22:35:05.382642 IP 98.139.183.24 > 192.168.1.56: ICMP echo reply, id 13411, seq 1, length 64
22:35:05.385116 IP 192.168.1.56.4715 > 8.8.8.8.53: 20198+ PTR? 24.183.139.98.in-addr.arpa. (44)
22:35:05.421660 IP 8.8.8.8.53 > 192.168.1.56.4715: 20198 1/0/0 PTR ir2.fp.vip.bf1.yahoo.com. (82)
22:35:06.043118 IP 192.168.1.56 > 98.139.183.24: ICMP echo request, id 13411, seq 2, length 64
22:35:06.320655 IP6 fe80::21c:bfff:fe88:7699.5353 > ff02::fb.5353: 0 PTR (QM)? _sane-port._tcp.local. (39)
22:35:06.379631 IP 98.139.183.24 > 192.168.1.56: ICMP echo reply, id 13411, seq 2, length 64
22:35:06.382123 IP 192.168.1.56.46710 > 8.8.8.8.53: 57385+ PTR? 24.183.139.98.in-addr.arpa. (44)
22:35:06.422658 IP 8.8.8.8.53 > 192.168.1.56.46710: 57385 1/0/0 PTR ir2.fp.vip.bf1.yahoo.com. (82)
22:35:07.045041 IP 192.168.1.56 > 98.139.183.24: ICMP echo request, id 13411, seq 3, length 64
22:35:07.392617 IP 98.139.183.24 > 192.168.1.56: ICMP echo reply, id 13411, seq 3, length 64
22:35:07.395058 IP 192.168.1.56.45164 > 8.8.8.8.53: 61668+ PTR? 24.183.139.98.in-addr.arpa. (44)
22:35:07.439657 IP 8.8.8.8.53 > 192.168.1.56.45164: 61668 1/0/0 PTR ir2.fp.vip.bf1.yahoo.com. (82)
22:35:08.047057 IP 192.168.1.56 > 98.139.183.24: ICMP echo request, id 13411, seq 4, length 64
22:35:08.468620 IP 98.139.183.24 > 192.168.1.56: ICMP echo reply, id 13411, seq 4, length 64
22:35:08.470982 IP 192.168.1.56.42216 > 8.8.8.8.53: 59188+ PTR? 24.183.139.98.in-addr.arpa. (44)
22:35:08.503666 IP 8.8.8.8.53 > 192.168.1.56.42216: 59188 1/0/0 PTR ir2.fp.vip.bf1.yahoo.com. (82)
22:35:09.048992 IP 192.168.1.56 > 98.139.183.24: ICMP echo request, id 13411, seq 5, length 64
22:35:09.379616 IP 98.139.183.24 > 192.168.1.56: ICMP echo reply, id 13411, seq 5, length 64
22:35:09.382238 IP 192.168.1.56.34221 > 8.8.8.8.53: 14912+ PTR? 24.183.139.98.in-addr.arpa. (44)
22:35:09.417647 IP 8.8.8.8.53 > 192.168.1.56.34221: 14912 1/0/0 PTR ir2.fp.vip.bf1.yahoo.com. (82)
22:35:10.041147 ARP, Request who-has 192.168.1.56 tell 192.168.1.1, length 28
22:35:10.043087 ARP, Reply 192.168.1.56 is-at 00:1c:bf:88:76:99, length 46
22:35:10.051238 IP 192.168.1.56 > 98.139.183.24: ICMP echo request, id 13411, seq 6, length 64
22:35:10.427597 IP 98.139.183.24 > 192.168.1.56: ICMP echo reply, id 13411, seq 6, length 64
22:35:10.429970 IP 192.168.1.56.33283 > 8.8.8.8.53: 56390+ PTR? 24.183.139.98.in-addr.arpa. (44)
22:35:10.481607 IP 8.8.8.8.53 > 192.168.1.56.33283: 56390 1/0/0 PTR ir2.fp.vip.bf1.yahoo.com. (82)
22:35:11.052959 IP 192.168.1.56 > 98.139.183.24: ICMP echo request, id 13411, seq 7, length 64
22:35:11.373619 IP 98.139.183.24 > 192.168.1.56: ICMP echo reply, id 13411, seq 7, length 64
22:35:11.375946 IP 192.168.1.56.44447 > 8.8.8.8.53: 46841+ PTR? 24.183.139.98.in-addr.arpa. (44)
22:35:11.411722 IP 8.8.8.8.53 > 192.168.1.56.44447: 46841 1/0/0 PTR ir2.fp.vip.bf1.yahoo.com. (82)
22:35:12.055119 IP 192.168.1.56 > 98.139.183.24: ICMP echo request, id 13411, seq 8, length 64
22:35:12.383617 IP 98.139.183.24 > 192.168.1.56: ICMP echo reply, id 13411, seq 8, length 64
22:35:12.385948 IP 192.168.1.56.63895 > 8.8.8.8.53: 46666+ PTR? 24.183.139.98.in-addr.arpa. (44)
22:35:12.437624 IP 8.8.8.8.53 > 192.168.1.56.63895: 46666 1/0/0 PTR ir2.fp.vip.bf1.yahoo.com. (82)
22:35:13.056951 IP 192.168.1.56 > 98.139.183.24: ICMP echo request, id 13411, seq 9, length 64
22:35:13.386615 IP 98.139.183.24 > 192.168.1.56: ICMP echo reply, id 13411, seq 9, length 64
22:35:24.976213 IP 192.168.1.56.56053 > 91.189.89.76.443: Flags [F.], seq 223, ack 1, win 913, options [nop,nop,TS val 9086283 ecr 2023468429,nop,nop,sack 1 {1449:1519}], length 0
22:35:25.193640 IP 91.189.89.76.443 > 192.168.1.56.56053: Flags [F.], seq 1519, ack 224, win 122, options [nop,nop,TS val 2023480771 ecr 9086283], length 0


```

[http://yahoo.com](http://yahoo.com) is as follows:
```

22:37:51.859941 IP 192.168.1.56.23135 > 8.8.8.8.53: 51005+ A? www.yahoo.com. (31)
22:37:51.902646 IP 8.8.8.8.53 > 192.168.1.56.23135: 51005 6/0/0 CNAME fd-fp3.wg1.b.yahoo.com., CNAME ds-fp3.wg1.b.yahoo.com., CNAME ds-any-fp3-lfb.wa1.b.yahoo.com., CNAME ds-any-fp3-real.wa1.b.yahoo.com., A 206.190.36.105, A 206.190.36.45 (174)
22:37:51.904864 IP 192.168.1.56.35989 > 8.8.8.8.53: 1700+ A? www.yahoo.com. (31)
22:37:51.951636 IP 8.8.8.8.53 > 192.168.1.56.35989: 1700 6/0/0 CNAME fd-fp3.wg1.b.yahoo.com., CNAME ds-fp3.wg1.b.yahoo.com., CNAME ds-any-fp3-lfb.wa1.b.yahoo.com., CNAME ds-any-fp3-real.wa1.b.yahoo.com., A 206.190.36.105, A 206.190.36.45 (174)
22:37:52.096662 IP 206.190.36.45.80 > 192.168.1.56.37917: Flags [S.], seq 3736218828, ack 3102944601, win 8192, options [mss 1460,nop,nop,sackOK,nop,wscale 8], length 0
22:37:52.098652 IP 192.168.1.56.37917 > 206.190.36.45.80: Flags [.], ack 1, win 913, length 0
22:37:52.100653 IP 192.168.1.56.37917 > 206.190.36.45.80: Flags [P.], seq 1:1436, ack 1, win 913, length 1435
22:37:52.100774 IP 192.168.1.1 > 192.168.1.56: ICMP 206.190.36.45 unreachable - need to frag (mtu 576), length 556
22:37:52.103437 IP 192.168.1.56.37917 > 206.190.36.45.80: Flags [.], seq 1:537, ack 1, win 913, length 536
22:37:52.104449 IP 192.168.1.56.37917 > 206.190.36.45.80: Flags [.], seq 537:1073, ack 1, win 913, length 536
22:37:52.105520 IP 192.168.1.56.37917 > 206.190.36.45.80: Flags [P.], seq 1073:1436, ack 1, win 913, length 363
22:37:52.331652 IP 206.190.36.45.80 > 192.168.1.56.37917: Flags [.], ack 537, win 27, length 0
22:37:52.338662 IP 206.190.36.45.80 > 192.168.1.56.37917: Flags [.], ack 1073, win 32, length 0
22:37:52.339630 IP 206.190.36.45.80 > 192.168.1.56.37917: Flags [.], ack 1436, win 36, length 0
22:37:52.684646 IP 192.168.1.56.37904 > 206.190.36.45.80: Flags [F.], seq 0, ack 1, win 913, options [nop,nop,sack 1 {1018:1019}], length 0
22:37:54.368732 IP 192.168.1.56.37904 > 206.190.36.45.80: Flags [F.], seq 0, ack 1, win 913, options [nop,nop,sack 1 {1018:1019}], length 0
22:37:56.905153 ARP, Request who-has 192.168.1.56 tell 192.168.1.1, length 28
22:37:56.907011 ARP, Reply 192.168.1.56 is-at 00:1c:bf:88:76:99, length 46
22:37:57.736654 IP 192.168.1.56.37904 > 206.190.36.45.80: Flags [F.], seq 0, ack 1, win 913, options [nop,nop,sack 1 {1018:1019}], length 0
22:38:04.472945 IP 192.168.1.56.37904 > 206.190.36.45.80: Flags [F.], seq 0, ack 1, win 913, options [nop,nop,sack 1 {1018:1019}], length 0
22:38:07.368654 IP 206.190.36.45.80 > 192.168.1.56.37917: Flags [F.], seq 1018, ack 1436, win 36, length 0
22:38:07.370559 IP 192.168.1.56.37917 > 206.190.36.45.80: Flags [.], ack 1, win 913, options [nop,nop,sack 1 {1018:1019}], length 0
22:38:15.332316 IP 192.168.1.56.53890 > 91.189.89.114.443: Flags [F.], seq 942858671, ack 960584386, win 913, options [nop,nop,TS val 9128866 ecr 2011152679,nop,nop,sack 1 {1449:1519}], length 0
22:38:15.543653 IP 91.189.89.114.443 > 192.168.1.56.53890: Flags [F.], seq 1519, ack 1, win 122, options [nop,nop,TS val 2011165023 ecr 9128866], length 0
22:38:15.545601 IP 192.168.1.56.53890 > 91.189.89.114.443: Flags [R], seq 942858672, win 0, length 0
22:38:17.944806 IP 192.168.1.56.37904 > 206.190.36.45.80: Flags [F.], seq 0, ack 1, win 913, options [nop,nop,sack 1 {1018:1019}], length 0

```

There was the curious "need to frag (mtu 576), length 556" message in above. Maybe that's another clue?

Thanks!
kwiadnyana

---

### Post by The Cog on 2013-09-14
I'm not sure the need to fragment is anything to do with it. Your client is observing that, and re-sending that packet in three fragments, which all get acknowledged by the server.

It seems to me that the client is timing out waiting for a response from the server. Without seeing more of the content of the packets, I can't be really sure what's going on, but I do have one suspicion. Is 192.168.1.56 a Linux box? If so, can you please try this command on it, to temporarily disable TCP window scaling:
```
sudo sysctl -w "net.ipv4.tcp_window_scaling=0"
```
If that makes no difference, you can turn it back on again with```
sudo sysctl -w "net.ipv4.tcp_window_scaling=1"
```

If it makes things work you can add these two lines to /etc/sysctl.conf to make it disabled after a reboot:
```
# Disable TCP window scaling
net.ipv4.tcp_window_scaling=0
```

If window scaling turns out to be the problem, you may want to read more about it (I don't think it's a Linux problem, but something else further along between you and the web server): [http://en.wikipedia.org/wiki/TCP_window_scale_option](http://en.wikipedia.org/wiki/TCP_window_scale_option)

---

### Post by s-bodet on 2013-09-14
> **kwiadnyana said:**
> 
There was the curious "need to frag (mtu 576), length 556" message in above. Maybe that's another clue?


It means your client sends IP packets with the DF bit set.
Then the Cisco 2100 sends an ICMP T3,C4 when it needs to forward an IP packet larger than the MTU of the outgoing interface.

I would first check why the outgoing interface of the 2100 has a so tiny MTU...  Sounds strange to me.

Then, I would redo testings with a client that doesn't send IP packets with the DF bit set (you can tune this parameter in Windows through the Config Register, just ask Google since it depends on the OS, or in Ubuntu by setting the value /proc/sys/net/ipv4/ip_no_pmtu_disc to 1).  Another idea is to use 'ping' command with different payloads with the DF bit set or not...

Setting or not the DF Bit is a long debate...  There are pros ans cons...  Especially when IP packets need to pass through multiple encapsulations (OpenVPN, GRE/IPSec tunnels, etc).
Keep in mind that if you want the IP Path MTU Discovery to work, all gateways/firewalls along the path must be compliant to it (RFC1191).  Otherwise they will silently drop the IP packets...

Steve

---

### Post by kwiadnyana on 2013-09-14
> **s-bodet said:**
> 
I would first check why the outgoing interface of the 2100 has a so tiny MTU...  Sounds strange to me.


Thanks Cog, Steve. I will check on these later. I would comment on Steve's post, though, that the Cisco 2100 modem is configured by the cable company. I think they (cable co) wanted to discourage routing because they wanted to sell their 'wireless router and service' package. So maybe there is a landmine hidden somewhere in their configuration? This is shown by the fact that the modem will only talk to the machine whose MAC address is detected at the time the modem boots up (no hot swapping of PC while the modem is powered up).

Aside from the above, interestingly though, when I use Win XP as the router (on the laptop), it routes packets successfully. So this problem occurs only when I use Ubuntu as the router software.

To add confusion to all this, **I can browse** from the router computer (on Ubuntu) normally while the client computer is unable to do that. So, my suspicion is that there is something wrong in the routing strategy.

---

### Post by The Cog on 2013-09-15
> Aside from the above, interestingly though, when I use Win XP as the router (on the laptop), it routes packets successfully. So this problem occurs only when I use Ubuntu as the router software.

To add confusion to all this, I can browse from the router computer (on Ubuntu) normally while the client computer is unable to do that. So, my suspicion is that there is something wrong in the routing strategy.

I think that rules out TCP window scaling as the cause of the problem. That's not going to be affected by which OS is doing the routing.

Sorry, but I think I'm out of ideas except maybe one last guess - maybe it's the MTU setting on the internet interface. Try this:
```
sudo ifconfig eth3 mtu 576
```

---

