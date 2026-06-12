---
title: "DNS problem.. Not sure though"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by simpleUser on 2006-07-18
Hello everybody,

I've been using Ubuntu Linux for a while. I've just got a new ADSL connection from my ISP. My modem is a simple DLINK 502-T.

I've got a dual boot machine and I'd like to keep it that way because I have to switch back and forth due to my work.

Now problem I have is that I can PING to any address (i.e., google, fastmail etc..).
But when I fire up websites in firefox (version 1.5.04), i get time out. 

I don't know why this is happening and I really don't know at this stage whether it's my problem or the modem's problem.

Also IMPORTANT to mention is that I can usually fire up IP addresses in firefox and the website works fine! (i.e., in firefox, typing [http://64.233.167.99](http://64.233.167.99)  (for google)  works fine) but [http://www.google.com](http://www.google.com) doesn't!!

There are some websites that I can visit without typing IP address like [http://fastmail.fm](http://fastmail.fm) and [http://www.tldp.org](http://www.tldp.org).

Also my /etc/resolv.conf has only one line
nameserver 10.1.1.1


Please help.. :(

Thank you for your time.

Cheers,
simpleUser.

---

### Post by wieman01 on 2006-07-18
Hi, 

I suspect that a missing DNS entry is not a problem since you can ping various addresses. I think your problem has to do with "ipv6" that Ubuntu enables by default. 

Look for it in the forum, you have to blacklist "ipv6" when booting and disable the function in firefox (also check in this forum how to do that). 

Unluckily I am not in front of my own computer so this all I can say.

---

### Post by simpleUser on 2006-07-18
Hey mate,

It was indeed missing DNS entries in the /etc/resolv.conf.. stupid me.. :)

But it's all good now.. Using Ubuntu at the moment. 

I'll upgrade to Dapper in a moment. ;)

But I don't know why I could ping to google or fastmail ??? strange.

thanx anyway. And thanx to people at #Ubuntu. :)

Cheers,
simpleUser.

---

### Post by wieman01 on 2006-07-18
Howdy, 

The "ping thing" is strange indeed, but let's not beat a dead horse.

But bear the "ipv6" issue in mind. You can speed up firefox considerably by disabling the "ipv6" function. Look out for it in the forum if you have performance issues.

And good luck with the new version of Ubuntu. Dapper Drake is a very nice distribution.

---

### Post by simpleUser on 2006-07-18
No worries. ;)
I'll search for it in the forum.
thanx.

Cheers,
simpleUser

---

### Post by mips on 2006-07-18
Upgrade the dlink firmware to v2+ and look at this thread, [http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337)

Make sure you use the firmware intended for your country.

---

### Post by simpleUser on 2006-07-18
Yep problems solved. :)

Thanks. The DNS entry was the main problem.. worked fine until dns entries kept on dissappearing so had to download 1) resolvconf 2) pump 3) dnsmasq and working fine! ;)

I've got the Firmware V2.00B02.AU so I reckon that's ok.

But Xchat isn't working ? Connection refused ??

Searching the forum for an answer. :-k 

Cheers,
simpleUser

---

### Post by wieman01 on 2006-07-18
Xchat... I have not used this program before but I guess it's a chat client using particular ports for communication.

Can you try to find out what ports the pogram is using? Then check whether you have a firewall running on your PC (e.g. Firestarter) or on the router (hardware firewall). You may have to open the particular ports.

---

### Post by mips on 2006-07-19
Is it only Xchat not working ? Seems weird that one single app is not working. If you don't have any firewalling then there should be no issue.

Which steps did you follow ?

---

### Post by simpleUser on 2006-07-19
Sorry I was out of loop for 2 days.. 
Anyway I have a router and that has firewall rules.
But main problem seems to be my iptables.

Alhtough I haven't loaded any firewall as such. I see list of rules when I issues "iptables -L -n". ?
I never made those rules explicitly myself unless Ubuntu has some kind of inbuilt program to make those rules automatically at start up ? 
Is it safe that is my machine ???

