---
title: "Netgear HEAD TO HEAD with Linux"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by Sugi on 2007-07-30
I have notice on Linux (ubuntu 7.04 feisty fawn) that it can't get internet to all of the programs.  It can only get internet with Aim (under Gaim/Pidgin) and IRC.  No internet with firefox, msn and yahoo (also under Pidgin). I do not know what to do.  My computer with the linux partition also has windows with a dual boot setup.  The windows and linux partition shares the same IP.  But Windows can get internet with any programs.  Side note, I can get internet with Ubuntu on different router just not Netgear,

Has anyone notice the same problem as me?

---

### Post by Sugi on 2007-08-12
o.0





BUMP!

---

### Post by callan79 on 2007-08-12
> **Sugi said:**
> It can only get internet with Aim (under Gaim/Pidgin) and IRC.  No internet with firefox, msn and yahoo (also under Pidgin). I do not know what to do


Hi Sugi,

I work for an Internet provider here in Australia and I hear this question from some customers. Sometimes what can happen is that the DNS would not be passed to the computer properly. Here's how you can check....

Type these commands in a terminal, I will also paste the results you should see :

```
ping -c 1 202.6.141.215
```
PING 202.6.141.215 (202.6.141.215) 56(84) bytes of data.
64 bytes from 202.6.141.215: icmp_seq=1 ttl=59 time=19.1 ms

```
ping -c 1 www.adam.com.au
```
PING [www.adam.com.au](www.adam.com.au) (202.6.141.215) 56(84) bytes of data.
64 bytes from webhost-15.adam.com.au (202.6.141.215): icmp_seq=1 ttl=59 time=19.9 ms

```
host www.adam.com.au
```
[www.adam.com.au](www.adam.com.au) has address 202.6.141.215


Often when I see this problem, the first test above will work, and the other ones will have something like 

TEST 2 - ping: unknown host [www.adam.com.au](www.adam.com.au)
TEST 3 - Host www44.adam.com.au not found: 3(NXDOMAIN)

If this happens to you, you need to check your DNS servers in System >> Administration >> Networking, and put the DNS servers of your Internet Provider. You should also check your netgear settings, and make sure you put your Inernet Provider's DNS in there too.

Hope this works for you.

Regards,
Callan

---

