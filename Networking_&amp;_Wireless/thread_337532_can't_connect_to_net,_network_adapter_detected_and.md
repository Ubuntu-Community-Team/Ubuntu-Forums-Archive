---
title: "can't connect to net, network adapter detected and will connect to lan, but not adsl"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by goathunter on 2007-01-13
[solved]

hello. I am using an acer aspire 3000 and ubuntu 6.06 dapper.
can get dialup fine. my networkcard can share file with other computers fine, but will not connect to adsl with alcatel adsl + wlan t07aw router. 
I went into admin-networking and tried changing ip etc, pretty much everything i could but no result. Sometimes the computer will attemp to connect to a webpage or msn for a few seconds and give me a page not found message, and other times won't even try (like the cable is unpugged). I know its not a problem because my mates laptop running winxp connects fine with same router and cable. However it gets worse. 
After changing a few setting in th networking menu around a few time it now won't open. I click system-admin-networking, it loads for a few seconds then dissapeers. So now i can't even get into networking. dapper did detect my network card fine and and i can still share file between computers. The broadband was working fine the first time i used it about a week ago and then just decided it didn't want to work any more. Up until then I had changed nothing.
Any help would be appreciated.
Thank You for your time

---

### Post by apjone on 2007-01-13
> **goathunter said:**
> hello. I am using an acer aspire 3000 and ubuntu 6.06 dapper.
can get dialup fine. my networkcard can share file with other computers fine, but will not connect to adsl with alcatel adsl + wlan t07aw router. 
I went into admin-networking and tried changing ip etc, pretty much everything i could but no result. Sometimes the computer will attemp to connect to a webpage or msn for a few seconds and give me a page not found message, and other times won't even try (like the cable is unpugged). I know its not a problem because my mates laptop running winxp connects fine with same router and cable. However it gets worse. 
After changing a few setting in th networking menu around a few time it now won't open. I click system-admin-networking, it loads for a few seconds then dissapeers. So now i can't even get into networking. dapper did detect my network card fine and and i can still share file between computers. The broadband was working fine the first time i used it about a week ago and then just decided it didn't want to work any more. Up until then I had changed nothing.
Any help would be appreciated.
Thank You for your time


can you post the following files.

/etc/network/interfaces 
/etc/resolv.conf

With linux you are better having a static IP address. Also sometimes you need to tell linux the address of your dns servers.

example.

root@ichigo:~# cat /etc/network/interfaces 
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.6
netmask 255.255.255.0
gateway 192.168.1.1
```

root@ichigo:~# cat /etc/resolv.conf 
```
search MY.DOMAIN
nameserver 158.152.1.58
nameserver 158.152.1.42
```

---

### Post by goathunter on 2007-01-13
Thankyou for your reply.

/etc/network/interfaces  is as follows

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface ppp0 inet ppp
provider ppp0

iface eth1 inet dhcp


/etc/resolv.conf is an empty file, ie. when i open it its is just a blank page.


> With linux you are better having a static IP address. Also sometimes you need to tell linux the address of your dns servers.

example.

root@ichigo:~# cat /etc/network/interfaces 

Code:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.6
netmask 255.255.255.0
gateway 192.168.1.1root@ichigo:~# cat /etc/resolv.conf 

Code:
search MY.DOMAIN
nameserver 158.152.1.58
nameserver 158.152.1.42

sorry i'm not quite sure what your getting at here. I'm new to broadband used to using dialup. should i copy and paste this into the terminal? Or do i need the ips particular to my isp? would this mean i would have to change them whenever i use adsl in a different country or different isp?

thanks for your time and fast reply

---

### Post by apjone on 2007-01-13
i recommend setting the box to a static IP. On your routers config note down the DNS it use's. If you tel me the IP of your router i can write here how to set up static ip for u

---

### Post by gcordoba on 2007-01-13
hi, I got the a similar problem.
I am trying to connect a laptop (dell inspiron 6000) which has been set to have double OS.
Ubuntu detected the network card and it is detecting the incoming trafic.
I need to use DHCP as my broad band service require it.
I intalled ubuntu 6.06 as the only OS in this laptop (toshiba satelite pro) and it detected got the internet connection (DHCP) without problem.
This sounds to me as a firewall problem. However I can not undertant why (and of course how to solve) using Ubuntu as an unique OS Internet is working fine using the same network and Ubuntu is unable to use the network is used in a double OS (if this is the problem)
Plese, any idea?
Gustavo

---

### Post by apjone on 2007-01-13
> **gcordoba said:**
> hi, I got the a similar problem.
I am trying to connect a laptop (dell inspiron 6000) which has been set to have double OS.
Ubuntu detected the network card and it is detecting the incoming trafic.
I need to use DHCP as my broad band service require it.
I intalled ubuntu 6.06 as the only OS in this laptop (toshiba satelite pro) and it detected got the internet connection (DHCP) without problem.
This sounds to me as a firewall problem. However I can not undertant why (and of course how to solve) using Ubuntu as an unique OS Internet is working fine using the same network and Ubuntu is unable to use the network is used in a double OS (if this is the problem)
Plese, any idea?
Gustavo
 open a terminal
type: sudo gedit /etc/resolv.conf
and add 
nameserver dns server1 (IP address of your isp's primary dns)
nameserver dns server2 (IP address of your isp's secondary dns)

then save it.

---

### Post by goathunter on 2007-01-13
> **apjone said:**
> i recommend setting the box to a static IP. On your routers config note down the DNS it use's. If you tel me the IP of your router i can write here how to set up static ip for u

Thankyou for your reply.
sorry for sounding like a dumbass but how do i get onto the routers config? I'm using a windows laptop at the moment is there a way to find out the DNS from this pc? or do i need to get it from my isp?

thanks for your time

---

### Post by goathunter on 2007-01-14
Also is there anyway i can get the networking dialog box to open gain. At the moment when I go into system-admin networking it loads for a few seconds then quits. 

Thanks for your time

---

### Post by goathunter on 2007-01-16
Problem solved. I just loaded up the ubuntu live cd and connected that way. When i loaded up again without the live cd the internet was working sweet.

Cheers

---

### Post by Peter6218 on 2007-07-19
Glad you could get online. Tried everything yesterday running from the Live CD. No results at all. 

Now I'm cyrrently running two flavours of Windows and Xandros V3 Linux on the same machine with no connection problems at all.

Feisty simply refused to connect. Found the network card and apparently hooked up to the hub but would not access the modem attached to the hub. Other three have no problem whatever. Ideas?

---

