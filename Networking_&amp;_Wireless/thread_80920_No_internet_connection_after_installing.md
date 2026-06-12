---
title: "No internet connection after installing"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by Duffman2010 on 2005-10-23
I got no internet connection: ping [www.google.com](www.google.com) doesn't work. 
But I do can ping the dsl router: ping 192.168.1.1 works.
The dns looks right: resolv.conf contains the right ones.
What can it be?
NOTE: I do not have Xorg working, I need to fix my Internet connection before installing the NVIDIA drivers.

---

### Post by cwaldbieser on 2005-10-23
[QUOTE=Duffman2010]I got no internet connection: ping [www.google.com](www.google.com) doesn't work. 
But I do can ping the dsl router: ping 192.168.1.1 works.
The dns looks right: resolv.conf contains the right ones.
What can it be?
NOTE: I do not have Xorg working, I need to fix my Internet connection before installing the NVIDIA drivers.[/QUOTE]
Can you ping outside addresses by IP address?  If so, it must be some sort of DNS problem.  If not, maybe it is some sort of firewall or NAT issue with your router?

---

### Post by spd106 on 2005-10-23
If you can ping 64.233.183.99 (google) successfully, then you will know it's a dns problem. Are you using your router to forward dns requests, or are you querying your ISP's dns servers directly?

If the ping is unsuccessful, you are not connected. I would suggest you start at the router and double check it's working ok. Can you verify it work with another machine/windows dual boot.

---

### Post by MAZDA on 2005-10-23
I have nearly the same Problem with Breezy Badger after upgrading Hoary to Breezy Badger.

