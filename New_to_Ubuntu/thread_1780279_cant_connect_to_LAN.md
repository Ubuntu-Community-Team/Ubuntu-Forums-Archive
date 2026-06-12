---
title: "cant connect to LAN"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by 007casper on 2011-06-11
I have a trouble connecting my laptop to LAN.

I have this linksys router that can only have one static IP address.  The server is hooked up to it to serve a public website.  I hooked up my laptop to the same router to have a LAN network between the laptop and the server.  However, laptop doesnt have any local connection at all.  It doesnt go online either.

the laptop's /etc/network/interfaces 
> 
auto lo
iface lo inet loopback


thinking of adding eth0
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

then
sudo service network start

would this work?

---

### Post by jtarin on 2011-06-11
Looks OK,(make a back up before changing) post your "route -n" before and after.
Maybe "sudo /etc/init.d/networking start" if your command doesn't seem to work.

---

### Post by 007casper on 2011-06-11
as a test I looked at my computers route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
165.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

how would you set it?

auto eth0
iface eth0 inet static
address 192.168.1.0 (destination)
netmask 255.255.255.0 (genmask)
broadcast 192.168.1.255
gateway 192.168.1.1 (gateway)

and then 
sudo /etc/init.d/networking start

is that right?

---

### Post by jtarin on 2011-06-11
Does your gateway match your router? Enter 192.168.1.1  in a browser and see if it is. You should get your router interface.

---

### Post by 007casper on 2011-06-11
I am just doing a test in a different location, so the IPs will be different set up in actual production.  I just want to make sure I place them properly.

Yes, I do see the router interface when I enter 192.168.1.1

---

### Post by jtarin on 2011-06-11
So let's see an "ifconfig" before you issue the network start command.

---

### Post by 007casper on 2011-06-11
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:2a:a0:5e:70:33  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe4e:7032/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17545070 (17.5 MB)  TX bytes:2514315 (2.5 MB)
          Interrupt:26 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52300 (52.3 KB)  TX bytes:52300 (52.3 KB)

```

---

### Post by jtarin on 2011-06-11
Try to start your network and see then what "ifconfig" says.

---

### Post by 007casper on 2011-06-13
under /etc/network/interface the laptop had
```
auto lo
iface lo inet loopback
```

then did route -n
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
it didnt print anything else besides that... so I did ifconfig

ifconfig
```

eth0   Link encap:Ethernet hWaddre 00:21:9b:eb:cc:73
       inet6 addr: fe80::221:9aee:fccb:ee73/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 B)  TX bytes:1368 (1.3KB)
       Interrupt:16


lo    Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436 Metric:1
      RX packets:12 errors:0 dropped:0 overruns:0 frame:0
      TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txquevuelen:0
      RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```


I changed it to```

auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1 
```

sudo /etc/init.d/networking start

ifconfig
```

eth0   Link encap:Ethernet hWaddre 00:21:9b:eb:cc:73
       inet addr:192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0
       inet6 addr: fe80::221:9aee:fccb:ee73/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       RX packets:1 errors:0 dropped:0 overruns:0 frame:0
       TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:60 (60.0 B)  TX bytes:3527 (3.5KB)
       Interrupt:16


lo    Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436 Metric:1
      RX packets:12 errors:0 dropped:0 overruns:0 frame:0
      TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txquevuelen:0
      RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

I couldnt connect to the internet.  However, I was able to reach to the router panel on 192.168.1.1.

The router is connected to the server and it has a assigned static IP.  The router has four ports, however I cant assign static IP to each port on the router.

I am assuming I should still be able to connect the laptop and go online though.  

Am I putting the wrong settings on /etc/network/interfaces?

Thank you.

---

