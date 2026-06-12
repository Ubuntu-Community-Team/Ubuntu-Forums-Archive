---
title: "Nothing but firefox can connet to the net"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by 2dere on 2007-04-01
G'day all.

Installed Daper Ububtu round about 7 hours ago and have abit of trouble getting my comp to acess the internet. I tried looking at the other threads before making my own but I just haven't found anything yet that's sorted me out enough to be happy.
/end rant.

My problem at first was having no internet access whats so ever with Ubuntu and after reading around managed to get firefox to connect by following the
"about:config" then turning offing the ipv6 thing.

This has allowed me to keep looking at the net while on Ubuntu but I can't update anything nor connect to the net using any other program bar firefox. I've tried rewriting the /etc/modprobe.d/aliases by changing the < alias net-pf-10 ipv6 > to read off but that hasn't made a difference, Can anyone put me outta my misery? If I need to display more information please tell me the info you guys need.

Thanks in advance

EDIT: Just noticed I have 6.06 noy 6.10 like I was claiming >.<

---

### Post by Rui Pais on 2007-04-01
Hi,
the "alias net-pf-10 ipv6" on edgy don't work.
You need to edit:
/etc/modprobe.d/blacklist
and add a line at the end:
> blacklist ipv6

---

### Post by 2dere on 2007-04-01
Ahh thanks for the tip Rui, but alas, my problem hasn't changed. 
I tried logging on via Gaim to no use and Synaptic Packaging can't download the desired files. Perhaps you guys can steer me to whats gone wrong?

---

### Post by dbott67 on 2007-04-01
Many folks have had issues with IPv6 and with DNS resolution.  ***Before you change any of your DNS servers***, can you confirm whether or not you can ping by fully qualified domain name from the terminal.

Can you post the output of the following commands:
```
dbott@thedrake:~$ [COLOR=Red]**ping www.google.com**[/COLOR]
PING www.l.google.com (64.233.161.104) 56(84) bytes of data.
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=1 ttl=234 time=43.8 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=2 ttl=234 time=43.7 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=3 ttl=234 time=45.1 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=4 ttl=234 time=43.8 ms

--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3012ms
rtt min/avg/max/mdev = 43.787/44.161/45.115/0.590 ms

dbott@thedrake:~$ [COLOR=Red]**ping www.cbs.com**[/COLOR]
PING a916.g.akamai.net (209.123.81.94) 56(84) bytes of data.
64 bytes from 209.123.81.94: icmp_seq=1 ttl=60 time=15.4 ms
64 bytes from 209.123.81.94: icmp_seq=2 ttl=60 time=15.5 ms
64 bytes from 209.123.81.94: icmp_seq=3 ttl=60 time=15.2 ms
64 bytes from 209.123.81.94: icmp_seq=4 ttl=60 time=15.7 ms
64 bytes from 209.123.81.94: icmp_seq=5 ttl=60 time=17.5 ms

--- a916.g.akamai.net ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4022ms
rtt min/avg/max/mdev = 15.229/15.905/17.566/0.845 ms

dbott@thedrake:~$ [COLOR=Red]**ping www.yahoo.com**[/COLOR]
PING www.yahoo-ht3.akadns.net (69.147.114.210) 56(84) bytes of data.
64 bytes from f1.www.vip.re3.yahoo.com (69.147.114.210): icmp_seq=1 ttl=47 time=40.7 ms
64 bytes from f1.www.vip.re3.yahoo.com (69.147.114.210): icmp_seq=2 ttl=47 time=38.2 ms
64 bytes from f1.www.vip.re3.yahoo.com (69.147.114.210): icmp_seq=3 ttl=47 time=38.5 ms
64 bytes from f1.www.vip.re3.yahoo.com (69.147.114.210): icmp_seq=4 ttl=47 time=38.7 ms
64 bytes from f1.www.vip.re3.yahoo.com (69.147.114.210): icmp_seq=5 ttl=47 time=41.4 ms

--- www.yahoo-ht3.akadns.net ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4020ms
rtt min/avg/max/mdev = 38.283/39.546/41.473/1.294 ms

```If you do not get replies, you may be suffering from name resolution issues.  You may want to try 2 things:

1. Blacklist ipv6 (as suggested above)
2. Change default DNS servers to OpenDNS servers.

Both steps are outlined in this thread (post #3 and #5):

[http://www.ubuntuforums.org/showthread.php?t=323747 ]("http://www.ubuntuforums.org/showthread.php?t=323747")

-Dave

---

### Post by 2dere on 2007-04-01
Did the ping command, everything went as good as can be. Went over the thread you gave me and nothing had  changed at all. I did noticed however with the ```
cat /etc/resolv.conf
``` you gave on that thread my name server pulled up 10.1.1.1 which was different from the number Wingsfan gave back to you.

Cheers for the help though.

---

### Post by dbott67 on 2007-04-01
That may be due to the router DHCP configuration.

Can you post the output of the following commands:
```
dbott@thedrake:~$ [COLOR=Red]**ifconfig -a**[/COLOR]
[COLOR=Red]eth0  [/COLOR]    Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55
          [COLOR=Red]inet addr:192.168.1.106[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2507483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2190593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2169285565 (2.0 GiB)  TX bytes:889103590 (847.9 MiB)
          Interrupt:185 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:781534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:781534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:558347414 (532.4 MiB)  TX bytes:558347414 (532.4 MiB)

```
and 
```
dbott@thedrake:~$ [COLOR=Red]**route -n**[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[COLOR=Red]192.168.1.0[/COLOR]     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         [COLOR=Red]192.168.1.1[/COLOR]     0.0.0.0         UG    0      0        0 eth0

```

In my case, you'll notice that my ethernet card (eth0) is assigned 192.168.1.106 and my default gateway is 192.168.1.1.  In your case, I would suspect that your ethernet card woud be assigned an IP address similar to 10.1.1.xxx.  The fact that you already have some internet access means that it's probably not an IP address issue.

Can you also describe your network layout (router make & model, # of computers, wired/wireless, cable/DSL ISP, etc.)?

Thanks,
Dave

PS - I'll be offline for a few hours but I'll take a look when I get home.

---

### Post by 2dere on 2007-04-01
Ohhh I've noticed an irregularity in my numbers comparing them to what you highlighted. This is what I turned up doing as you asked.
```
hhjlb@KaminaHaruka:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:00:21:04:45
          inet addr:[COLOR="Red"]10.1.1.3[/COLOR]  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:262982 (256.8 KiB)  TX bytes:18877 (18.4 KiB)
          Interrupt:177 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

```
Coupled by
```
hhjlb@KaminaHaruka:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[COLOR="Yellow"]10.0.0.0 [/COLOR]       0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0        [COLOR="Red"] 10.1.1.1[/COLOR]        0.0.0.0         UG    0      0        0 eth0

```

As for explaining my setup, bear with me here as I've upgraded to ADSL the day before installing Ubuntu.
Router is a wired D-Link DSL-502T hooked up to 1 computer. I'm sure its worth pointing out that we were told that our service provider supported linux (we got this through a door to door salesman >.<) Only to find out they don't. So the instalation disc was rendered useless and have been winging the setup to do it itself.

---

### Post by Rui Pais on 2007-04-02
hi again.
there is no problem. 
It's just that your router use that numeration, 1.0.x.x instead of 192.168.x.x. 
They are both for internal network.

The point of dbott67 was precisely **comment out** your router IP as DNS (put a # inthe begining of line at /etc/resolv.conf) and replace it for openDNS.

That should work, no matter what IP your router have.

[See here]("http://www.opendns.com/start/unix.php") for more details.

hth

---

### Post by 2dere on 2007-04-02
Alright, finally managed to follow the instructions properly. Things were made so much easier when I actually bothered to click on the Ubuntu tab and followed the slightly different instructions there. Cheers guys for the big help you've been. I'm now the happy Linux-convertee I should of been from the very start.

---

