---
title: "no internet"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by jason castro on 2010-01-19
I have just installed Ubuntu (latest version). newbie to Linux 
It seems that i can't get on the internet any help would be great...

---

### Post by J V on 2010-01-19
info info info, nothing without info! ISP, router, connection, lan? wan? what?

---

### Post by dirtrider1 on 2010-01-19
hello how are we supposed to know without any other info?

---

### Post by rlogan on 2010-01-19
Could you please let us know some more details.

Are you trying to access the net through ethernet or wireless? 
What type of internet connection are you using...adsl or 3g?
What type of PC do you have? Laptop or Desktop
Do you know the chipset for the networking?
Are you using a router or a modem and if so what type?

The more info you can give us the better we can help you

Cheers

Richard

---

### Post by pmlxuser on 2010-01-19
Guys be soft on this fella

the most important info is> **jason castro said:**
>  newbie to Linux 
...

just direct him/her on how to get help here

first my dear newbie is

1. you have to explain your problem in details, we are not there so we can't see for ourself your problem.
2. check on the compatibility list of the version of ubuntu you are using to see if there are any said issues about your kind of machine.

3. of course as everybody is saying no good description of problem no help /[ the help is for free so keep that in mind]

---

### Post by OptimusPrimeIsMyHero on 2010-01-19
Hello everybody!

I have the same problem as the thread starter: No internet after installing Ubuntu 9.10 Karmic Koala. It can not be the hardware because I could surf the web half an hour before installing it. (Running on XP though...)
My internet connection is via ADSL using LAN.
The funny thing is: I seem to be able to ping [www.google.ch](www.google.ch) without loss of packets... ?!
The computer is a HP Pavilion and is about four years old (2 GHz, 1 GB ram).
Everytime i connect the LAN-cable Ubuntu tells my I am connected but neither Firefox nor the packet manager work.

My guess is that it is a matter of settings. But where and what?

Thanks for your help!

Martin

---

### Post by shreepads on 2010-01-19
Silly question... Does the ADSL modem perform PPPoE login or did you do it from Windows XP earlier?

---

### Post by OptimusPrimeIsMyHero on 2010-01-19
Both login name and password are stored in the modem/router so that should not be the problem. I can use the internet with my other XP-laptop without doing anything except plug in the LAN-cable. The modem itself gets a dynamic IP from my ISP when switched on.

---

### Post by OptimusPrimeIsMyHero on 2010-01-19
Ok. I am back home now and can give some details:
Laptop: HP Pavilion dv4000
Modem: D-Link DSL-524T ADSL2/2+ Router
OS: Ubuntu 9.10 Karmic Koala
Browser: Firefox 3.5.3

