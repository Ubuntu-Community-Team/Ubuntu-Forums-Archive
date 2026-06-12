---
title: "How do I create fast connection between two ubuntu machines?"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by jerseyman on 2007-05-22
Hi!

I have little network problem! I want create fast link between two ubuntu machines.
These two machines are linked together with five port switch (cannot configure it) and I have cable internet connection.

I have tried NFS and I have also tried setup an SSH-Sever. The problem is I can make this connection to work, but always when I'm downloading files I'll get only about 115 kbps. Should be more i think?

In my understanding this connection is always routing itself through the network and routers somehow.

How do I setup the link so that it will go direct through my switch, then it would be much faster???

Thanks for your help!

Jersey

---

### Post by hartz on 2007-05-22
On both those machines, please run these two commands:

```
ifconfig -a
netstat -rn
```

Please post the output of those two commands - I want to look at netmasks, default gateways and IP addresses to see if they are in fact in the same address range (network address)

When you transfer data between the two machines, do you use IP addresses or host-names?  What are the exact values?

The best way to test raw network performance is with FTP,  so please isntall an FTP server on one of the hosts.  We will do some FTP transfers from /dev/zero on one machine to /dev/null on the other.  FTP is also not particularly CPU heavy (unlike ssh for example).

---

### Post by jerseyman on 2007-05-23
Hi!

I use hostnames when transfering files between hosts
.
This is the output from client.

ifconfig -a
> eth0      Link encap:Ethernet  HWaddr 
          inet addr:  Bcast:  Mask:
          inet6 addr:  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:977724 (954.8 KiB)  TX bytes:166675 (162.7 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1032 (1.0 KiB)  TX bytes:1032 (1.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


netstat -rn
> Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
     0.0.0.0            U         0 0          0 eth0
0.0.0.0              0.0.0.0         UG        0 0          0 eth0


This is the output from server

ifconfig -a
> eth0      Link encap:Ethernet  HWaddr   
          inet addr:  Bcast:  Mask:
          inet6 addr:  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:592176 (578.2 KiB)  TX bytes:31211 (30.4 KiB)
          Interrupt:193 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ra0       Link encap:Ethernet  HWaddr   
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xc000 

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



netstat -rm
> Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
     0.0.0.0            U         0 0          0 eth0
0.0.0.0              0.0.0.0         UG        0 0          0 eth0


Thanks for your help!

jersey

---

### Post by hartz on 2007-05-23
The IP addresses are on different networks (With network I mean the TCP/IP meaning, not the cabling meaning)

Where did you get these IP addresses from?

There are a number of ways to force these machines to talk to one another without going via the router.

1. Static ARP entries
2. Point-to-point (host) routing entries
3. Multi-homing one of the machines (Extra IP on existing subnet)
4. Change the IP, netmask and default gateway of one of the machines

Nr 4 is the cleanest solution, but may break existing things (that I why I asked where did the IP addresses come from)

Nr 1 is possibly oyur only option if you are using DHCP.

There is actually a 5th possibility.  multi-home both machines using 192.168 addresses.

All of the above methods still depend on one other consideration.  You need to change the way the name resolves, or you need to create new aliases for "different" addresses allocated as entries in your /etc/hosts file.

---

### Post by jerseyman on 2007-05-23
Hi!

I'm using DHCP, so these addresses are given automaticly from my ISP (Cable network). I dont know if it is possible change these ip-addresses? What is the meaning of my stupid five post swich, maybe thats the problem? In the first place I was just wondering that my swich could route the traffic directly.

Conglusion, I have learn more about Unix/Linux networking, maybe then someday I'll get things working in the way that I want.

Thanks for your help!

jersey

---

### Post by hartz on 2007-05-23
OK, here goes solution nr 5.

Lets assume your computers are named as follow
server: computera 
client: computerb

currently computera has got IP address XX.XX.XX.XX on eth0.
currently computerb has got IP address ZZ.ZZ.ZZ.ZZ on its eth0

We will create a new virtual network with no routing, just linking the two systems to one another.

This virtual network will use the Private IP range, 192.168.*.*

run this on computera:
```
sudo ifconfig etc add 192.168.10.5
sudo ifconfig eth0:0 netmask 255.255.255.0
```


run this on computerb:
```
sudo ifconfig eth0 add 192.168.10.6
sudo ifconfig eth0:0 netmask 255.255.255.0
```

You can test the throughput now using the following:

On the server install and run an FTP server (pick your poison from Synaptic.  I personally like the pure-ftpd package.)  Then make an FTP connection from the client to the server using the 192.168 IP address, using a CLI ftp client, like this
```
ftp 192.168.10.5
```

Log in into the server with any user login ID and password.  Then enter this command:
```
put "| dd if=/dev/zero bs=32k count=16384" /dev/null
```

If the test completes too quickly you can set the count to 163840, though I doubt that it will - it takes a good few seconds on a gigabit network.

Once the test completes, it will print some statistics.  Please can you post that here.

---

### Post by jerseyman on 2007-05-24
Hi!

Now I'm happy, it's working just like I wanted. I was just so stupid that i didn't understand that I have to create a private network to use these things. It's allways nice to learn new things and linux/ubuntu are great to have!

Thanks very much for your help!

Here are the results from the network test now. It was about 115 kbps and now it is:
> ftp> put "| dd if=/dev/zero bs=32k count=16384" /dev/null
local: | dd if=/dev/zero bs=32k count=16384 remote: /dev/null
200 PORT command successful. Consider using PASV.
150 Ok to send data.
16384+0 records in
16384+0 records out
536870912 bytes (537 MB) copied, 45.6486 seconds, 11.8 MB/s
226 File receive OK.
536870912 bytes sent in 46.11 secs (11369.7 kB/s)


Jersey

---

### Post by jerseyman on 2007-05-24
Hi!

I have still one problem. When I create this private network and configure these ip addresses and netmasks things are working fine. But when I reboot the machine I have to do these configurations allover again. How do I make them stay after reboot? Is there some text file where I can input them manually?

Thanks

Jersey

---

### Post by jerseyman on 2007-05-24
Hi! I have solved the problem.

I added these configuration in /etc/network/interfaces.
Now they stay after reboot.

Thanks

jersey

---

### Post by hartz on 2007-05-24
Good.  You still need to make it permanent (Those settings will be lost on a reboot)

I am uncertain how to add a fixed IP to an interface that is primarily DHCP, without buggering up the DHCP interface (which is what is giving you internet access in the first place).  This I will have to investigate.  I'll come back to you.

---

