---
title: "I have leakage of data in computer. Who is doing this? How to stop it?"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by deki999 on 2007-01-14
When I'm not surfing, some proces is doing it by himself!!!
I recieve some data from 1 to 10 KBit/s.
A few min. = 1 Mb

how to block it ???
I do not want to pay it when I'm not using it!

in windows I used Zone alarm, who blocked network after few minutes (my settings).
how to do it in Ubuntu???
(I have cable modem....)

---

### Post by floke on 2007-01-14
You could download firestarter (firewall)

sudo apt-get install firestarter

Are you sure the data you're recieving isn't just your PC refreshing webpages etc. - if they are open although you might not be using them? (if that makes sense)

---

### Post by spd106 on 2007-01-14
Maybe try installing the Firestarter firewall, it's available through add/remove programs or in Synaptic. It starts on boot and has a notification tray icon for easy access to block Internet traffic.

Be aware that automatic updates is switched on by default, so when you have a net connection it will automatically go and search for new updates. If you want to switch this feature off (not advisable) then open System -> Admin -> Software Sources, go the internet updates tab and uncheck the automatic update box. You will now have to start the check manually, such as through Synaptic.

---

### Post by deki999 on 2007-01-14
I thing that it is not a refreshing of web pages.
if it is, how to stop it?
I also stoped automatic updates.
unchecked it !

traffic is going on every second...not stoping ever !!!

I installed firestarter & I'm trying it...

---

### Post by deki999 on 2007-01-14
not working !!!
any sugestions...???

---

### Post by spd106 on 2007-01-14
Have a read through [http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)
I suggest you enable the panel applet and click on it to lock the firewall when you want to stop activity.

---

### Post by deki999 on 2007-01-14
I know that!
read my first message, plz and help if you can.
thnks

---

### Post by kerry_s on 2007-01-14
How about you just add the network applet and disconnect when not in use.
I think its just your dial up connection keeping the link alive.

---

### Post by deki999 on 2007-01-14
> **kerry_s said:**
> How about you just add the network applet and disconnect when not in use.

I'm already doing it...

it's not dial up, it' cable!

guy's, can anybody help!

---

### Post by tagra123 on 2007-01-14
iptable is blocking unwanted traffic from the install of ubuntu -- so there are usually no worries.

I have wireless broadband internet (no cable to the house) and my lan router acts as the first firewall. 

Before the router I was getting a lot of this type of activity. Rest assured I'm sure its just unwanted traffice that iptable is safely blocking for you. The internet is a busy place and most likely this is just noise.

If you are worried about it  go to this site and run the tests.

