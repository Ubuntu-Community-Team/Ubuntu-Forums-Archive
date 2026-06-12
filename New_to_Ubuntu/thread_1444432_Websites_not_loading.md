---
title: "Websites not loading"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by wab4u on 2010-04-01
Hi,

I have recently installed ubuntu 9.10 32bits. I am  a beginner. I am facing problems loading websites other than google. I can ping all websites but firefox is unable to load them (other than google). I am using wired connection and use static IP settings as given to me by my university hostel. They are working fine in XP. Looking forward to your guidance! Thank you

---

### Post by Chesamo on 2010-04-01
What error are you getting? 404? 503? Details, details, details.

---

### Post by lovinglinux on 2010-04-01
[Disable ipv6](http://lovinglinux.megabyet.net/?page_id=220#Firefox-can-connect-to-sites-only-using-the-IP-number-2)

---

### Post by wab4u on 2010-04-01
> **Chesamo said:**
> What error are you getting? 404? 503? Details, details, details.

There is no error. It just keeps waiting waiting. I get the title of the website also on the title-bar but nothing else happening.

---

### Post by Martje_001 on 2010-04-01
Could you give the output of the following commands?
```
ping google.com
traceroute google.com
wget http://www.google.com
```

You can quit 'ping' by pressing CTRL + C.

---

### Post by karthick87 on 2010-04-01
Me too faced the same problem,it was solved automatically..But still i dont find the cause for the problem..

---

### Post by wab4u on 2010-04-01
> **Martje_001 said:**
> Could you give the output of the following commands?
```
ping google.com
traceroute google.com
wget http://www.google.com
```You can quit 'ping' by pressing CTRL + C.

I get the following ouput

ping google.com

PING google.com (209.85.129.99) 56(84) bytes of data.

64 bytes from fk-in-f99.1e100.net (209.85.129.99): icmp_seq=1 ttl=53 time=5.41 ms

64 bytes from fk-in-f99.1e100.net (209.85.129.99): icmp_seq=2 ttl=53 time=5.40 ms

64 bytes from fk-in-f99.1e100.net (209.85.129.99): icmp_seq=3 ttl=53 time=5.18 ms

64 bytes from fk-in-f99.1e100.net (209.85.129.99): icmp_seq=4 ttl=53 time=5.24 ms

64 bytes from fk-in-f99.1e100.net (209.85.129.99): icmp_seq=5 ttl=53 time=5.46 ms

64 bytes from fk-in-f99.1e100.net (209.85.129.99): icmp_seq=6 ttl=53 time=5.05 ms

64 bytes from fk-in-f99.1e100.net (209.85.129.99): icmp_seq=7 ttl=53 time=5.05 ms

64 bytes from fk-in-f99.1e100.net (209.85.129.99): icmp_seq=8 ttl=53 time=5.20 ms

^C

--- google.com ping statistics ---

8 packets transmitted, 8 received, 0% packet loss, time 7020ms
rtt min/avg/max/mdev = 5.055/5.253/5.466/0.169 ms





wget [http://www.google.com](http://www.google.com)

--2010-04-01 18:23:43--  [http://www.google.com/](http://www.google.com/)

Resolving [www.google.com](www.google.com)... 209.85.129.104, 209.85.129.105, 209.85.129.106, ...

Connecting to [www.google.com|209.85.129.104|:80](www.google.com|209.85.129.104|:80)... connected.

HTTP request sent, awaiting response... 302 Found

Location: [http://www.google.de/](http://www.google.de/) [following]

--2010-04-01 18:23:43--  [http://www.google.de/](http://www.google.de/)

Resolving [www.google.de](www.google.de)... 209.85.129.99, 209.85.129.104, 209.85.129.105, ...

Reusing existing connection to [www.google.com:80](www.google.com:80).

HTTP request sent, awaiting response... 200 OK

Length: unspecified [text/html]

Saving to: `index.html'



    [ <=>                                   ] 7,463       --.-K/s   in 0.005s  



2010-04-01 18:23:43 (1.53 MB/s) - `index.html' saved [7463]



traceroute didnot work it said that there was no command as traceroute

---

### Post by Chesamo on 2010-04-01
> **wab4u said:**
> traceroute didnot work it said that there was no command as traceroute
The command is "tracert". If it's not installed, use "sudo apt-get install traceroute".

---

### Post by wab4u on 2010-04-01
> **Chesamo said:**
> The command is "tracert". If it's not installed, use "sudo apt-get install traceroute".

tracert also didnot work and I tried to install traceroute it gave the following messages

Reading package lists... Done

Building dependency tree       
Reading state information... Done

Package traceroute is not available, but is referred to by another package.

This may mean that the package is missing, has been obsoleted, or

is only available from another source

E: Package traceroute has no installation candidate

---

### Post by wab4u on 2010-04-01
> **lovinglinux said:**
> [Disable ipv6]("http://lovinglinux.megabyet.net/?page_id=220#Firefox-can-connect-to-sites-only-using-the-IP-number-2")

I disabled ipv6 in firefox as well as at the system level but still it is not loading the websites.

---

### Post by Chesamo on 2010-04-01
Look for it here.

[http://packages.ubuntu.com/karmic/traceroute](http://packages.ubuntu.com/karmic/traceroute)

---

