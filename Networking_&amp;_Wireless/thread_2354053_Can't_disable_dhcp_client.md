---
title: "Can't disable dhcp client"
date: 2017-02-27
forum: Networking &amp; Wireless
---

### Post by mickpf on 2017-02-27
Hello,

I've installed ubuntu-16.04.1 (and all updates) on my utilite pro (armv7) and would like to configure eth0 with static ip.
I've uninstalled the packages ics-dhcp..., udhcpd. There are no more packages with dhclient installed.

The directory '/etc/network/interfaces.d' is empty.

At my first attempt I've created a file '/etc/network/interfaces.d/eth0.conf':

[INDENT][FONT=Lucida Console]# The primary network interface
auto eth0
iface eth0 inet static

address		192.168.0.5
gateway		192.168.0.1
netmask		255.255.255.0
network		192.168.0.0
broadcast	192.168.0.255
[/FONT][/INDENT]

and used the original file '/etc/network/interfaces':

[INDENT][FONT=Lucida Console]# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:

source-directory /etc/network/interfaces.d
[/FONT][/INDENT]

After reboot eth0 got an ip address from the dhcp pool!

I removed the file '/etc/network/interfaces.d/eth0.conf' and moved its content into the file '/etc/network/interfaces':

[INDENT][FONT=Lucida Console]# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:

# The primary network interface
auto eth0
iface eth0 inet static

address		192.168.0.5
gateway		192.168.0.1
netmask		255.255.255.0
network		192.168.0.0
broadcast	192.168.0.255

source-directory /etc/network/interfaces.d
[/FONT][/INDENT]

After reboot eth0 got an ip address from the dhcp pool again!

Command 'ifconfig eth0' displays:

[INDENT][FONT=Lucida Console]eth0      Link encap:Ethernet  HWaddr 00:01:c0:14:1d:75  
          inet addr:192.168.0.228  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a02:908:2424:4ca0:201:c0ff:fe14:1d75/64 Scope:Global
          inet6 addr: fe80::201:c0ff:fe14:1d75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST DYNAMIC  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19996 (19.9 KB)  TX bytes:21977 (21.9 KB)
[/FONT][/INDENT]


What do I wrong?
NetworkManager ist not installed!

Can somebody help me please?

Thanks in advance
Michael

---

### Post by chili555 on 2017-02-27
My automobile doesn't get good gas mileage so I painted it blue.

I get nervous when people start making wholesale, permanent and not easily reversible changes to the system without understanding the consequences. For example, my system still contains all the DHCP packages that you removed and yet it obediently uses the static IP I specified perfectly well.

Generally, a correctly set /etc/network/interfaces and a reboot is all that is required. Yours is not.

First, check the administration pages of the router to be sure that the selected address 192.168.0.5 is outside the pool used in the router for DHCP leases. Here is an example: [http://www.mathgamehouse.com/oldmgh/istorm/help/manual/images/linksys.gif](http://www.mathgamehouse.com/oldmgh/istorm/help/manual/images/linksys.gif) In the example, the DHCP pool extends from 192.168.1.100 to 192.168.1.149. If it isn't otherwise reserved, a static address of, in this example, 192.168.1.5 would work perfectly.

Next, I suggest that you amend your file to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address	192.168.0.5
netmask 255.255.255.0
gateway	192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8

```Reboot.

---

### Post by mickpf on 2017-02-28
Hello chili555,

> **chili555 said:**
> My automobile doesn't get good gas mileage so I painted it blue.

I get nervous when people start making wholesale, permanent and not easily reversible changes to the system without understanding the consequences. For example, my system still contains all the DHCP packages that you removed and yet it obediently uses the static IP I specified perfectly well.



You should believe me, if I'd say: I searched for all posts about this problem and read them before I wrote this thread.
I'm neither a forum newbie nor linux newbie!

> **chili555 said:**
> 
Generally, a correctly set /etc/network/interfaces and a reboot is all that is required. Yours is not.


After editing the file I've rebooted the system, even if I didn't write it in this thread. Sorry!
> **chili555 said:**
> 

First, check the administration pages of the router to be sure that the selected address 192.168.0.5 is outside the pool used in the router for DHCP leases. Here is an example: [http://www.mathgamehouse.com/oldmgh/istorm/help/manual/images/linksys.gif](http://www.mathgamehouse.com/oldmgh/istorm/help/manual/images/linksys.gif) In the example, the DHCP pool extends from 192.168.1.100 to 192.168.1.149. If it isn't otherwise reserved, a static address of, in this example, 192.168.1.5 would work perfectly.

The IP 192.168.0.5 is outside the DHCP pool (192.168.0.100 - 192.168.0.250). It is not reserved for any other devices.
I checked it also before writing this thread.
> **chili555 said:**
> 

Next, I suggest that you amend your file to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address	192.168.0.5
netmask 255.255.255.0
gateway	192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8

```Reboot.

I've forgotten the code for the loopback device!
I added it and restarted the box...

**[SIZE=3]...but nothing helps!!![/SIZE]**

I've also tried with an other static ip, which I successfully use with an other computer, turned it off before reusing its address.

Kind Regards,
Michael

---

### Post by mickpf on 2017-02-28
Only after reserving the ip 192.168.0.5 in my router (192.168.0.1) for its MAC work it now!

The problem is solved for me now, even if I don't understand why it is necessary to reserve it!
It was not required for other devices!

Kind Regards,
Michael

---