I can give the list of my rules if you want.
thanks.

Cheers,
simpleUser

---

### Post by simpleUser on 2006-07-19
df command shows 2 tmpfs filesystem mounted. Are they really needed ? Couldn't find answer in the forum. I am just being a little paranoid. :???: 
```


starsky@volcano:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             11590524   6096192   4905552  56% /
tmpfs                   254316        12    254304   1% /dev/shm
tmpfs                   254316     12588    241728   5% /lib/modules/2.6.12-9-386/volatile



```




and iptables -L -n shows (sorry a bit long). But I didn't actually put those rules. I think Ubuntu did this.
```

starsky@volcano:~$ sudo iptables -L -n
Password:
Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     all  --  10.1.1.1             0.0.0.0/0
LSI        all  --  0.0.0.0/0            0.0.0.0/0

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  127.0.0.1            0.0.0.0/0           tcp flags:!0x16/0x02
ACCEPT     udp  --  127.0.0.1            0.0.0.0/0
ACCEPT     tcp  --  203.87.88.1          0.0.0.0/0           tcp flags:!0x16/0x02
ACCEPT     udp  --  203.87.88.1          0.0.0.0/0
ACCEPT     tcp  --  203.87.88.2          0.0.0.0/0           tcp flags:!0x16/0x02
ACCEPT     udp  --  203.87.88.2          0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
LSI        udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:33434
LSI        icmp --  0.0.0.0/0            0.0.0.0/0
NR         all  -- !10.0.0.0/8           0.0.0.0/0
DROP       all  --  0.0.0.0/0            255.255.255.255
DROP       all  --  0.0.0.0/0            10.255.255.255
DROP       all  --  224.0.0.0/8          0.0.0.0/0
DROP       all  --  0.0.0.0/0            224.0.0.0/8
DROP       all  --  255.255.255.255      0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID
LSI        all  -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5
INBOUND    all  --  0.0.0.0/0            0.0.0.0/0
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
LSI        udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:33434
LSI        icmp --  0.0.0.0/0            0.0.0.0/0
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (93 references)
target     prot opt source               destination
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x16/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x16/0x02
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain LSO (1 references)
target     prot opt source               destination
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound '
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable

Chain NR (1 references)
target     prot opt source               destination
LSI        all  --  0.0.0.0/8            10.0.0.0/8
LSI        all  --  1.0.0.0/8            10.0.0.0/8
LSI        all  --  2.0.0.0/8            10.0.0.0/8
LSI        all  --  5.0.0.0/8            10.0.0.0/8
LSI        all  --  7.0.0.0/8            10.0.0.0/8
LSI        all  --  10.0.0.0/8           10.0.0.0/8
LSI        all  --  23.0.0.0/8           10.0.0.0/8
LSI        all  --  27.0.0.0/8           10.0.0.0/8
LSI        all  --  31.0.0.0/8           10.0.0.0/8
LSI        all  --  36.0.0.0/8           10.0.0.0/8
LSI        all  --  37.0.0.0/8           10.0.0.0/8
LSI        all  --  39.0.0.0/8           10.0.0.0/8
LSI        all  --  41.0.0.0/8           10.0.0.0/8
LSI        all  --  42.0.0.0/8           10.0.0.0/8
LSI        all  --  49.0.0.0/8           10.0.0.0/8
LSI        all  --  50.0.0.0/8           10.0.0.0/8
LSI        all  --  73.0.0.0/8           10.0.0.0/8
LSI        all  --  74.0.0.0/8           10.0.0.0/8
LSI        all  --  75.0.0.0/8           10.0.0.0/8
LSI        all  --  76.0.0.0/8           10.0.0.0/8
LSI        all  --  77.0.0.0/8           10.0.0.0/8
LSI        all  --  78.0.0.0/8           10.0.0.0/8
LSI        all  --  79.0.0.0/8           10.0.0.0/8
LSI        all  --  89.0.0.0/8           10.0.0.0/8
LSI        all  --  90.0.0.0/8           10.0.0.0/8
LSI        all  --  91.0.0.0/8           10.0.0.0/8
LSI        all  --  92.0.0.0/8           10.0.0.0/8
LSI        all  --  93.0.0.0/8           10.0.0.0/8
LSI        all  --  94.0.0.0/8           10.0.0.0/8
LSI        all  --  95.0.0.0/8           10.0.0.0/8
LSI        all  --  96.0.0.0/8           10.0.0.0/8
LSI        all  --  97.0.0.0/8           10.0.0.0/8
LSI        all  --  98.0.0.0/8           10.0.0.0/8
LSI        all  --  99.0.0.0/8           10.0.0.0/8
LSI        all  --  100.0.0.0/8          10.0.0.0/8
LSI        all  --  101.0.0.0/8          10.0.0.0/8
LSI        all  --  102.0.0.0/8          10.0.0.0/8
LSI        all  --  103.0.0.0/8          10.0.0.0/8
LSI        all  --  104.0.0.0/8          10.0.0.0/8
LSI        all  --  105.0.0.0/8          10.0.0.0/8
LSI        all  --  106.0.0.0/8          10.0.0.0/8
LSI        all  --  107.0.0.0/8          10.0.0.0/8
LSI        all  --  108.0.0.0/8          10.0.0.0/8
LSI        all  --  109.0.0.0/8          10.0.0.0/8
LSI        all  --  110.0.0.0/8          10.0.0.0/8
LSI        all  --  111.0.0.0/8          10.0.0.0/8
LSI        all  --  112.0.0.0/8          10.0.0.0/8
LSI        all  --  113.0.0.0/8          10.0.0.0/8
LSI        all  --  114.0.0.0/8          10.0.0.0/8
LSI        all  --  115.0.0.0/8          10.0.0.0/8
LSI        all  --  116.0.0.0/8          10.0.0.0/8
LSI        all  --  117.0.0.0/8          10.0.0.0/8
LSI        all  --  118.0.0.0/8          10.0.0.0/8
LSI        all  --  119.0.0.0/8          10.0.0.0/8
LSI        all  --  120.0.0.0/8          10.0.0.0/8
LSI        all  --  121.0.0.0/8          10.0.0.0/8
LSI        all  --  122.0.0.0/8          10.0.0.0/8
LSI        all  --  123.0.0.0/8          10.0.0.0/8
LSI        all  --  124.0.0.0/8          10.0.0.0/8
LSI        all  --  125.0.0.0/8          10.0.0.0/8
LSI        all  --  126.0.0.0/8          10.0.0.0/8
LSI        all  --  127.0.0.0/8          10.0.0.0/8
LSI        all  --  169.254.0.0/16       10.0.0.0/8
LSI        all  --  172.16.0.0/12        10.0.0.0/8
LSI        all  --  173.0.0.0/8          10.0.0.0/8
LSI        all  --  174.0.0.0/8          10.0.0.0/8
LSI        all  --  175.0.0.0/8          10.0.0.0/8
LSI        all  --  176.0.0.0/8          10.0.0.0/8
LSI        all  --  177.0.0.0/8          10.0.0.0/8
LSI        all  --  178.0.0.0/8          10.0.0.0/8
LSI        all  --  179.0.0.0/8          10.0.0.0/8
LSI        all  --  180.0.0.0/8          10.0.0.0/8
LSI        all  --  181.0.0.0/8          10.0.0.0/8
LSI        all  --  182.0.0.0/8          10.0.0.0/8
LSI        all  --  183.0.0.0/8          10.0.0.0/8
LSI        all  --  184.0.0.0/8          10.0.0.0/8
LSI        all  --  185.0.0.0/8          10.0.0.0/8
LSI        all  --  186.0.0.0/8          10.0.0.0/8
LSI        all  --  187.0.0.0/8          10.0.0.0/8
LSI        all  --  189.0.0.0/8          10.0.0.0/8
LSI        all  --  190.0.0.0/8          10.0.0.0/8
LSI        all  --  192.0.2.0/24         10.0.0.0/8
LSI        all  --  192.168.0.0/16       10.0.0.0/8
LSI        all  --  197.0.0.0/8          10.0.0.0/8
LSI        all  --  198.18.0.0/15        10.0.0.0/8
LSI        all  --  223.0.0.0/8          10.0.0.0/8
LSI        all  --  224.0.0.0/3          10.0.0.0/8

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:443
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:443
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpts:67:68
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:67:68
LSO        all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  10.1.1.2             127.0.0.1           tcp dpt:53
ACCEPT     udp  --  10.1.1.2             127.0.0.1           udp dpt:53
ACCEPT     tcp  --  10.1.1.2             203.87.88.1         tcp dpt:53
ACCEPT     udp  --  10.1.1.2             203.87.88.1         udp dpt:53
ACCEPT     tcp  --  10.1.1.2             203.87.88.2         tcp dpt:53
ACCEPT     udp  --  10.1.1.2             203.87.88.2         udp dpt:53
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  224.0.0.0/8          0.0.0.0/0
DROP       all  --  0.0.0.0/0            224.0.0.0/8
DROP       all  --  255.255.255.255      0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output'

```

