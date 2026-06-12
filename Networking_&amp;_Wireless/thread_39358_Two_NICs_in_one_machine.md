---
title: "Two NICs in one machine"
date: 2005-06-04
forum: Networking &amp; Wireless
---

### Post by Scorper on 2005-06-04
I have an older (333mhz PII 192MB) machine that I want to be my firewall, webserver and ssh server and stuff like that. I currently have two (diffrent kind of) PCI network cards on it, one 3Com and one RealTek. I have the ADSL modem connected to the other card and the other card goes to my better comp via a crossover cable. The problem is that the internet stopped working when I installed the other nic, and I don't really know how to get two cards working. I did dmesg | grep eth and I got this: [http://www.rafb.net/paste/results/VfU0rp71.html](http://www.rafb.net/paste/results/VfU0rp71.html)

I've googled like hours now and all I can find is something about giving parameters like ether=0,0,eth1 to lilo but I'm running grub..

So what do I have to do to get both cards working??

---

### Post by n21roadie on 2005-06-04
I am also new to linux and prehaps my post , which would appear similiar to yours is worth a look 
[http://ubuntuforums.org/showthread.php?t=38735](http://ubuntuforums.org/showthread.php?t=38735)

---

### Post by Scorper on 2005-06-04
I've been testing with it for the whole day and it seems that no matter which card I use it doesnt get any dhcp offers from the adsl box. I'm not even sure if its sending dhcpdiscovers on the right address (255.255.255.255 port 67).

---

### Post by janrinok on 2005-06-04
If I may suggest, using dhcp might not be the easiest way to make the system work.  Create your own internal network using, say, 192.168.1.1 and 192.168.1.2.  Install shorewall - it has a specific set up for exactly the situation you are trying to create.  Once you have your firewall functioning then add the server etc.
  To set up each ethernet connected:

sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0 ifup
sudo ifconfig eth1 192.168.1.2 netmask 255.255.255.0 ifup

When you can ping your adsl modem from the firewall box or, better still, ping the outside world then you know that it is connected.  Download shorewall onto the firewall and follow the instructions,

Hope that this helps

Jan

---

### Post by Scorper on 2005-06-04
I'm trying to get an IP from the adsl box with dhcp, I dont think theres any other way than dhcp. The lan can have static ips, that doesnt matter.

The current problem is that neither one of the cards isnt receiving a dhcp offer from the adsl box.

---

### Post by janrinok on 2005-06-06
Scorper
Sorry if my advice wasn't quite what you were looking for.  What kind of ADSL modem have you got?  I use a D-Link DSL-504 and it is set to default to dhcp however, it can be made to use a fix IP.  It might be that yours is the same.  And with my modem once the ADSL is connected to my ISP nobody else cares what IP addresses I use.
Can your computer see the ADSL modem - can you ping it?
Can your computer with the 2 NICs see the other - again can you ping it?
If you connect your original computer directly to the ADSL modem does the internet connection restart?  If so, what are the settings on the working computer.  Once we have that, we can set about setting up your firewall/server to the correct values.  HTH Jan.

---

### Post by outoforder2day on 2005-06-06
On my cable line, if the modem is left on for a few days, it won't pass any more dhcp leases through for some reason.  Try unplugging the modem, then plugging it back in again.  To find out which ethernet interface is plugged in to that modem, use ethtool -p [INTERFACE].  It should blink the status LED on your ethernet card.  Only some cards support this, but it's worth a shot.
once you know which interface is the right one, you should be able to bind the dhclient to it.  Good luck.

---

### Post by az on 2005-06-06
Are you sure that when you put the second card in it became eth0?  Are you trying to configure the correct card?

What do you see in the networking tool?

also, post the output of 

sudo route

sudo ifconfig

---

### Post by tamsia on 2007-07-06
I am new to this forum, and to linux as well. 
 I am building a proxy server and i want to feed internet from one NIC, and set the other NIC as gateway for other PC to connect to the internet. Here is how I have set  /etc/network/interfaces:

eth0 address 216.226.x.x
        netmask 255.255.255.255
        gateway 216.226.x.x
        network 216.226.x.x
        dns    x.x.x.x
eth1 address 192.168.x.x
        netmask 255.255.240.x

I can browser ok on it. But for some reasons that I cant tell :(, i am unabel to ping eth1 IP from the same box. And when I connect eth1 to a switch, and connect a PC to the same switch( with LAN settings on the same subnet) I still can not ping the IP eth1 nor browse.

Please can some one help me accomplish this project.

Danke!!

---

### Post by darrenm on 2007-07-06
Can you post your /etc/network/interfaces file? I know you've put some of it above but can you post all of it?

---

### Post by tamsia on 2007-07-06
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 216.226.208.140
        netmask 255.255.255.0
        network 216.226.208.0
        broadcast 216.226.231.191
        gateway 216.226.208.1
        dns-nameservers 216.226.231.132; 216.226.231.134; 208.67.222.222
# For the VNP interface
iface eth1 inet static
        address 192.168.96.10
        netmask 255.255.255.0

---

### Post by tamsia on 2007-07-06
> **darrenm said:**
> Can you post your /etc/network/interfaces file? I know you've put some of it above but can you post all of it?


Here is how it looks like.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 216.226.208.140
        netmask 255.255.255.0
        network 216.226.208.0
        broadcast 216.226.231.191
        gateway 216.226.208.1
        dns-nameservers 216.226.231.132; 216.226.231.134; 208.67.222.222
# For the VNP interface
iface eth1 inet static
        address 192.168.96.10
        netmask 255.255.255.0

---

### Post by tamsia on 2007-07-06
Ahhh! now i can communicate accros( i.e. ping across);). I still can't get internet across to the PC. maybe I need to set a static route. But I siply dont know how to get arround this

Pls help me out.

root@xxxxx:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
216.226.208.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.240.0   U     0      0        0 eth1
0.0.0.0         216.226.208.1   0.0.0.0         UG    0      0        0 eth0

**And this is how ifconfig looks like:**

auto eth0
iface eth0 inet static
        address 216.226.208.140
        netmask 255.255.255.0
        network 216.226.208.0
        broadcast 216.226.231.191
        gateway 216.226.208.1
        dns-nameservers 216.226.231.132; 216.226.231.134; 208.67.222.222
# For the VNP interface
auto eth1
iface eth1 inet static
        address 192.168.0.10
        netmask 255.255.240.0
        dns-nameservers 216.226.231.132; 216.226.231.134; 208.67.222.222

---

### Post by darrenm on 2007-07-06
Have you ```
sudo bash
echo 1 > /proc/sys/net/ipv4/ip_forward
```?

If you are trying to forward traffic from one network to another (looks like you are) then you will need to masquerade the inside traffic out.

```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

Shorewall is a little easier if you're doing lots of firewall stuff and it makes a bit more sense of source NATing.

Basically when traffic comes from 192.168.0.50 the source IP is written into the packet, Linux leaves this traffic alone and just forwards it across the interfaces, your ADSL router then re-writes this with its own outside IP such as 23.24.25.26. The remote server responds back to 23.24.25.26 and your ADSL router remembers the source IP for that connection as 192.168.0.50 but the ADSL router doesn't have a route to that IP, only 216.226.208.0 so it doesnt have anywhere to send the traffic to.

So when you Source NAT the traffic comes from 192.168.0.50, Linux sees the traffic going across the interfaces and re-writes the traffic to come from 216.226.208.140 so your router knows where to send packets back to.

Make sense?

---

