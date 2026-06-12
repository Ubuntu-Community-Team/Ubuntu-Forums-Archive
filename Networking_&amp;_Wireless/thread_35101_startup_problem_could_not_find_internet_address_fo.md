---
title: "startup problem could not find internet address for"
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by sanman_nor on 2005-05-17
so I added a address to the network while tring to conect to a wireless network.
put in the wep key
and then restarted the comp cause I was not geting anywere online
it steted up and said
"could not find internet address for.
this will prevent gnome from opperating corectly
it may be possable to corect the problem by adding to the file etc/hosts
conect any way try again"

try again does nothing
I can not get in to networking it just wont open
so I can not edit them
I hooked up a lan cable and can get online, but I open network conections and click on configure and nothing happens, thinks for a second then nothing
synaptic package manager won't open neather wil other aplications
what should I do

ran ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:3F:92:97:56
          inet addr:192.168.1.201  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fe92:9756/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5326683 (5.0 MiB)  TX bytes:1238429 (1.1 MiB)
          Interrupt:17 Base address:0x3000

eth1      Link encap:Ethernet  HWaddr 00:02:2D:B3:50:E3
          inet6 addr: fe80::202:2dff:feb3:50e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:122 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2827757 (2.6 MiB)  TX bytes:2827757 (2.6 MiB)
route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by alastair on 2005-05-17
So, "eth0" is UP and all your routing is via eth0.

What is in /etc/hosts ?

Can you ping your router? (ping 192.168.1.1)

---

### Post by sanman_nor on 2005-05-17
I can ping the router 
eth0 is ethernet cable  I am having isues with wireless which started all this

etc/hosts contains the following info
127.0.0.1 localhost.localdomain localhost hampshire thenor 

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by alastair on 2005-05-17
Forget about wireless just now (this is the next hurdle to cross!). 

Not sure but try and add a line to /etc/hosts :

192.168.1.201   <hostname>

Assuming your IP address is 192.168.1.201.

---

### Post by sanman_nor on 2005-05-17
so how would I do that 
sudo cp /etc/host????
sudo gedit etc/host  
I want to make sure I know what I am doing before I screw it up lol

---

### Post by alastair on 2005-05-18
If you have graphics, then yes. Using "gedit" is fine.

If not, just :

cd /etc/
sudo echo "192.168.1.201 YOUR_HOSTNAME" >> hosts

Replace YOUR_HOSTNAME with your actual hostname.

The IP address is taken from the "ifconfig" output for the working ethernet interface eth0.

---

### Post by sanman_nor on 2005-05-18
where do I find the host name 
the file etc/hostname is an empty file

---

### Post by alastair on 2005-05-18
Typing "hostname" usually tells you that.

But ... what does "hampshire thenor" mean in your post above (for 127.0.0.1)? I assumed these were your hostname(s)?

---

### Post by sanman_nor on 2005-05-18
I type hostname and get nothing 
the file host name is empty when I look in it it has nothing

---

### Post by alastair on 2005-05-18
Then set one.

Put your hostname in the file /etc/hostname - edit it, or :

echo MYHOSTNAME > /etc/hostname

Also add to /etc/hosts (look at the IP address in "ifconfig") :

192.168.1.201 MYHOSTNAME

and check you can "ping" MYHOSTNAME i.e.

ping MYHOSTNAME

---

### Post by sanman_nor on 2005-05-18
thanks it works now 
I really thank you for your help

---

