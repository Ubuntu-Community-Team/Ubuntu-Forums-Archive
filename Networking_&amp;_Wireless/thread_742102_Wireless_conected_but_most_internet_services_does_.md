---
title: "Wireless conected but most internet services does not work"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by arcktos on 2008-04-01
Hello,

Yesterday i decided to upgrade my ubuntu 7.04 to 7.10. After the hours of downloading and installing update was finally done. But there seems to be problem with Ubuntu 7.10 and internet connection bcoz Firefox, synaptic, p2p, and other network sevices are not working. Its really wird couse i can download my mail, and login on router by telnet, i can also ping evry page and normally get response. What should i do to repair it?

Regards

PS. I tried:

-sudo dhclient wlan0
-disabling Ipv6 in modprobe

my /etc/resolv.conf

nameserver 192.168.1.1

HELP PLEEEASE! ;)

---

### Post by arcktos on 2008-04-01
Bump!, help please!

---

### Post by dannyboy79 on 2008-04-01
what do these command

route

ifconfig

iwconfig

 cat /etc/network/interfaces


return from a terminal session.

---

### Post by arcktos on 2008-04-01
route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

iwconfig:

wlan0     IEEE 802.11b  ESSID:"F@st88c150"
         Mode:Managed  Frequency:2.462 GHz  Access Point: 00:60:B3:6E:8D:85
         Bit Rate=11 Mb/s   Sensitivity=-200 dBm
         RTS thr=2346 B   Fragment thr=2346 B
         Power Management:off
         Link Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:02:A5:1B:19:43
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:18:E7:01:11:14
         inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
         inet6 addr: fe80::218:e7ff:fe01:1114/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:224 errors:0 dropped:0 overruns:0 frame:0
         TX packets:237 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:15831 (15.4 KB)  TX bytes:16741 (16.3 KB)
         Interrupt:19 Memory:40100000-40110000

---

### Post by dannyboy79 on 2008-04-01
your link quality is VERY low. It's only 15. How far are you from the access point? What kind of card are you using? Are you using native linux drivers or ndiswrapper? If you can ping [www.l.google.com](www.l.google.com), what is the time it takes? Mine is this:
PING  (64.233.169.99) 56(84) bytes of data.
64 bytes from yo-in-f99.google.com (64.233.169.99): icmp_seq=1 ttl=243 time=32.5 ms
64 bytes from yo-in-f99.google.com (64.233.169.99): icmp_seq=2 ttl=243 time=32.8 ms
64 bytes from yo-in-f99.google.com (64.233.169.99): icmp_seq=3 ttl=243 time=28.7 ms
64 bytes from yo-in-f99.google.com (64.233.169.99): icmp_seq=4 ttl=243 time=28.0 ms
64 bytes from yo-in-f99.google.com (64.233.169.99): icmp_seq=5 ttl=243 time=32.5 ms
64 bytes from yo-in-f99.google.com (64.233.169.99): icmp_seq=6 ttl=243 time=29.0 ms

That's a hard line though, 100Mbit. i am guessing it's just a connection strength issue.

---

### Post by arcktos on 2008-04-01
Thats not the way. On 7.04 it worked perfectly. Im using ndiswrapper.

---

### Post by dannyboy79 on 2008-04-01
well ok, if that's not the way then it sounds like you don't need any help. Good luck.

---

### Post by arcktos on 2008-04-01
Noooo ;)

I still have no internet expect pinging and mailing, please, help me, i think i tried everything! ;)

---

### Post by stream303 on 2008-04-01
Looks like a dns issue - classic being able to ping, but not resolve any urls, etc.

Do you know your ISP's dns primary and backup server addresses?  If so, you can enter them into your networking preferences.  Even better, if you are behind a router, you can enter them into the router's configuration page and let the machines pick them up from there.

If you don't know your dns server addresses, I tend to favor those at

[http://www.opendns.com](http://www.opendns.com)

Just look at the right hand bottom of the page for the primary and backup addresses you can use.  There are more dns servers available, but don't just pick one out of thin air or based on what you see in a thread - go to the site to confirm, hence the reason I don't show them here. :)

Give that a shot...

---

### Post by dannyboy79 on 2008-04-01
if he can ping [www.gogle.com](www.gogle.com) from the terminal than it's not a dns issue is it?

---

### Post by stream303 on 2008-04-01
> **dannyboy79 said:**
> if he can ping [www.gogle.com](www.gogle.com) from the terminal than it's not a dns issue is it?

Yes, you are definitely right.  I got a little fast on the draw there. :)

---

### Post by arcktos on 2008-04-02
then how cani solve this???

---

### Post by dannyboy79 on 2008-04-02
respond with what I asked you. please post the results of this command

ping [www.gogle.com](www.gogle.com)

---

### Post by arcktos on 2008-04-02
PING [www.l.google.com](www.l.google.com) (66.249.91.99) 56(84) bytes of data.
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=1 ttl=244 time=51.4 ms
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=2 ttl=244 time=48.5 ms
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=3 ttl=244 time=49.2 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10134ms
rtt min/avg/max/mdev = 48.535/49.742/51.436/1.233 ms

---

### Post by dannyboy79 on 2008-04-02
well, it doesn't appear to be a connection issue since you didn't have any dropped packets and it resolved [www.gogle.com](www.gogle.com) so it's not a dns issue. what does this return?

nslookup 127.0.0.1

---

### Post by arcktos on 2008-04-02
Server:         192.168.1.1
Address:        192.168.1.1#53

1.0.0.127.in-addr.arpa  name = localhost.

---

### Post by dannyboy79 on 2008-04-02
found on gogle.



1. Opened "about:config" within firefox, filter by ipv6 and set it to true
2. /etc/hosts changed (IPv6 section)

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

---

### Post by dannyboy79 on 2008-04-02
also, is there any relevant info within dmesg? just enter it within a terminal, it will be long, look for errors or anything unusual.

---

### Post by arcktos on 2008-04-02
i tried everything, your last tips didnt work at all. Do u or anybody have anymore ideas?

---

### Post by dannyboy79 on 2008-04-02
this has been a huge problem for some people because of their routers. The majority of solutions involve turning off IPv6 within firefox, if that didn't do it. than you can try to hard code your dns nameservers within your /etc/dhcp3/dhclient.conf file. it would look something like this:

prepend domain-name-servers 208.67.222.222,208.67.220.220;

and in the section directly below that, change this:

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

so that it doesn't request any  domain-name-servers from your dhcp server (your router I am assuming). so just erase the following:

 domain-name-servers,

those are dns servers from opendns. that's all that I can think, sorry I couldn't solve this for you.

---

### Post by arcktos on 2008-04-02
:guitar::guitar::guitar::guitar::guitar:

YEEEEAY, i found solution at last!

net.ipv4.tcp_window_scaling=0
to file: /etc/sysctl.conf

but i got one more question, can anybody explain me what is this doing? 
REGARDS.

---

### Post by dannyboy79 on 2008-04-02
I couldn't tell you what that does? maybe someone else can, glad you got it working.

---