I have read somewhere else that I should change my MTU settings. ([http://ubuntuforums.org/showthread.php?t=1373003&page=2](http://ubuntuforums.org/showthread.php?t=1373003&page=2))

My router has an MTU of 1492 so this should have done the trick? Wrong...

When I try to open a webpage in Firefox, it just loads without result. But it does not display the 'Server not found' message. (Which it does when loading without connection, being a good thing.)

---

### Post by dmillerct on 2010-01-19
> **OptimusPrimeIsMyHero said:**
> Ok. I am back home now and can give some details:
Laptop: HP Pavilion dv4000
Modem: D-Link DSL-524T ADSL2/2+ Router
OS: Ubuntu 9.10 Karmic Koala
Browser: Firefox 3.5.3

I have read somewhere else that I should change my MTU settings. ([http://ubuntuforums.org/showthread.php?t=1373003&page=2](http://ubuntuforums.org/showthread.php?t=1373003&page=2))

My router has an MTU of 1492 so this should have done the trick? Wrong...

When I try to open a webpage in Firefox, it just loads without result. But it does not display the 'Server not found' message. (Which it does when loading without connection, being a good thing.)

Can you type the following in a terminal and then paste the output here?

```
ifconfig
```

---

### Post by canthus13 on 2010-01-19
1492 should be fine.  Are you going wired or wireless?

--Me

---

### Post by Cabs21 on 2010-01-19
Did you try hard wiring to the internet thru a LAN cable and updating your Wireless drivers in the Hardware Drivers menu? 9 times out of 10 that is why you cant get a wireless card to work on ubuntu. Soon as you do this and reboot it should work. You need to be connected to the internet somehow (LAN) and you need to pick the correct drivers.

---

### Post by OptimusPrimeIsMyHero on 2010-01-19
martin@martin:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:df:d0:fa  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fedf:d0fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2018 (2.0 KB)  TX bytes:8923 (8.9 KB)
          Interrupt:20 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:15:00:4f:ff:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 Memory:c8206000-c8206fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by OptimusPrimeIsMyHero on 2010-01-19
> **canthus13 said:**
> 1492 should be fine.  Are you going wired or wireless?

--Me

Wired

---

### Post by OptimusPrimeIsMyHero on 2010-01-19
> **Cabs21 said:**
> Did you try hard wiring to the internet thru a LAN cable and updating your Wireless drivers in the Hardware Drivers menu? 9 times out of 10 that is why you cant get a wireless card to work on ubuntu. Soon as you do this and reboot it should work. You need to be connected to the internet somehow (LAN) and you need to pick the correct drivers.

It is by LAN-cable...

---

### Post by dmillerct on 2010-01-19
Disregard post got OPs problem confused with hijackers. :)

---

### Post by OptimusPrimeIsMyHero on 2010-01-19
I connect via cable. Why should there be a problem with not having a wireless connection?!

By the way:

martin@martin:~$ ping google.com
PING google.com (209.85.129.103) 56(84) bytes of data.
64 bytes from google.com (209.85.129.103): icmp_seq=1 ttl=53 time=14.0 ms
64 bytes from google.com (209.85.129.103): icmp_seq=2 ttl=53 time=13.8 ms
64 bytes from google.com (209.85.129.103): icmp_seq=3 ttl=53 time=13.1 ms
64 bytes from google.com (209.85.129.103): icmp_seq=4 ttl=53 time=13.0 ms
64 bytes from google.com (209.85.129.103): icmp_seq=5 ttl=53 time=13.1 ms
64 bytes from google.com (209.85.129.103): icmp_seq=6 ttl=53 time=13.1 ms
64 bytes from google.com (209.85.129.103): icmp_seq=7 ttl=53 time=13.3 ms
64 bytes from google.com (209.85.129.103): icmp_seq=8 ttl=53 time=12.8 ms
^C
--- google.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7009ms
rtt min/avg/max/mdev = 12.899/13.347/14.053/0.402 ms

It seems i can ping... Help?!

---

### Post by canthus13 on 2010-01-19
Hmm... Proxy settings, maybe...In firefox: Check edit > preferences > advanced > network. Click Settings in the connections box and make sure you have no proxy set.

--Me

---

### Post by OptimusPrimeIsMyHero on 2010-01-19
> **canthus13 said:**
> Hmm... Proxy settings, maybe...In firefox: Check edit > preferences > advanced > network. Click Settings in the connections box and make sure you have no proxy set.

--Me

Tried that already. Does not work...

---

### Post by Cabs21 on 2010-01-19
what does 

```
iwconfig
``` 

ouput??

---

### Post by OptimusPrimeIsMyHero on 2010-01-19
I think I have the problem cornered now. It seems to be an ipv6/DNS issue
When deactivating ipv6 in Firefox, I can at least browse the net...
In Firefox enter 'about:config' in the address bar, use 'ipv6' as filter and set the boolean to TRUE.

Synaptic Package Manager does not work yet however...

BUT: my /etc/resolv.conf file just states
# Generated by NetworkManager

Shouldn't there be more?

I hope this helps...

---

### Post by OptimusPrimeIsMyHero on 2010-01-19
Ok...

IT WORKS ! ! ! (Sorry for yelling but I am really relieved now :-D )

What I did: 

Concerning ipv6:
(from: [http://forum.fachinformatiker.de/linux-unix/132897-dns-probleme-ubuntu-9-10-debian-5-a.html](http://forum.fachinformatiker.de/linux-unix/132897-dns-probleme-ubuntu-9-10-debian-5-a.html)
and: [http://konstantin.filtschew.de/blog/2007/09/03/ipv6-unter-linux-debian-ubuntun-gentoo-redhat-deaktivieren/](http://konstantin.filtschew.de/blog/2007/09/03/ipv6-unter-linux-debian-ubuntun-gentoo-redhat-deaktivieren/)
German links, sorry...)

In Firefox:
Deactivated ipv6 as mentioned in my last post.

In /etc/hosts:
Enter 'sudo gedit /etc/hosts' in a terminal and uncomment the lines with 'ip6' in it in the file opened in gedit.
My file now looks as follows:

127.0.0.1    localhost
127.0.1.1    martin

# The following lines are desirable for IPv6 capable hosts
#::1     localhost ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

In /etc/modprobe.d/blacklist:
Enter 'sudo gedit /etc/modprobe.d/blacklist' in a terminal and add 'blacklist ipv6' at the end of the file opened in gedit.

Concerning issues with DNS:
I followed the instructions at: [http://ubuntuforums.org/archive/index.php/t-426073.html](http://ubuntuforums.org/archive/index.php/t-426073.html)


Firefox and Synaptic Package Manager work for me now but I take no responsibility for potential damage to your system because I am still a Linux noob...

Thanks everybody for helping!

Martin

---

