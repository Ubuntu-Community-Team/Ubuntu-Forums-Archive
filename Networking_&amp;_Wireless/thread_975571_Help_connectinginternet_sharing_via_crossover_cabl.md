---
title: "Help connecting/internet sharing via crossover cable on mac/ubuntu"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by Dwiman89 on 2008-11-08
Hi, 
    I need help getting Internet sharing to work. I have a ubuntu 8.10 intrepid box and a mac osx 10.3.9. The Ubuntu Machine connects to the Internet via wireless. I want to use a crossover ethernet cable between the two to share the internet connection of the ubuntu box to the mac box. its my understanding that the new ubuntu 8.10 is supposed to easily allow multiple connections(wifi and ethernet) now. 

  I have the Mac set to static.
addresses are;
IP:     192.168.1.3
Subnet: 255.255.255.0
Router: 192.168.1.104

   I have the ubuntu box eth1 connection set;
IP:     192.168.1.104
subnet: 255.255.255.0
Gateway: 192.168.1.3

With these settings I cant even get a ping through from both sides and my wifi connection wont work. I have to restart the ubuntu box to get wifi working and it looses the eth1 settings.
 my ubuntu wifi connection is:
IP:        192.168.1.104
broadcast: 192.168.1.255
subnet:    255.255.255.0
Router:    192.168.1.1

I think maybe it could be that The wifi connection(wlan0) is DHCP, and the Ehternet connection(eth1) is Static, but to the best of my knoledge it has to be set this way...

 please help me.

Thank you.

---

### Post by helgman on 2008-11-08
The short version,

Change the network settings on the Mac to:

IP: 192.168.2.2
Subnet: 255.255.255.0
Router: 192.168.2.1

Change the wired network (eth1?) on the Ubuntu-machine to:

IP: 192.168.2.1
Subnet: 255.255.255.0

As you see, it should have NO router.

Keep wlan0 as it is.

Now try:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

Does it work?

Regards,
Helgman

---

### Post by Dwiman89 on 2008-11-08
Im able to ping both computers now with those settings. now how do I get file sharing and interent sharing to work? thank you.

---

### Post by Dwiman89 on 2008-11-08
IM trying to at least share my home folder on the ubuntu machine to the mac, but the mac wants a username, password, and workgroup... I never set any of that up....

I have enabled sharing on both computers. when I try to access the mac from the ubuntu box it says "unable to mount location, could not connect to host". any ideas?

---

### Post by helgman on 2008-11-09
As for file sharing ... I've never had the need to share files between my Mac and any Linux machine that way (I use scp for the few files I need to move). Maybe you should start a new thread about that.

Is the Internet sharing up and running?

Regards,
Helgman

---

### Post by Dwiman89 on 2008-11-09
Ive played with it a little, but im not really sure how to do that...

What should I do to get sharing up and running?

---

### Post by helgman on 2008-11-09
On the machine with the wireless, open a Terminal and:

```
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
sudo iptables -t nat -A POSTROUTING -o <interface pointing to the Internet> -j MASQUERADE
```

Then make sure that machine no 2 has valid DNS information (make sure that /etc/resolv.conf is the same on both machines).

The first command (echo) tells the computer that it's OK to forward traffic from one interface to another and the second tells it to put it's own IP address on every packet it forwards out onto the Internet (you can find more information about that here: [http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)).

If it's still not working, make sure that the computer connected to the Internet can surf the web and then post the output of:
```
ifconfig
route
```

from both machines and

```

cat /proc/sys/net/ipv4/ip_forward
```

from the one with the wireless.

Regards,
Helgman

---

### Post by Dwiman89 on 2008-11-09
The second command says bash(sudo iptables -t nat -A POSTROUTING -o <interface pointing to the Internet> -j MASQUERADE)

"bash: interface: No such file or directory"

I cnat find /etc/resolve.conf on the mac(its probabply obvious but im new to mac)

the output for ifconfig is:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:06:33:20  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe06:3320/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3407 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:476093 (476.0 KB)  TX bytes:401835 (401.8 KB)
          Interrupt:22 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:e0:18:f1:e8:42  
          inet6 addr: fe80::2e0:18ff:fef1:e842/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:1 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15020 (15.0 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84506 (84.5 KB)  TX bytes:84506 (84.5 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1c:df:24:bd:f1  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:dfff:fe24:bdf1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39844254 (39.8 MB)  TX bytes:9807399 (9.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-DF-24-BD-F1-64-66-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

the output for route is:route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     1      0        0 eth0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan1
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1 
```

And the output for:
cat /proc/sys/net/ipv4/ip_forward

```
1
```

I hope this helps. Do you need the info from the mac? I dont know how to get it to the computer connected to the internet unless I type it all manually....
```

```

---

### Post by helgman on 2008-11-10
> **Dwiman89 said:**
> The second command says bash(sudo iptables -t nat -A POSTROUTING -o <interface pointing to the Internet> -j MASQUERADE)

"bash: interface: No such file or directory"

Change <interface pointing to the Internet> to wlan1. The rest looks good ...

It's a bit strange that you can't find /etc/resolv.conf on the Mac ... I've got it on my Mac ...

Did changing the command help?

Regards,
Helgman

---

### Post by Dwiman89 on 2008-11-10
I still got this...
```
root@derrick-Hambone:/home/derrick# sudo echo 1 > /proc/sys/net/ipv4/ip_forward
root@derrick-Hambone:/home/derrick# sudo iptables -t nat -A POSTROUTING -o <wlan1> -j MASQUERADE
bash: wlan1: No such file or directory

```

how do I find "/etc/resolve.conf" on the mac? through finder? I have only had the mac for about 4 days, and I have never used mac before...

---

### Post by helgman on 2008-11-11
Not <wlan1>, just wlan1.

```
sudo iptables -t nat -A POSTROUTING -o wlan1 -j MASQUERADE
```

Ah ... I've only owned and used a Mac for about a month or two. Anyway ... go to the Applications-folder (in Finder) and in there you'll find a folder name "Utilities" (I think). In there you'll find the Terminal.

Regards,
Helgman

---

### Post by Dwiman89 on 2008-11-11
yeah, I found resolv.conf in terminal, but I dont know the command to open and read it. I tried "nano resolv.conf" but I guess nano doesnt work on mac...

also that command finally did work. what next?

---

### Post by helgman on 2008-11-12
Try ```
cat /etc/resolv.conf
``` in the terminal. The same thing will work in Ubuntu. That's just for DNS-settings. Both machines should probably use the same settings ...

Regards,
Helgman

---

### Post by Dwiman89 on 2008-11-12
yeah< i had to give it DNS information manually through network settings and give it DNS addresses. but the internet works now. thank you for you help.

---

### Post by Dwiman89 on 2008-11-12
nevermind... For some reason every time I reboot the linux box it looses all the settings, and I have to redo everything on the linux side... and idea what that could be?

---

### Post by helgman on 2008-11-13
Yeah, the settings I gave you was just to test the whole thing, to make sure it works without doing any real "changes".

You can edit /etc/sysctl.conf to make the /proc/sys ... persistent. Just uncomment the line that read ```
#net.ipv4.ip_forward=1
```(remove the #).

You can find more information about iptables at [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

There are a few helpful hints and tips there.

Regards,
Helgman

---