[http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

I also have firestarted installed to make it easier than learning iptables. I believe firestarter works with the iptables directly.

---

### Post by deki999 on 2007-01-15
don't get me wrong!
I'm not afraid of viruses or something like that...
provider is collecting money from this leakage.
few minutes, one mega....

Isupose I have no other choice but to turn it of manually...
oh my God...

---

### Post by deki999 on 2007-01-21
ethereal is showing me activity of ARP packets!!!
constantly!!!
even when I'm not surfing

that is my problem.
can anybody help ???

---

### Post by IntuitiveNipple on 2007-01-21
ARP is used on Ethernet to find the **real** address of a network device's interface. This is what we know as the MAC address.

When a network device using, say, TCP/IP needs to send a packet of data to an IP address it  broadcasts an ARP query to get the MAC address of the next 'hop' on the route - the one that 'hosts' the IP address it is sending to.

Are these packets mostly incoming, outgoing, or balanced; from one device or several?

I see you're using Ethereal to snoop the traffic.

Can you post a *small* sample of the data its capturing here so we can see whats happening, and also explain how you are connected to the Internet:

Your network device, IP addresses, type of connection (ADSL/cable/modem/etc.), ISP, anything unusual or noteworthy about the Internet service you use, etc.

---

### Post by deki999 on 2007-01-21
on the site of the provider MAC of my cable modem is :_00:0f:21:d0:63:82_

with ifconfig I have following:

eth2      Link encap:Ethernet  HWaddr _00:0F:21:D0:63:83_
          inet addr:89.216.173.232  Bcast:89.216.173.255  Mask:255.255.254.0
          inet6 addr: fe80::20f:21ff:fed0:6383/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24973455 (23.8 MiB)  TX bytes:2145439 (2.0 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

so, MAC adresses are not the same?!?!?!
but my internet is working OK.
???!!!???

these packets are incoming 100%, that is the problem.
I'm paying it, and not using it !!!
I'm very new with Ethereal, and I wouldn't say I'm using it, but ...ok I'll try to send a small sample.

please help, this is my first Linux, and I don't want to stop using it because of this small problem.

can I change MAC?
what should I do?

---

### Post by RandomJoe on 2007-01-21
Are you sure you are actually paying for those?  If so, that's a heckuva scam the provider has going for them...

I have a cable connection too, and those ARP packets are just a fact of life.  They are broadcast packets, so you hear every one that happens on your segment of their network.  And I hear a LOT as well!  There are also a few other types of traffic that can commonly dump in, again all broadcast stuff looking for other systems.

You _shouldn't_ be paying for bandwidth like that, hopefully they only bill you for packets that actually contain your IP address.  But 'ifconfig' is showing _all_ traffic, including broadcast.  (In my case, I don't pay per-megabyte anyway, it's just a huge nuisance on my firewall and I have to be sure to filter them.)

One option you have is to get a cable/DSL router and use it - that will stop all the extraneous stuff from getting to your computer.  But it's still arriving - the router just drops it all instead of your computer.

The MAC addresses are different, because each device has its own.  It's fine (indeed necessary) that they be different.

---

### Post by deki999 on 2007-01-23
I found this command to stop network:
sudo ifdown eth0.
To start it again I use:
sudo ifup eth0.

It's working ok.
Can anybody tell me how to make first command to run it self every, let's say 10 minutes?

help

---

### Post by cilynx on 2007-01-23
Scheduled tasks are the domain of cron.  There's an alright tutorial here:

[http://www.tech-geeks.org/contrib/mdrone/cron&crontab-howto.htm](http://www.tech-geeks.org/contrib/mdrone/cron&crontab-howto.htm)

---

### Post by deki999 on 2007-01-25
I did it finally !!!

when I turn my PC on network is not on !!! (I put # in front of auto eth0 in **/etc/network/interfaces**)

I turn network on with this launcher: **sudo ifup eth0**

next I use crontab command ***/10 * * * * sudo ifdown eth0** to stop network every 10 minutes (can be changed, of course, 15 min., 20 min...).

if network is stopped and I want to surf more, I just click on luncher mentioned up there (on the desktop for example...), and in a few seconds there it is...

this is forced solution, but I'm satisfied for now.
anyway the problem is not solved. my opinnion is that provider should not charge me this gAR(P)bage,

---

### Post by IntuitiveNipple on 2007-01-25
How many Internet IP addresses do you have? In your **ifconfig** details it says:

eth2 Link encap:Ethernet HWaddr 00:0F:21: D0:63:83
inet addr:89.216.173.232 Bcast:89.216.173.255 **Mask:255.255.254.0**

That **mask** controls how many other IP addresses your PC can *see* and will respond to. If you only have one Internet IP address assigned by your ISP then I'd have expected that mask is set to 255.255.255.255. **254.0** means that your PC can potentially see and respond to 512 IP addresses.

I have 8 IPs ( a /29 range - mask 255.255.255.248 ), and they are arranged like this:

[list][*].0 - network 'class' base (the first IP of a class is the network address - can't be used by a device)
[*].1 - Internet router, DSL connected to ISP, Ethernet switch connected to my PCs
[*].2 - PC1 
[*].3 - PC1
[*].4 - PC2
[*].5 - PC3
[*].6 - PC4
[*].7 - the network 'class' broadcast address (can't be assigned to a device)
[/list]

You can change that mask by altering the settings in **/etc/network/interfaces**. If that interface is set to use DHCP then you need to alter the DHCP server's setttings because it looks as if it is issuing the wrong netmask. That could be down to your ISP.

I think, even with DHCP in use you can over-ride that by adding the mask setting into **/etc/network/interfaces**.

To check all the options and how to use them, read the manual **man interfaces**.

---

### Post by koenn on 2007-01-25
cyou can check whiat other computers servers your computer is connected with by running
```
netstat -n -t -u
```
or
```
netstat -t -u
```
(turn network back on as it was before).
That could help you figure out what's going.

Furthermore, you definitely should use a firewall if you don't already, as you are directly connected to the internet with a publicly accessible address.

---

### Post by deki999 on 2007-01-25
IntuitiveNipple  thanks for help.
I also thing that ISP is to blame.
I tried with man interfaces, but I acomplished nothing, because it is very complicated.
for me.

can you help me to make mask to be 255.255.255.255
I have only one PC.
what mask do I need?

_*this is my interfaces file*_

[B]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


iface eth0 inet dhcp
netmask 255.255.255.255
#auto eth0
[/B]

I put the netmask line, but it is doing nothing.
what to do??!!??

---