[http://ubuntuforums.org/showthread.php?p=438081#post438081](http://ubuntuforums.org/showthread.php?p=438081#post438081)

It would be great if someon can help me with this Issue.

Thanks in advance for your medicine.

---

### Post by gruepig on 2005-10-23
In addition to ping, traceroute is a good tool to use.  Try 'traceroute 64.233.183.99'.  This should show you not only whether that IP is accessible, but also which hops along the way are.  This will verify whether the problem is before/at your router or beyond.

Also, if the interface to your router supports it, try pinging something from your router (or from another computer behind your router) to verify that the problem is with your computer and not the router.

Network configuration is primarily in the file /etc/network/interfaces.  (DNS, as you point out, is in /etc/resolv.conf.) You can verify the existing IP configuration with 'ifconfig -a' and the existing routes with 'route -n' or 'netstat -rn'.  Since you can ping an IP on your local subnet, 'route -n' is a good thing to check.  For a typical setup, you should have two routes: one with a destination of your local subnet and one with a destination of 0.0.0.0; the latter is called your default route, and the gateway for your default route should be the IP address of your router.  To check whether you have any firewall rules, run 'sudo iptables -L'.

You can modify your network configuration in real time, or you can bring down the interface (e.g., 'sudo ifdown eth0' if your card is eth0), make changes to /etc/network/interfaces, and bring the interface back up (e.g., 'sudo ifup eth0').  The stanza for your ethernet card (eth0) probably should be:

```

auto eth0
iface eth0 inet dhcp

```

or, if you aren't using dhcp, something like this (your IPs may vary):

```

auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.1


```

or, if you're using wireless, something like:

```

auto eth0
iface eth0 inet dhcp
    wireless-mode managed
    wireless-essid MYWIRELESS
    wireless-key 00112233....

```

Good luck!

If you still need help, post the contents of your /etc/network/interfaces file.

---

### Post by MAZDA on 2005-10-24
Hello gruepig !

Thanks a lot for your very Helpfull and Informative Answer.

Here are my results to your Suggestion.

I have connected my ADSL-Modem-Router with my Notebook which has Windows Installed and opened the Opera Browser and typed there the adress of my router "192.168.1.1".
One possibility in the showed screen is to show the System Status of my Router.

The result is the following.
I have no problems to surf on the Internet by using Windows together with my ADSL Modem Router.
> 
System Status 
  	
System Name : 	
ZyNOS F/W Version: V3.40(IC.1) | 9/19/2002 	
DSL FW Version: Alcatel, Version 2.7.38	
Standard: Multi-Mode	
  	
 	
WAN Information: 
  	
IP Address: 83.79.92.232 	
IP Subnet Mask: 255.255.255.255 	
Default Gateway: MyISP 	
VPI/VCI: 8 / 35 	
  	
 	
LAN Information: 
  	
IP Address: 192.168.1.1
IP Subnet Mask: 255.255.255.248
DHCP: Server
DHCP Start IP: 192.168.1.2
DHCP Pool Size: 4

After this intermezzo i plug my other PC which has installed Ubuntu with the router and beginn to boot the later Ubuntu version hoary on my PC which work very well on this PC.

If i type there the following command
"route -n"
the result is the following

> Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.248 U 0 0 0 eth0
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0


the command "ping 64.233.183.99" does function in hoary without any problems.
> The ping time is allways about 37.5 ms

[B]In Breezy the hole thing looks the total oposide.
I don't have any Kernel IP routes and the command ping give the Error "Network is unreachable".
[/B]

The File /etc/resolv.conf under Breezy is the same like in hoary
There is no difference !

The File /etc/dhcp3/ is also the same.
Absolutley no difference between Hoary and Breezy

And the File /etc/network/interfaces
which is showed under Breezy is also the same.

**There are no diffrences between the Files under Hoary or Breezy !**

If i type the following command to shutdown the Network Card under breezy for reconfiguration of my etho card like you have said it.

ifdown eth0
then i recive the following error
> 
**ifdown: interface eth0 not configured**

the result of the command 
ifconfig -a is the following

> eth0	Link encap: Ethernet  HWaddr 00:10:87:B6:7B:D8
	BROADCAST MULTICAST MTU:1500 Metric: 1
	RX packets: 0 errors: 0 dropped: 0 overruns:0 frame:0
	TX packets:97  erros:0 dropped:0 overruns:0 carrier:44
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
	Interrupt:11 Base address: 0xf800

If i compare this result with other Posting here in this Forum
then i see that i don't have any IP adress
showed in the Output.

Other people have a  ip adress with a scope Link showed in there Output.

[http://ubuntuforums.org/showthread.php?t=81131&highlight=link+encap](http://ubuntuforums.org/showthread.php?t=81131&highlight=link+encap)

> eth0	Link encap: Ethernet  HWaddr 00:00:86:36:7B:78
	inet6 addr: fe80:200:86ff:fe36:7v78/64 Scope: link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
	RX packets: 0 errors: 0 dropped: 0 overruns:0 frame:0
	TX packets:97  erros:0 dropped:0 overruns:0 carrier:44
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 b) TX bytes:15672 (15.3 KiB)
	Interrupt:3 Base address: 0x300

Please Help !

---

### Post by MAZDA on 2005-10-24
One thing also

if i type the following command

ifup eth0

then i resive the following output
> 
Listening on LPF/eth0/.......
Sending on LPF/eth0/.......
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval ...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval ...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval ...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval ...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval ...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval ...
No  DHCPOFFERS recieved
No working leases in persistent database -sleeping

---

### Post by MAZDA on 2005-10-24
Strange Thing.

after the failed command 

> ifup eth0

i have typed the command

> ifdown eth0 
to shutdown the the Service only to proove if really has typed all right without any faults.

So i try once again the command
> ifup eth0

and for my surprice now the hole thing works :D 
**Yaba Daba Doooo**

After three Discovers
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval ...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval ...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval ...
i have recieved a DHCPOFFER and a DHCPREQUEST

DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67

The ping command
> ping 64.233.183.99
now works also without any problems under Breezy !

I will try now to reboot and look if the hole thing works now without any problems !

---

### Post by MAZDA on 2005-10-24
It does not look good !

After the rebooting if i type the following command
> "ping 64.233.183.99"

then i recive once again the error message
> "Network Unreachable"

if i type after this Error Message the command
> "ifup eth0"

and after this once again the ping command
> "ping 64.233.183.99"

then it works !

I belive that something is wrong with the Booting of Breezy Badger.
In the Boot output there is a line which looks as follow
> "Cleaning ifupdown [Ok]"

Could be that throug the booting of breezy the old settings are cleaned and there is no more a "ifup eth0" command somewhere in the BootScript ?

It would be great if somebody could help with this issue.
Thanks in advance.

P.S. for what is this ifupdown cleaning good ?

---

### Post by exile on 2005-11-09
has anyone found a solution to this problem yet?

I find I can only get assigned an ip address if I ifdown eth0, unplug the cat5 from the adsl router then plug it into another free port, then ifup eth0 - magically I get assigned an IP address and it's all good until I reboot again.

To get the network up after a reboot I follow the above procedure and just put it back into the original socket.

It's definately NOT a problem with the router or the cable. I have tested both independently.

Any suggestions would be greatfully received.

---

### Post by Lambert on 2005-11-22
When you first boot  before you bring up your interface run this command

```
route
```

post the output here.

Then go through your steps to bring up your internet connection and re-run the command route. 

Post that output here.

---

