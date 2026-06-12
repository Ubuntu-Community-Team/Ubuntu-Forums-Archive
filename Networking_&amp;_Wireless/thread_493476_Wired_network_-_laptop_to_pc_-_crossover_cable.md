---
title: "Wired network - laptop to pc - crossover cable"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by mymumlovesme on 2007-07-05
Hi everyone,

   I am struggling to set up a connection via a crossover cable between a laptop running 5.10 and my desktop pc running 7.04. I have been playing around with system>admin>network/ network tools but can't get them to see each other. I have also tried setting up nfs but the tutorials I've tried to follow became much too complicated for my aching brain. 

Can this be made to work? I would like to be able to share files between the two machines and possibly get an internet connection for the laptop via the cable.

Thanks,
andy

---

### Post by KiloEleven on 2007-07-05
Did you try setting static IP addresses on the two interfaces on either end of the crossover cable (System-->Administration-->Networking)? If they are connected to each other, they will not be able to get a dynamic IP address, b/c there is no DHCP server. Try going into the properties of each interface and changing it from Dynamic to Static. Then assign a generic IP scheme, like 192.168.1.1 on one interface, and 192.168.1.2 on the other interface (subnet mask 255.255.255.0 for both, gateway address doesn't matter at this point). Then see if you can ping across the connection.

---

### Post by mymumlovesme on 2007-07-06
Thanks KiloEleven,

   I'll try it tonight when I get home from work and post the results.

andy

---

### Post by mymumlovesme on 2007-07-06
Ok, when I ping the laptop from the pc it says:

```
andy@sheba:~$ ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.213 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.137 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=0.100 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=64 time=0.165 ms
64 bytes from 192.168.1.2: icmp_seq=5 ttl=64 time=0.102 ms
64 bytes from 192.168.1.2: icmp_seq=6 ttl=64 time=0.115 ms
64 bytes from 192.168.1.2: icmp_seq=7 ttl=64 time=0.139 ms
64 bytes from 192.168.1.2: icmp_seq=8 ttl=64 time=0.123 ms
64 bytes from 192.168.1.2: icmp_seq=9 ttl=64 time=0.134 ms
64 bytes from 192.168.1.2: icmp_seq=10 ttl=64 time=0.120 ms
64 bytes from 192.168.1.2: icmp_seq=11 ttl=64 time=0.130 ms
64 bytes from 192.168.1.2: icmp_seq=12 ttl=64 time=0.125 ms
64 bytes from 192.168.1.2: icmp_seq=13 ttl=64 time=0.103 ms
64 bytes from 192.168.1.2: icmp_seq=14 ttl=64 time=0.121 ms
64 bytes from 192.168.1.2: icmp_seq=15 ttl=64 time=0.104 ms

--- 192.168.1.2 ping statistics ---
15 packets transmitted, 15 received, 0% packet loss, time 14002ms
rtt min/avg/max/mdev = 0.100/0.128/0.213/0.031 ms

```

and pinging the pc from the laptop produces the same results.

What do I need to do now?

andy

---

### Post by KiloEleven on 2007-07-06
Since you are able to ping from both machines, that means that basic network connectivity is present. Check out this link for help w/ sharing folders:

[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/]("http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/")

Hope this helps - I can look more into it when I get home from work. Might be a while tho, since I am in the middle of upgrading to Feisty :)

---

### Post by mymumlovesme on 2007-07-06
Thanks for your help, KiloEleven. I've got the shared folders set up and working beautifully. 

From what I have read, internet sharing via crossover cable seems to be a serious undertaking if it works at all. I may have to buy/ build a router after all.

andy

---

### Post by KiloEleven on 2007-07-06
Glad to hear the folder sharing is setup and working. For sharing the internet connection, you might want to check out firestarter: [http://www.fs-security.com/]("http://www.fs-security.com/")

To install:

```
sudo apt-get install firestarter
```

then run:

```
gksu firestarter
```

It has a GUI, and looks to be pretty straightforward. I just installed it, and that is about all the experience I have w/ it, but if you checked into it, I'm sure you could get some use out of it. During initial setup, you can set it up to bridge connections.

---