I haven't worked that much in iptables and really new to it. Is there sth I need to be worried about ?
thanks.

Cheers,
simpleUser

---

### Post by wieman01 on 2006-07-19
So you have not installed Firestarter?

Your router's firewall could also be the problem although I understand that X-chat uses port 80. So normally there should not be an issue. 

I would suggest to install Firestarter and disable the firewall using the Firestarter GUI (there is a "disable firewall" button. Then you could try using X-chat, if it works then there is an issue with IP Table being configured.

---

### Post by facer on 2006-07-19
Ive been having a similar problem. I can login to my router at 192.168.1.1 and play with it and i can ping all sorts of sites. Im getting 127 to google.com and 104 to yahoo.com yet i cant connect to them via firefox. i havnt tried just searching for the ip yet tho.

Bear in mind im a total linux noob and only installed it today. but when the install was finished i couldnt get on the net, then i had a fiddle and it worked so i set about updating it and getting the packages i need and then bang it stopped and it hasnt worked since.

---

### Post by simpleUser on 2006-07-19
> Ive been having a similar problem. I can login to my router at 192.168.1.1 and play with it and i can ping all sorts of sites. Im getting 127 to google.com and 104 to yahoo.com yet i cant connect to them via firefox. i havnt tried just searching for the ip yet tho.

Bear in mind im a total linux noob and only installed it today. but when the install was finished i couldnt get on the net, then i had a fiddle and it worked so i set about updating it and getting the packages i need and then bang it stopped and it hasnt worked since.


Have you tried looking at /etc/resolv.conf ?? 
open it up in your editor and try this.
You should have sth like
nameserver YOUR_ISPs_PRIMARY_DNS (something like 202.x.y.z )
nameserver YOUR_ISPs_SECONDARY_DNS (ditto here)


You could also use opendns if ISPs DNS isn't working.
But the best thing is to search the forum for downloading 
1) resolvconf 2) pump 3) dnsmasq ... and all will be taken care for your *IF* it is a DNS issue.

Cheers,
simpleUser

---

### Post by simpleUser on 2006-07-19
Yeah I've got firestarter.. probably that was the causing it..
But in the firestarter, I have not enabled anything besides HTTP, HTTPS, DNS and DHCP.. so probably that's the reason.. I'll have a look in the evening.. at work.. ](*,) 

Cheers,
simpleUser]

---

