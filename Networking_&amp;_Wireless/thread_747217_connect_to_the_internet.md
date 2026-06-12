---
title: "connect to the internet"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by gwarguy on 2008-04-06
I did a search and saw a lot of posts about connecting to the internet but almost all of them deal with wireless connetivity problems. Ive tried going through the few regular modem posts and i have not been able to get my internet up and running. 

I have tried the sudo ifconfig eth0 /sudo ifconfig eth0 up to try and release and renew my ip and i had no luck. 

When i run dhclient i get a "No dhcpoffers recieved, No working leases in persitent database - sleeping"

when i do lspci i get
02.03.0 Ethernet controller: Realtek Semiconductor CO., ltd RTL-8139/8139c/8239 C+ (rev10)

Ive tried restarting my computer, ive turned off my computer and unplugged the modem and router. plugged the modem in then the router. I have 2 other computers and an xbox360 hooked up to the router and all 3 have connection to the internet so its not my modem/router configurations. 

when i run route i get the following "```
destination gateway genmask flags metric ref use iface

link-local  *  255.255.0.0  u 0 0 0 eth0
default  * 0.0.0.0 u 1000 0 0 eth0

```

when i run ifconfig i get
```

eth0    link encap: ethernet hwaddr 00.16.17:3A:89:23
inet6 add: feb80::216:17ff:fe3a:8923/64 Scope:Link
up broadcast running multicast mtu:1500metric:1
rx packets 0 errors 46 dropped 0 overruns)fram0
txpackets0errors0dropped0overruns 0 carrier0
collisions 0 txqeuelen:1000
rx bytes 0 tx bytes 0
interrupt: 20 base address:x2000

eth0:avah  link encap:ethernethwaddr 00:16:17:3A:89:23
inet addr 169.254.3.198 bcast 169.254.255.255 mask 255.255.0.0
up boadcast running multicast mtu:1500 metric:1
interrupt:20 base address 0x2000

lo   link encap:local Loopback
inet addr:127.0.0.1 mask:255.0.0.0
inet6 addr: ::1/128 scope:host
up loopback running mtu:16436 metric:1
rx packets 891errors:0 dropped 0 overrunns 0 frame:0
tx packets 891 errors 0 dropped 0 overrunns 0 frame 9
collisions 0 txqueulen 0
rxbytes68224(66.6kb)txytes68224(66.6kb)
```

when i ping 127.0.0.0.1 i get 10 packets transmitted, 10 packets recieved 0% packetloss, time 8997ms

Please excuse the typos, obviously i cant access this forum and so i couldnt copy paste so i had to hand type the info.

---

### Post by brian_p on 2008-04-06
> **gwarguy said:**
> 
I have tried the sudo ifconfig eth0 /sudo ifconfig eth0 up to try and release and renew my ip and i had no luck. 

When i run dhclient i get a "No dhcpoffers recieved, No working leases in persitent database - sleeping"

when i run ifconfig i get
```

eth0    link encap: ethernet hwaddr 00.16.17:3A:89:23
inet6 add: feb80::216:17ff:fe3a:8923/64 Scope:Link
up broadcast running multicast mtu:1500metric:1
rx packets 0 errors 46 dropped 0 overruns)fram0
txpackets0errors0dropped0overruns 0 carrier0
collisions 0 txqeuelen:1000
rx bytes 0 tx bytes 0
interrupt: 20 base address:x2000

