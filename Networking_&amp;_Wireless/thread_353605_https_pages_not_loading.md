---
title: "https pages not loading"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by abuntoyoutoo on 2007-02-04
I recently installed ubuntu 6.10. However, while most internet pages work correctly, pages prefixed with https (such as [https://help.ubuntu.com/](https://help.ubuntu.com/)) won't connect. It results in this error:
```

Unable to connect
Firefox can't establish a connection to the server at help.ubuntu.com.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

```
Other sites that do not work include gmail, hotmail and other such sites. It appears like I am missing something which allows the opening of encripted pages but I have no ideas about what it could be. I would greatly appreciate any help!

---

### Post by amohanty on 2007-02-04
Thats because a server needs to explicitely be running a secure server to serve out pages on the https link. Its possible:
a. help.ubuntu.com is not running https (doesnt seem so from an nmap scan)
b. its overloaded.

To rephrase:
Its not you, its them :)

HTH
AM

---

### Post by abuntoyoutoo on 2007-02-04
> Its not you, its them :)
I actually think it is me, as it works on other computers without a problem. For example, I cannot get onto my gmail account using this computer, while I can get onto it using another (windows xp) computer. Is there any workaround to get it working?

---

### Post by kidders on 2007-02-04
Hi there,

> **amohanty said:**
> Thats because a server needs to explicitely be running a secure server to serve out pages on the https link. Its possible:
a. help.ubuntu.com is not running https (doesnt seem so from an nmap scan)
b. its overloaded.

To rephrase:
Its not you, its them :)

HTH
AM

I'm not so sure about this...

```
$ nmap help.ubuntu.com

Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2007-02-05 03:18 GMT
Interesting ports on 82.211.81.234:
(The 1661 ports scanned but not shown below are in state: filtered)
PORT    STATE SERVICE
80/tcp  open  http
443/tcp open  https

Nmap finished: 1 IP address (1 host up) scanned in 23.129 seconds
```

The link posted works fine for me over HTTPS. :confused:

I wonder if it would be worth testing out a couple of things:

[LIST]
[*]Does SSL work in another browser... Links, for instance?
[*]Can you connect to help.ubuntu.com over port 443 with telnet?
[/LIST]

**Edit:** It's also worth asking if you've done something odd with your firewall, or are using a HTTP proxy to access the web.

---

### Post by abuntoyoutoo on 2007-02-04
> Does SSL work in another browser... Links, for instance?
No, reports that it is making a connection, but it never succeeds. It reports an error
```

  Unable to retrieve https://help.ubuntu.com/:  &#9474;               
               &#9474;                                                &#9474;               
               &#9474;                No route to host

```


> Can you connect to help.ubuntu.com over port 443 with telnet?
I'm not that good at using telnet. What command should I use to do this?

> It's also worth asking if you've done something odd with your firewall, or are using a HTTP proxy to access the web.
I don't know how to access the firewall in ubuntu yet. Also, this problem has existed since i installed it. I'm not using a proxy.

---

### Post by amohanty on 2007-02-05
Kidders: as I mentioned it didnt seem so from nmap. :)

abuntoyoutoo: 
Sorry I read the FP as you **can** get to gmail et al.
Can you post the output of :
ps aux | grep fire

AM

---

### Post by abuntoyoutoo on 2007-02-05
> abuntoyoutoo:
Sorry I read the FP as you can get to gmail et al.
Can you post the output of :
ps aux | grep fire
Here it is:
```

david     4655  3.4  8.5 178408 66372 ?        Sl   13:33   5:44 /usr/lib/firefox/firefox-bin
david    10097  0.0  0.0   2808   760 pts/1    R+   16:20   0:00 grep fire

```

---

### Post by amohanty on 2007-02-05
firestarter's not running then. 
can you post the output of:


telnet help.ubuntu.com 443

AM

---

### Post by abuntoyoutoo on 2007-02-05
output of: telnet help.ubuntu.com 443:

```
Trying 1.0.0.0...
telnet: Unable to connect to remote host: No route to host
```

---

### Post by amohanty on 2007-02-05
**Trying 1.0.0.0...**

aaaaaaahhhhhhh! so now we know the truth. 
post the output of 

ifconfig -a

AM

---

### Post by abuntoyoutoo on 2007-02-05
> aaaaaaahhhhhhh! so now we know the truth. 
Yay! :) 

Output of ifconfig -a

```

eth0      Link encap:Ethernet  HWaddr 00:40:CA:40:C5:11  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe40:c511/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37465588 (35.7 MiB)  TX bytes:2505645 (2.3 MiB)
          Interrupt:185 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by amohanty on 2007-02-06
OK everything looks good here. Post the contents of :

/etc/resolv.conf
/etc/hosts

AM

---

