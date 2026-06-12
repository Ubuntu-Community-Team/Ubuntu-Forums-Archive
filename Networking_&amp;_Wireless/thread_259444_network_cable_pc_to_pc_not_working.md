---
title: "network cable pc to pc not working"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by jd65pl on 2006-09-17
Hello I posted this thread in beginner already but think this may be a more appropriate place.

I have two pc's which are both linux, they network to each other fine over the router I have but i really need to just network them straight together. This doesn't seem to work when they are connected via cable.

I am using a crossover cable. one of the pc's has a wireless connection to the router which is networked and working. When using nmap I can see the IP's but i they computers can't ping each other. ssh login works on localhost and the IP of the ssh server but other computer cant find the server.

edit:

IP address info

PC number 1
Wireless connection eth1
IP: 192.168.1.64
Subnet: 255.255.255.0

Wired connection eth0
IP: 192.168.0.2
Subnet: 255.255.254.0

PC number 2
Wired Connection eth0
IP: 192.168.0.1
Subnet: 255.255.254.0

PC 1 is my ssh client and internet connection access
PC 2 is wired to my iternet connection and some external hard drives and is a SSH server

Thanks

J

---

### Post by nmaquet on 2006-09-17
are you sure the netmask for your wired ethernet network should not be 255.255.255.0 instead of 255.255.254.0 ???

---

### Post by jd65pl on 2006-09-17
I dont want any IP conflicts so I think it is ok.

---

### Post by nmaquet on 2006-09-17
can you post the output of 'sudo route' ?

---

### Post by jd65pl on 2006-09-17
Output of route

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1


This is the same for both computers.

If i enable the wired connection on the computer with both wifi and wired then my computer does not connect to the web through my wireless connection which is the only one available.

Thanks so far

J

---

### Post by jd65pl on 2006-09-18
Bump - I really need some help with this one

---

### Post by tbonius on 2006-09-18
If youre going NIC to NIC.. 

use a crossover cable.. not just a cat5/6 patch cable

Verify Dmesg output for the ehternet interface when plugging up the cable

Apply individual IP addresses withing the right range.. with a subnet mask.. but you dont need a default gateway.

example:  10.0.0.1/255.255.255.0 and 10.0.0.2/255.255.255.0

Since their is not DNS server.. be sure and either user a hosts file.. or setup DNS

thats it.. if you have issues from here.. start checking from both angles.. very bottom and very top.

Crossover cable - Software Firewall

Works for me 

T

---