```


I can tell you what your problem is (although it sounds as though you have a good idea yourself) but have no surefire solution. The machine is not being handed an IP. There should be an inet addr in the second line of ifconfig's output.

Have a go at

```
sudo /etc/init.d/networking restart
```

> Please excuse the typos, obviously i cant access this forum and so i couldnt copy paste so i had to hand type the info.

You have given a very full account of the problem. Hopefully we will solve it.

---

### Post by gwarguy on 2008-04-06
thanks for the tip bryan. i did the 
sudo/etc/init.d/networking restart
and it said "reconfiguring network interfaces... [ok]

when i right click on the two monitors in the task bar and go to connection information, it detects my interface (wired ethernet eth0)
but i ahve 0.0.0.0 for all the ip/mask/dns/etc

---

### Post by brian_p on 2008-04-06
> **gwarguy said:**
> thanks for the tip bryan. i did the 
sudo/etc/init.d/networking restart
and it said "reconfiguring network interfaces... [ok]

when i right click on the two monitors in the task bar and go to connection information, it detects my interface (wired ethernet eth0)
but i ahve 0.0.0.0 for all the ip/mask/dns/etc

Just to check: the ethernet cable is ok and any leds that should be on are on?

Let's try giving the interface a fixed IP.

Use a text editor to display /etc/network/interfaces. There is should be a line for the loopback network interface. Below this add

auto eth0
iface eth0 inet static
address 192.168.7.15
netmask 255.255.255.0
network 192.168.7.0
broadcast 192.168.7.255
gateway 192.168.7.1

and then change the 7s to match what your network is.

Run the previous command. And/or do

sudo ifdown eth0 followed by sudo ifup eth0.

---

### Post by gwarguy on 2008-04-06
> **brian_p said:**
> Just to check: the ethernet cable is ok and any leds that should be on are on?

Let's try giving the interface a fixed IP.

Use a text editor to display /etc/network/interfaces. There is should be a line for the loopback network interface. Below this add

auto eth0
iface eth0 inet static
address 192.168.7.15
netmask 255.255.255.0
network 192.168.7.0
broadcast 192.168.7.255
gateway 192.168.7.1

and then change the 7s to match what your network is.

Run the previous command. And/or do

sudo ifdown eth0 followed by sudo ifup eth0.

miss understood what you were saying ithought that the info above should already of been in the file. How do i find out what  numbers to replace the 7's with. ifconfig brings up nothing in the eth0 part and intheth0:avah  the numbers are no where near yours. instead of 192 i have 168 

If this doesnt make sense i apologize, im a total linux newbie so bear with me.

---

### Post by brian_p on 2008-04-06
> **gwarguy said:**
> miss understood what you were saying ithought that the info above should already of been in the file. How do i find out what  numbers to replace the 7's with. ifconfig brings up nothing in the eth0 part and intheth0:avah  the numbers are no where near yours. instead of 192 i have 168 

If this doesnt make sense i apologize, im a total linux newbie so bear with me.

You should be able to get it from the router or one of the other computers.

---

### Post by gwarguy on 2008-04-06
ok when i ipconfig my laptop i get this information

ip address 192.168.1.100
subnet mask 255.255.255.0
default gateway 192.168.1.1

so i edited my interfaces file to look like this

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.15
255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

saved and exited

did a ifconfig and the above information is listed next to eth0
so thats a start i guess
i did a sudo /etc/init.d/networking restart and it gave back this error

* Reconfiguring network interfaces...
grep: /etc/resolv.conf: no such file or directory

---

### Post by brian_p on 2008-04-06
> **gwarguy said:**
> ok when i ipconfig my laptop i get this information

ip address 192.168.1.100
subnet mask 255.255.255.0
default gateway 192.168.1.1

so i edited my interfaces file to look like this

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.15
255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

saved and exited

Just so you know, 192.168.1.15 could be anything that doesn't conflict with the IPs of the other machines. e.g 192.168.1.37

> did a ifconfig and the above information is listed next to eth0
so thats a start i guess
i did a sudo /etc/init.d/networking restart and it gave back this error

* Reconfiguring network interfaces...
grep: /etc/resolv.conf: no such file or directory

Mmm. That file has always existed on any machine I have worked with. It contains the nameserver IPs. It must have at least one in. You can get yours from your router.

Check:

```
less /etc/resolv.conf or ls /etc/resolv.conf
```

Really not there?

```
sudo nano /etc/resolv.conf
```

and put in the nameserver IPs on separate lines.

Before doing that, would you do

```
ping 192.168.1.15
```

and

```
ping 158.152.1.58
```

and tell us what you get.

---

### Post by gwarguy on 2008-04-07
did the two pings and i got a host unreachable both times

---

### Post by brian_p on 2008-04-08
> **gwarguy said:**
> did the two pings and i got a host unreachable both times

Sorry, I've just noticed:

The fourth line in the eth0 stanza should be

```
netmask 255.255.255.0
```

Then

```
sudo ifdown -v eth0
```

followed by

```
sudo ifup -v eth0
```

-v makes it verbose.

---

