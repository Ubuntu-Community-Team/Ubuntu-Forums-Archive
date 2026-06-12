---
title: "Unable to access some website"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by DFry on 2008-01-12
Since two days, I can't access some website like [www.washingtonpost.com](www.washingtonpost.com), [www.accuweather.com](www.accuweather.com) or [www.msnbc.msn.com](www.msnbc.msn.com), independent of the browser I use. I have a Intel® PRO/Wireless 3945ABG chip, and a Windows machine connected to the same router opens the sites just fine. I did run some updates recently, but really can't remember which ones (is there a log somewhere?). I followed the instruction at [http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon](http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon) because I thought that might be it, but to no avail.
Thanks for your help.

---

### Post by Sukarn on 2008-01-12
Go to System -> Administration -> Network -> DNS
Check the tab DNS Servers, and try adding these two to it -
208.67.222.222
208.67.220.220

---

### Post by erfahren on 2008-01-12
I don't know if this will help that much but you can see the history of Updates through Synaptic Package Manager (File > History)

try enering this into your browsers address bar and see if the washingtonpost site comes up
```

12.129.147.65

```
(I got it from doing in the terminal)
```

host www.washingtonpost.com

```
if that works then it's a DNS issue - the DNS address that were posted are the OpenDNS addresses (which I was going to suggest as well) - they'd get entered into /etc/resolv.conf

---

### Post by DFry on 2008-01-12
Thanks, but both methods didn't work. 

These are my recent updates:

deskbar-applet (2.20.0-0ubuntu2) to 2.20.1-0ubuntu1
libdb4.4 (4.4.20-8.1ubuntu3) to 4.4.20-8.1ubuntu3.1
libsnmp-base (5.3.1-6ubuntu2) to 5.3.1-6ubuntu2.1
libsnmp10 (5.3.1-6ubuntu2) to 5.3.1-6ubuntu2.1
openssh-client (1:4.6p1-5build1) to 1:4.6p1-5ubuntu0.1
ssh-askpass-gnome (1:4.6p1-5build1) to 1:4.6p1-5ubuntu0.1
cupsys (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.3
cupsys-bsd (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.3
cupsys-client (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.3
cupsys-common (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.3
libcupsimage2 (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.3
libcupsys2 (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.3
libcupsys2-dev (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.3
libpt-1.10.0 (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
libpt-plugins-alsa (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
libpt-plugins-v4l (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
libpt-plugins-v4l2 (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
tomboy (0.8.0-1) to 0.8.0-1ubuntu0.1

---

### Post by cubicsilver on 2008-01-14
There is a bug (59331) in the kernel that stops some websites from loading.

Here is how to fix it:

You need to edit your sysctl.conf

```
sudo gedit /etc/sysctl.conf
```

add these lines and save:

```
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760
```

then run this to make the change

```
sudo sysctl -p
```

try your website again.

---

### Post by Steve.G on 2008-05-09
These methods did not resolve my problem. For example, I can not connect to cnn.com at all. I have added open DNS to my router's config page as well as done several other edits. No dice. There are several sites that I can not connect to.

```
ping cnn.com
PING cnn.com (64.236.16.20) 56(84) bytes of data.
From ubuntu (192.168.1.66) icmp_seq=1 Destination Port Unreachable
From ubuntu (192.168.1.66) icmp_seq=2 Destination Port Unreachable
From ubuntu (192.168.1.66) icmp_seq=3 Destination Port Unreachable
From ubuntu (192.168.1.66) icmp_seq=4 Destination Port Unreachable
From ubuntu (192.168.1.66) icmp_seq=5 Destination Port Unreachable
From ubuntu (192.168.1.66) icmp_seq=6 Destination Port Unreachable

--- cnn.com ping statistics ---
6 packets transmitted, 0 received, +6 errors, 100% packet loss, time 5001ms

host cnn.com

cnn.com has address 64.236.16.20
cnn.com has address 64.236.16.52
cnn.com has address 64.236.24.12
cnn.com has address 64.236.29.120
cnn.com mail is handled by 10 atlmail3.turner.com.
cnn.com mail is handled by 10 atlmail5.turner.com.
cnn.com mail is handled by 10 nycmail1.turner.com.
cnn.com mail is handled by 10 nycmail2.turner.com.
cnn.com mail is handled by 30 lonmail1.turner.com.
cnn.com mail is handled by 40 hkgmail1.turner.com.
```

Any other bright ideas?

---

