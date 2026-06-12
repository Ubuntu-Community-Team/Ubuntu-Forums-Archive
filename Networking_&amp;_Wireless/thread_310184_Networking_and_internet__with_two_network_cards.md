---
title: "Networking and internet  with two network cards"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by Bill007 on 2006-11-30
My small but big question

I have a working server edgy 6.10 base system working well


What I now want is to be able to do is

Below
|
|
v

What I want to do is run a network thru and provide internet via 

eth1(static 192.168.2.100 )


internet card eth0 ( static 192.168.1.4 ) is cconnecting to the web and 


How do I route internet packets from eth0 to eth1

or is there a   bridge to connect network interfaces eth0 and eth1

Network settings

**sudo nano /etc/network/interfaces**

# The loopback network interface

auto lo eth0 eth1
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

iface eth1 inet static
address 192.168.2.100
netmask 255.255.255.0
broadcast 192.168.2.255
network 192.168.2.0

**root@production:/home/bill007# ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:E0:4C:E9:39:F7
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fee9:39f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6925723 (6.6 MiB)  TX bytes:12037454 (11.4 MiB)
          Interrupt:185 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:14:85:D5:18:6F
          inet addr:192.168.2.100  Bcast:192.168.2.100  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fed5:186f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:43398 (42.3 KiB)  TX bytes:1686 (1.6 KiB)
          Interrupt:193 Base address:0xc400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5588321 (5.3 MiB)  TX bytes:5588321 (5.3 MiB)

---

### Post by Abhi Kalyan on 2006-12-01
Yo buddy,
Been facing the same problem,
Lets just wait. We might get a solution.
Ill post in when and if i find a solution, You could do it too.
Thank you

---

### Post by Bill007 on 2006-12-01
Sweet I been thinking Im alone here 

 Not a lot of help on this topic Ive found

This is more of a challange now just so I can learn been two days on this ](*,)  

 still no closer

I will post if anyhting is useful Its tial and Error

How are you communicating to the server  

I am doing it Via Putty and webmin but not up to speed with webmin YET

BUT IT LOOKS LIKE IT CAN BE DONE 

you herd of NAT

---

### Post by Bill007 on 2006-12-01
I havent read this thru yet 

could be some clues here

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html")

Bill007

---

### Post by halfvolle melk on 2006-12-01
Make a file called /etc/init.d/iptables and make it look something like this
```
#!/bin/bash

# flush old rules
iptables -F

# Masquerade out eth0
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

# Disallow NEW and INVALID incoming or forwarded packets from ppp0.
iptables -A INPUT   -i eth1 -m state --state NEW,INVALID -j DROP
iptables -A FORWARD -i eth1 -m state --state NEW,INVALID -j DROP

# allow ssh ftp http https from everywhere
iptables -I INPUT -p tcp --destination-port 22  -j ACCEPT
iptables -I INPUT -p tcp --destination-port 21  -j ACCEPT
# proftpd poorten voor passive transfers achter een firewall
# zie ook /etc/proftpd.conf
iptables -I INPUT -p tcp --destination-port 60000:65000 -j ACCEPT
iptables -I INPUT -p tcp --destination-port 80  -j ACCEPT
iptables -I INPUT -p tcp --destination-port 443 -j ACCEPT
iptables -I INPUT -p tcp --destination-port 873 -j ACCEPT

# Teamspeak server
iptables -I INPUT -p udp --destination-port 8767 -j ACCEPT

# Teamspeak web interface
iptables -I INPUT -p tcp --destination-port 14534 -j ACCEPT

# Enemy territory
iptables -I INPUT -p udp --destination-port 27950 -j ACCEPT
iptables -I INPUT -p udp --destination-port 27951 -j ACCEPT
iptables -I INPUT -p udp --destination-port 27952 -j ACCEPT
iptables -I INPUT -p udp --destination-port 27960 -j ACCEPT
iptables -I INPUT -p udp --destination-port 27965 -j ACCEPT

# Turn on IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward
```
The first few rules are for routing, the rest are for making services available to the world. You may need to swap eth0 <-> eth1 in this script and offcourse take out all the stuff you don't need.

