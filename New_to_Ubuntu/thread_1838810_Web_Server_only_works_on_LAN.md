---
title: "Web Server only works on LAN"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by tusharsingal on 2011-09-04
Hey guys! I'm having a bit of a problem here. I'm setting up a site, and I want it to be able to be used for 2 ports, (port 80 for web, and 25565 for Minecraft). I use DynDNS (tusing.dyndns.org *and* onyxfreedom.dyndns.org). 64-bit Ubuntu but I have the 32 bit libraries installed (it was something like ia32libs, dont remember the exact name or letters),

Well, I put my .html files in /var/www/ and I can connect to my website via LAN (eg. 192.168.2.8). But the problem is, **whenever I try to connect via tusing.dyndns.org or onyxfreedom.dyndns.org, it never works. It just loads forever then tells me "Webpage not Available."**

I have port forwarding on both ports (80 and 25565) and a few more ports for things like FTP and SSH. Any ideas? I've been trying to solve this since last night D: sigh.

D=

---

### Post by tusharsingal on 2011-09-04
Also, here is the nmap analysis.

***192.168.2.8***
```

Starting Nmap 5.21 ( http://nmap.org ) at 2011-09-04 10:59 EDT
Nmap scan report for 192.168.2.8
Host is up (0.00079s latency).
Not shown: 997 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https

```


***tusing.dyndns.org***
```

Starting Nmap 5.21 ( http://nmap.org ) at 2011-09-04 10:59 EDT
Nmap scan report for tusing.dyndns.org (66.176.230.68)
Host is up (0.032s latency).
rDNS record for 66.176.230.68: c-66-176-230-68.hsd1.fl.comcast.net
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
9090/tcp open  zeus-admin

```


***onyxfreedom.dyndns.org***
```
Starting Nmap 5.21 ( http://nmap.org ) at 2011-09-04 11:00 EDT
Nmap scan report for onyxfreedom.dyndns.org (66.176.230.68)
Host is up (0.034s latency).
rDNS record for 66.176.230.68: c-66-176-230-68.hsd1.fl.comcast.net
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
9090/tcp open  zeus-admin

```



***66.176.230.68** (my ip)*
```

Starting Nmap 5.21 ( http://nmap.org ) at 2011-09-04 11:01 EDT
Nmap scan report for c-66-176-230-68.hsd1.fl.comcast.net (66.176.230.68)
Host is up (0.038s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
9090/tcp open  zeus-admin

```

---

### Post by tusharsingal on 2011-09-04
Also, I'm kind of new to Ubuntu and this forum. So, please give simple instructions.

---

### Post by tusharsingal on 2011-09-04
Anyone here? This thread has been here, for, an hour or so, and no one else even viewed it. :( :confused:

---

### Post by tusharsingal on 2011-09-05
> **tusharsingal said:**
> Anyone here? This thread has been here, for, an hour or so, and no one else even viewed it. :( :confused:

No one's here I guess. *sigh*    :confused::confused::(:(

---

### Post by bodhi.zazen on 2011-09-05
nmap from here shows no open ports.

I suspect you need to forward your ports or you have a firewall inplace, not sure which.

You really need to scan from outside you LAN, use an online scanner.

---

### Post by e79 on 2011-09-05
I only see port FTP (21) opened on your end when scanning :

```
Starting Nmap 5.21 ( http://nmap.org ) at 2011-09-05 11:43 EDT
Nmap scan report for **tusing.dyndns.org** (66.176.230.68)
Host is up (0.013s latency).
rDNS record for 66.176.230.68: c-66-176-230-68.hsd1.fl.comcast.net
Not shown: 999 filtered ports
PORT   STATE SERVICE
[B]21/tcp open  ftp
[/B] 
Nmap done: 1 IP address (1 host up) scanned in 5.31 seconds
```So as **bodhi.zazen **suggested, something must not be configured correctly on your firewall or your ISP blocks the ports.

---

