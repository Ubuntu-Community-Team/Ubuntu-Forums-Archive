---
title: "can't connect to certain sites"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by andymadonna on 2008-03-15
Hi I just installed Ubuntu Gutsy, I am able to get on to the internet and almost everthing works but Firefox won't connect to certain sitesm; like amazon.com, newegg.com, dell.com.

It will connect to google and ubuntuforums and about 70% of the sites I go to just fine

I have been looking around the forms and get find a solution.

I had my computer connected to a router and then a cable modem, so right now I have the computer connected directly to the modem, and it still has the same problem.

Here is a ping of amazon.com

```

andrew@andrew-desktop:~$ ping -c 10 amazon.com
PING amazon.com (72.21.206.5) 56(84) bytes of data.

--- amazon.com ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9010ms

```

and when I run a tracepath it just says no reply on each line.

$ route
```

andrew@andrew-desktop:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
76.117.212.0    *               255.255.254.0   U     0      0        0 eth0
default         c-76-117-212-1. 0.0.0.0         UG    0      0        0 eth0

```

```

andrew@andrew-desktop:~$ sudo cat /etc/resolv.conf
search hsd1.pa.comcast.net.
nameserver 68.87.64.146
nameserver 68.87.75.194

```

---

### Post by Iowan on 2008-03-15
I've seen other threads attempting to solve the same problem.  One frequent solution is to set the DNS addresses in the router.  I'll see if I can find some links.
BTW, have you reset the modem since you connect directly to it? Sometimes it "memorizes" the MAC address of the machine connected to it - and must be reset if that changes.

[Here]("http://ubuntuforums.org/showthread.php?t=615126&highlight=connect+sites+DNS&page=3") is a similar thread.
[This]("http://ubuntuforums.org/showthread.php?t=565073&highlight=connect+sites+DNS") is another.

---

### Post by andymadonna on 2008-03-15
I now think it has something to do with MoBlock. I turned it off and now every site works and the pages load much faster.

---

### Post by andymadonna on 2008-03-15
Fixed. I had to edit a line in /etc/moblock/moblock.conf

[https://help.ubuntu.com/community/MoBlock#head-9c97310221297300ca7e1ddfa293f541c6da6d81]("https://help.ubuntu.com/community/MoBlock#head-9c97310221297300ca7e1ddfa293f541c6da6d81")

---

### Post by Iowan on 2008-03-17
GREAT! Mark this one SOLVED (under Thread Tools).  Hopefully, I'll remember it for next time.

---

