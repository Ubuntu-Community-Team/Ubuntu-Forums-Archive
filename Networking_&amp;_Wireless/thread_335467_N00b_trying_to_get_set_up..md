---
title: "N00b trying to get set up."
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by dac10 on 2007-01-10
ive just got Ubuntu installed today and i must admit im completely new to Linux. im sure i can find my way around the OS ok and im planning on getting a few books, but in the mean time it would be very helpful if i could establish an internet connection. that way i can stay away from windows and find my feet on Ubuntu.

heres the symptoms;

i have a Dlink router with two computers attached via ethernet cables. both are windows based but obviously this one is going to be Linux. the downstairs (windows) machine is connected to the internet through firefox.

however when i open firefox on the Linux partition i get the "website not found" error message, it wont even connect to the routers IP address. when i connect to the router on the downstairs machine it displays that both computers are in fact connected.

now please dont start blaring commands and assuming i know which windows your on about cause im literally on my first day here.

thanks in advance,

---

### Post by renzokuken on 2007-01-10
Ok, in linux, ethernet connectins should be automatically detected. it may be a hardware problem.

go to System -> Administration -> Networking and see if your ethernet controller is listed (eth0 usually).

also, do you know the address of your d-link router? it is usually 192.168.1.1. if so, have you tried seeing if firefox will connect to that in linux (enter the routers address in the firefox address bar)

---

### Post by dac10 on 2007-01-10
> **renzokuken said:**
> Ok, in linux, ethernet connectins should be automatically detected. it may be a hardware problem.

go to System -> Administration -> Networking and see if your ethernet controller is listed (eth0 usually).

also, do you know the address of your d-link router? it is usually 192.168.1.1. if so, have you tried seeing if firefox will connect to that in linux (enter the routers address in the firefox address bar)

yes, thats probs as far as i got. both my ethernet ports are detected, and i tried connecting to the routers ip address but it still displayed the "not found" error.

---

### Post by renzokuken on 2007-01-10
what does the terminal give you when u run

```
ifconfig
```

(may have to put a 'sudo' in front, cant remember)

edit, also, you have two ethernet sockets on the same pc?

---

### Post by dac10 on 2007-01-10
> **renzokuken said:**
> what does the terminal give you when u run

```
ifconfig
```

(may have to put a 'sudo' in front, cant remember)

edit, also, you have two ethernet sockets on the same pc?

give me two ticks, got to reboot to the other OS. 

i have two built in Nvidia ethernet sockets yes, only one is connected.

---

### Post by dac10 on 2007-01-10
i typed in "sudo ipconfig" and "ipconfig" both gave errors.

---

### Post by renzokuken on 2007-01-10
could you post the errors in more detail?

---

### Post by dac10 on 2007-01-10
> **renzokuken said:**
> could you post the errors in more detail?

it just says command not found.

---

### Post by renzokuken on 2007-01-10
weird,

ifconfig works for me, lists the eth0 ip and other info

---

### Post by dac10 on 2007-01-10
> **renzokuken said:**
> weird,

ifconfig works for me, lists the eth0 ip and other info

it definately says command not found, i typed it into the terminal window in accesories. it had bash something then my name and the computers name on the left.

---

### Post by chatterbabies on 2007-01-10
you are typing ipconfig supposed to be ifconfig

---

### Post by dac10 on 2007-01-10
oops, my bad. sorry. 

heres what it says;

[IMG]http://i55.photobucket.com/albums/g133/dac_10/DSC00123.jpg[/IMG]

---

### Post by dac10 on 2007-01-10
could somebody please tell me what this means and what is should be doing next, i have no idea. thanks,

---

### Post by dac10 on 2007-01-11
im guessing it is displaying the status of both ethernet cards? is there anything else i should try next, cause im just getting nowhere. thanks,

---

### Post by el-sio on 2007-01-11
Hello, I will try to help you (but I am kind of new to ubuntu too :D )
the ifconfig gives you the physical address of your network interface, and should give you your IP address and such informations if you were connected to a network. for example I have :

```

eth0  Lien encap:Ethernet  HWaddr 00:11:24:8A:76:06  
          inet adr:221.115.74.226  Bcast:221.115.74.231  Masque:255.255.255.248
          adr inet6: fe80::211:24ff:fe8a:7606/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:31757 erreurs:0 :0 overruns:0 frame:0
          TX packets:13878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:42208918 (40.2 MiB) Octets transmis:1867913 (1.7 MiB)
          Interruption:41 Adresse de base:0x1000 
```

next, I do not know your configuration, but there are two choices : either, your router gives you the IP automatically via DHCP, either you chose an IP and enter the IP of your router as gateway.

you can do this through the network manager application or manually by editing the network interfaces files (/etc/iftab, /etc/network/interfaces, /etc/resolv.conf)  with your favourite text editor (assuming gnome desktop and gedint installed here) :

```
el-sio@rivendell:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:11:24:8a:76:06 arp 1
eth1 mac 00:11:24:9c:0b:0e arp 1


```

nothing to change here, but check that the HW address written here is the same than the one given by ifconfig...

then network intererffaces configuration :

```

gksudo gedit /etc/network/interfaces

```

and you should see something like this : 

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
```

the eth0 configuration is in the case of automatic IP retrieving through DHCP, the eth1 configuration is for static IP configuration (enter here the IP of your router as gateway)

then restart networking (sudo /etc/init.d/networking restart or a simple reboot should do) and try to test your network with the ping command :

first try to ping your own IP (if you entered one yourself)
then try to ping your router IP address
if all this works try to ping a website to see if you can resolve names (associate ggogle.com with an IP) like this :

```
el-sio@rivendell:~$ ping www.google.com
PING www.l.google.com (66.249.89.99) 56(84) bytes of data

```

if you get nothing at this step,  try to look the resolv.conf file and you should see something like this :

```
el-sio@rivendell:~$ cat /etc/resolv.conf 
search usen.ad.jp
nameserver 61.122.112.97
nameserver 61.122.112.1

```

If you have no name server written, you can try to add your nameserver (which you can check on one of your other machines) and retry to resolve.

I hope all this helped a little...
feel free to ask any other question.

---