---

### Post by Bill007 on 2006-12-01
Looks good

Is this working for you right now 

And where did you find it 

Surely it cant be this easy

Bill007

---

### Post by Bill007 on 2006-12-01
How do we activate the script  so it becomes effective

Is there some way of starting it

also any clues as to how to set the ip configs on the Machines on the internal card  eg network 192.168.2.100 netmask 225.225.225.0
Gateway 192.168.?.?  Preferred dns 192.168.?.?

---

### Post by halfvolle melk on 2006-12-01
> Is this working for you right now
Yep.
> Surely it cant be this easy
You can make it as hard as you want to ;)
[http://www.netfilter.org/](http://www.netfilter.org/)
> How do we activate the script so it becomes effective 
 Is there some way of starting it
Make sure it's executable
```
sudo chmod +x /etc/init.d/iptables
```
Scripts in init.d will start at boot, but you can start the script manually like this
```
sudo /etc/init.d/iptables
```

On the server, this is what the back-end NIC config looks like
```
auto eth0
iface eth0 inet static
    address 10.1.1.1
    netmask 255.255.255.0
    network 10.1.1.1
```

---

### Post by Bill007 on 2006-12-01
Well its done the file saved

set the file to start at bootup 

Ihave a funny feeeling that the file /etc/init.d/iptables does'nt have permission to boot

Executing **/etc/init.d/iptables start**

/bin/sh: /etc/init.d/iptables: Permission denied

Enabling action iptables at boot time.



 I dont see the internet on eth1 only on eth0

Still no routing between interfaces eth0 (external got the net) eth1 (internal want the net) 

Any suggestions

---

### Post by Bill007 on 2006-12-01
just saw your last post we must have posted at the same time  Hey thanks this is awsome thanks so much for your help here

Kind Regards Bill007
[URL="http://newplymouthmotel.co.nz"]
Taranaki accommodation New Plymouth New Zealand[/URL]

---

### Post by Bill007 on 2006-12-01
Oh My God Respect to you

That is amazing as you said change around eth0 and eth1 and bulls eye 

You are brilliant you know that feeling you get as noobie who just finally got it  

Thats Me right now  thank you for taking me to the next level

I will be getting this saved and stowed away:p :p :p :p

---

### Post by halfvolle melk on 2006-12-01
You're welkome :)
> That is amazing as you said change around eth0 and eth1 and bulls eye
Yeah, that's because I've got it the non-logical way, something to do with the MAC adress and getting an IP-lease. And everyone started out as a noobie, you'll catch on!

---

### Post by Bill007 on 2006-12-01
sweet halfvolle melk;) 

I will endevour to hand on what has been learnt

Ive come along way and its people like you who help people like me stay with the challange  Im starting to like the command line more and more  and this forum

Over and out Bill007 one day

---

### Post by brookiemonsta on 2006-12-01
Hey Bill007,

 For beginners to routing on Linux I would recommend installing the firestarter program. It's a graphical firewall manager, which includes a wizard for configuring your computer as a router. It's very easy to use.

 If you do not have graphical access to your server (I think you mentioned accessing the server via putty) then I recommend investigating the firehol program ("sudo apt-get install firehol"). This makes routing really easy, but it does involve editing a text file to produce the exact effects that you want. Using firehol is FAR easier than using iptables etc. directly.

You can find information about how to configure firehol using the manpage once it's installed "man firehol.conf" or at the website [http://firehol.sourceforge.net/](http://firehol.sourceforge.net/)

 NB. If you are going to use firehol then you should also edit (as root) the /etc/sysctl.conf file by uncommenting the line that reads:
#net.ipv4.conf.default.forwarding=1

so you should end up with the line looking like this:
net.ipv4.conf.default.forwarding=1

Hope that helps.

---

