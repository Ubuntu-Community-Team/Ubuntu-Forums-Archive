---
title: "Wireless problem...Help!"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by pillu on 2007-02-16
Hi all,

I upgraded from my perfectly functioning 6.06 Dapper to 6.10 Edgy (Kubuntu). I am having problems connnecting to my wireless network ever since. The wireless network was detected but could not be connected to. I followed everything in this post

[http://www.ubuntuforums.org/showthread.php?t=361932](http://www.ubuntuforums.org/showthread.php?t=361932)

Here are the output of some commands. Note that wireless is eth1 and I disabled eth0 as mentioned in the post

```
anand@zorg:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"ANMIT"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:CA:D7:E6
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:xxxxxxxxx   Security mode:open
          Power Management:off
          Link Quality=91/100  Signal level=-40 dBm  Noise level=-41 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:20   Missed beacon:0
``` 

So the network can be detected. Now I tried the dhcp

```
anand@zorg:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:b0:cc:76:2f
Sending on   LPF/eth0/00:0f:b0:cc:76:2f
Listening on LPF/eth1/00:18:de:2c:99:86
Sending on   LPF/eth1/00:18:de:2c:99:86
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.103 -- renewal in 267638 seconds.
```

but when I try to ping my router 

```
anand@zorg:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.103 icmp_seq=1 Destination Host Unreachable
From 192.168.0.103 icmp_seq=2 Destination Host Unreachable
From 192.168.0.103 icmp_seq=3 Destination Host Unreachable
```

Could someone please help me with this. Thanks

---

### Post by gradedcheese on 2007-02-16
> bound to 192.168.0.103 -- renewal in 267638 seconds.

Don't worry: if you got this far, you're very close.  Do you have a second PC or laptop on the same network?  If so, you can do some useful troubleshooting: perhaps your router just doesn't respond to pings, or there are some other issues.  Try pinging a different PC.  Also, on that different PC try running this:

```

sudo tcpdump host 192.168.0.103

```

(change the IP as needed to match that of the troublesome PC).  Then ping that PC from the one you're troubleshooting: does tcpdump show incomming traffic?  Also, lets be absolutely sure you're using eth1 when you ping:

```

ping -I eth1 192.168.0.1

```

---

### Post by wieman01 on 2007-02-16
Two possible problems:

1. You are using Firestarter which prevents you from connecting (I often have a similar problem for no reason).
2. Your DNS settings have not been updated as in "/etc/resolv.conf". 

As for #2, please post the contents of that file:
> cat /etc/resolv.conf

---

### Post by pillu on 2007-02-16
@gradedcheese
The other computer on the network is my roommate's laptop which I think does not have linux on it. Is there some way I can do this with windows ?

@wieman01
I modified the contents of resolve.conf and added my ISP's dns to it already. The contents now look like:
```
search cpe.orbis.net
#nameserver 192.168.0.1
nameserver  206.196.46.26
```

I don't know if firestarter is installed by default on kubuntu 6.10 because I haven't installed it myself but will check that. I suppose when i do 

sudo ps -e

firestarter will show up as a process.

Thanks for following up guys.

---

### Post by pillu on 2007-02-16
Another update:

I think the problem is with the DHCP because if I shut the network down and then start it up again I do not get any IP assigned. When I do "dhclient eth1" it keeps listening on eth1 without any success. So I think my success with getting dhcp to work was just a one time thing. I will keep looking the forums for any solutions to this.

cheers

---

### Post by Bogdan Ghiurco on 2007-02-16
I had the same problem. And i didn't know what to do. I have tried every sollution, but in vain... So I called my good friend, who's an wireless master, and the problem was solved.
 [http://www.wikipedia.org/](http://www.wikipedia.org/)

---

### Post by pillu on 2007-02-16
> **Bogdan Ghiurco said:**
> I had the same problem. And i didn't know what to do. I have tried every sollution, but in vain... So I called my good friend, who's an wireless master, and the problem was solved.
 [http://www.wikipedia.org/](http://www.wikipedia.org/)

Hey Bogdan,

Could you be more explicit ? What am I looking for on Wikipedia (which I assume is your good friend)

---

### Post by pillu on 2007-02-20
I still haven't got the wireless to work...I am posting this to bump up the thread....Could someone please help ? I have been doing thread hunting all week now :(

---

### Post by pillu on 2007-02-20
Final update....after much tinkering around....Basically I did the same things I was doing before. But it just worked somehow :)

---

