---
title: "Cannot conntect to google.com"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by rook_lv on 2006-08-16
I can ping it and resolve the IP 66.02.7.9, which is what my XP computer resolves to. I cannot trace it past 68.1.0.82. I ran some of the previously posted terminal commands:

rook@LinuxLappy:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
6.6.6.0         *               255.255.255.0   U     0      0        0 ath0
default         [www.routerlogin](www.routerlogin) 0.0.0.0         UG    0      0        0 ath0
rook@LinuxLappy:~$ cat /ect/resolve.conf
cat: /ect/resolve.conf: No such file or directory
rook@LinuxLappy:~$ ping 82.211.81.186
PING 82.211.81.186 (82.211.81.186) 56(84) bytes of data.
64 bytes from 82.211.81.186: icmp_seq=1 ttl=41 time=167 ms
64 bytes from 82.211.81.186: icmp_seq=2 ttl=41 time=154 ms
64 bytes from 82.211.81.186: icmp_seq=3 ttl=41 time=184 ms
64 bytes from 82.211.81.186: icmp_seq=4 ttl=41 time=153 ms
64 bytes from 82.211.81.186: icmp_seq=5 ttl=41 time=163 ms
64 bytes from 82.211.81.186: icmp_seq=6 ttl=41 time=154 ms
64 bytes from 82.211.81.186: icmp_seq=7 ttl=41 time=156 ms
64 bytes from 82.211.81.186: icmp_seq=8 ttl=41 time=156 ms
64 bytes from 82.211.81.186: icmp_seq=9 ttl=41 time=157 ms

--- 82.211.81.186 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 8023ms
rtt min/avg/max/mdev = 153.580/161.019/184.394/9.293 ms
rook@LinuxLappy:~$ ping [www.ubuntuforums.org](www.ubuntuforums.org)
PING [www.ubuntuforums.org](www.ubuntuforums.org) (82.211.81.186) 56(84) bytes of data.
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=1 ttl=41 time=158 ms64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=2 ttl=41 time=154 ms64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=3 ttl=41 time=155 ms64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=4 ttl=41 time=157 ms64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=5 ttl=41 time=152 ms
--- [www.ubuntuforums.org](www.ubuntuforums.org) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4015ms
rtt min/avg/max/mdev = 152.897/155.652/158.093/1.910 ms
rook@LinuxLappy:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
6.6.6.0         0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         6.6.6.1         0.0.0.0         UG    0      0        0 ath0
rook@LinuxLappy:~$ cat /ect/resolve.conf
cat: /ect/resolve.conf: No such file or directory
rook@LinuxLappy:~$ sudo cat /ect/resolve.conf
Password:
cat: /ect/resolve.conf: No such file or directory
rook@LinuxLappy:~$ sudo cat /ect/resolve.conf
cat: /ect/resolve.conf: No such file or directory
rook@LinuxLappy:~$ sudo cat /ect/resolve.conf
cat: /ect/resolve.conf: No such file or directory
rook@LinuxLappy:~$ sudo cat /ect/resolve.conf
cat: /ect/resolve.conf: No such file or directory


I'm at a lost here. I can't see where it's failing a Cox SWEARS it is a problem on my side. They alwasy swear it's a problem on my side. Any helo would be appreciated.

By they way, i am a linux n00b. But I'm an old pro at windows, so i have a fair bit of networking experiance behind me. I just can't see what on earth would cause one OS to fail and the other to succeed at getting to a particular website. By the by, my internet is working otherwise. In fact, i'm posting this from the linux laptop right now.

---

### Post by JerMe on 2006-08-16
First thing that pops in my head, your **/etc/resolv.conf** file. ;)

```
cat /etc/resolv.conf
```

Mind posting the output?

---

### Post by rook_lv on 2006-08-16
i can't get any output on that. I've tried. All i get is:

rook@LinuxLappy:~$ cat /ect/resolve.conf
cat: /ect/resolve.conf: No such file or directory

Could that be the issue?

---

### Post by JerMe on 2006-08-16
... because there's no such thing as an **ect** directory? :)

---

### Post by rook_lv on 2006-08-16
I browsed and found the file. Opened in gedit and here's what I found:

search Belkin
nameserver 6.6.6.1

---

### Post by rook_lv on 2006-08-16
> **JerMe said:**
> ... because there's no such thing as an **ect** directory? :)

Point taken. I get the same thing when I use the CORRECT directory:

search Belikn
nameserver 6.6.6.1

---

### Post by drtvasudevan on 2006-08-16
you can ping the ubuntu server.
so fix the ipv6 problem before looking for other solutions.
in the firefox address bar type about:config 
and in the filter bar type ipv6 
and change from false to true= just double click it 
shutdown firefox
restart firefox

---

### Post by rook_lv on 2006-08-16
done the firefox thing as well. That's hasn't made a bit of difference. Although, seeing as how I cannot trace my way to google seems a bit telling that it is not a firefox config issue.

---

### Post by goatflyer on 2006-08-16
Try:

```


nslookup google.com


```

and paste the output.

---

### Post by JerMe on 2006-08-16
I'm not sure about your /etc/resolv.conf file.  change the **search Belkin** line to read something like **search *your_isp***.  For example, my /etc/resolv.conf file reads:

```
search san.rr.com
nameserver 192.168.0.1
```

Reason I say this is because it seems that your resolv.conf is trying to use your router for DNS queries, but your router isn't configured to do so.  So use your ISP's DNS instead.

---

### Post by rook_lv on 2006-08-17
> **goatflyer said:**
> Try:

```


nslookup google.com


```

and paste the output.

rook@LinuxLappy:~$ nslookup google.com
Server:         6.6.6.1
Address:        6.6.6.1#53

Non-authoritative answer:
Name:   google.com
Address: 64.233.187.99
Name:   google.com
Address: 72.14.207.99
Name:   google.com
Address: 64.233.167.99

---

### Post by rook_lv on 2006-08-17
FIXED! The issue is with the firmware on the router. If you have the netgear WNR834B you MUST be running firmware 1.0.2.4 to resolve this issue. I thought I had upgraded it previously, but it would seem I didn't. Sorry for the wild goose chase. Now, has anyone seen my left-handed smoke shifter lying about? :cool:

---

