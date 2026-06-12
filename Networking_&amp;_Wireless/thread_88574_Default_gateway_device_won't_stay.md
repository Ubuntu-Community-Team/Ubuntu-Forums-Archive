---
title: "Default gateway device won't stay"
date: 2005-11-10
forum: Networking &amp; Wireless
---

### Post by boozie1580 on 2005-11-10
I am trying to set up my ethernet connection while running the 5.10 live CD. It is reading my ethernet card, and I set it to a DHCP connection and activated it. I can't access the internet, and I think the problem may be that eth0 (my ethernet card) is not selected as the default gateway device. This is because when I select it and press OK, the next time I go into Network Manager the default gateway device is blank again. Could this be the problem, and if so how would I fix it?

---

### Post by teaker1s on 2005-11-10
manually configure static ip and dns I've a similar problem

---

### Post by boozie1580 on 2005-11-10
I restarted with Windows, and wrote down the static ip, dns, and gateway information. I manually put that in for Ubuntu, activated it, and the disappearing default gateway problem went away. But, I still can't access the internet. I know the connection is fine b/c when I use Windows it works with no problem. I'm using a Marvell 4351 card on a Toshiba Satellite.

---

### Post by ssam on 2005-11-10
can you paste the output of the following commands here.

```
cat /etc/resolv.conf
```

```
ifconfig
```

```
route
```

```
cat /etc/network/interfaces
```

also try puting [http://216.239.57.99/](http://216.239.57.99/) into firefox. (this is googles ip address, a good way of checking if dns is broken)

---

### Post by boozie1580 on 2005-11-10
I tried pasting the IP address in Firefox, wouldn't come up. Also, how would I go about pasting the output of those commands on here, since I can't access this site from Ubuntu I can't think of any way to do it other than just writing it down and typing it in. (I'm on a different computer right now)

---

### Post by ssam on 2005-11-10
do you have a usb memory stick (what do people call them).

open a text editor on the live cd, and copy them into a document. then save that on the usb stick, and open on you other computer.

---

### Post by boozie1580 on 2005-11-10
First one didn't do anything.

```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:21:02:83
          inet addr:129.2.203.233  Bcast:129.2.255.255  Mask:255.255.0.0
          inet6 addr: fe80::2a0:d1ff:fe21:283/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:cc000000-0

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1531899 (1.4 MiB)  TX bytes:1531899 (1.4 MiB)

```

```
ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
129.2.0.0       *               255.255.0.0     U     0      0        0 eth0
default         129.2.203.1     0.0.0.0         UG    0      0        0 eth0

```

```
ubuntu@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet static
address 129.2.203.233
netmask 255.255.0.0
gateway 129.2.203.1

auto eth0
```

---

### Post by ssam on 2005-11-10
if
```
cat /etc/resolv.conf
```
gives no output that means that linux does not know where to look up ip addresses.

after putting the dns server data into the network control panel did you click ok and close the panel? i think it only write this data on exit.

---

### Post by boozie1580 on 2005-11-10
Yes, it's definitely saved in there.

---

### Post by ssam on 2005-11-10
ok. i recomend that you put the dns servers directly into /etc/resolve.conf

```
sudo gedit /etc/resolv.conf
```

and put in

```

nameserver 80.225.252.178
nameserver 80.225.252.186

```

but replace those ip address with the addresses of you isp's dns servers.

---

### Post by boozie1580 on 2005-11-10
What exactly do you mean by the address of the DNS servers??

---

### Post by boozie1580 on 2005-11-10
OK, I punched in the DNS Servers (I had 3, I found them in my network preferences while runnning windows). I ran GAIM to test the connection, and unlike before, when it would immediately tell me it couldn't connect, now it's just stuck on "Connecting...." for a long time, and then disconnected me (after about 2 minutes). An improvement I guess, because it seems like it's doing SOMETHING now. Any ideas for what to do now??

---

### Post by boozie1580 on 2005-11-10
I just tried the pinned troubleshooting thread. I tried the first test:

sudo mii-tool eth0

and got:

SIOCGMIIPHY on 'eth0' failed: Bad address

---

### Post by boozie1580 on 2005-11-11
Is the problem the fact that I'm using a DHCP server and I'm manually putting in the IP? Problem is, if I set it to DHCP in the network manager, the default gateway device starts clearing again.

---

### Post by slux on 2005-11-11
Are you able to ping your default gateway? The DNS servers? (ping <ip> in terminal).

Is the DHCP server in your personal control or set up by an isp or..? manually setting the details might be a problem if the ISP is dealing out the adresses.

You could just try adding the default gateway with "route add default gw <gateway ip>" after configuring with DHCP, if this works you can set up a dhclient.conf that specifies the gateway. The DHCP server might not be returning it properly. 

I wouldn't worry about the mii-tool output. Some network cards don't support it.

---

