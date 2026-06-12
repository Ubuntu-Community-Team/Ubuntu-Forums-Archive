---
title: "Port Forwarding"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by Hovercat on 2010-11-06
I try to use this command on a Ubuntu PC acting as a router to forward port 80 through my netgear router to the destination PC.

This is my setup:

ISP -> ISP Modem(173.2.xxx.xxx) -> Ubuntu PC Acting as Router(Receives 173.2.xxx.xxx, broadcasts 192.168.0.1) -> Net Gear Router(192.168.1.1) - PCs (Target PC is 192.168.1.8 )

I ran this command in the PC acting as router:


```
iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to 192.168.1.8:80
```And then no PCs on my network can connect to the internet until I restart the Ubuntu PC.

Yes, the port is forwarded on the NetGear router.

Basically, I need to let incoming connections on the Ubuntu PC Acting As Router, and send them to 192.168.1.8. How can I do that?

---

### Post by Hovercat on 2010-11-06
Can someone help?

---

### Post by uRock on 2010-11-06
Please wait at least 24 hours before bumping your thread. It times time for the right person to see your thread.

Thank you for your patience,
uRock

---

### Post by CharlesA on 2010-11-06
Why are you using two devices that act like routers on the same network?

It makes troubleshooting and port forwarding (among other things) very difficult.

---

### Post by Hovercat on 2010-11-06
The one PC is to use as a firewall, the actual router I use is for wireless.

---

### Post by CharlesA on 2010-11-06
Most home routers have a built in firewall, so unless you are running a specific firewall appliance, such as a box running pfSense, you don't need a firewall in front of a firewall.

If you still want the ubuntu box to act as the router, you should be able to hook it up to the netgear on one of the switch ports (not WAN) and use the 192.168.0.x ip addresses.

That is assuming the ubuntu box is running DHCP.

---

### Post by Hovercat on 2010-11-06
> **CharlesA said:**
> Most home routers have a built in firewall, so unless you are running a specific firewall appliance, such as a box running pfSense, you don't need a firewall in front of a firewall.

If you still want the ubuntu box to act as the router, you should be able to hook it up to the netgear on one of the switch ports (not WAN) and use the 192.168.0.x ip addresses.

That is assuming the ubuntu box is running DHCP.

That made me think. I'll probably disable the DHCP service on the router and have the Ubuntu PC act as the DHCP server.

---

### Post by Hovercat on 2010-11-06
Disabling the DHCP on the router did not work.

---

### Post by CharlesA on 2010-11-06
> **Hovercat said:**
> Disabling the DHCP on the router did not work.
How do you mean? Do you have the router hooked up via the "WAN" port to the ubuntu box?

---

### Post by Hovercat on 2010-11-06
The Ethernet from the modem plugs into eth1 on the Ubuntu PC. The Ubuntu PC broadcasts 192.168.0.1 through eth4. The Router uses a DHCP server to assign IPs to connected computers.

The Ubuntu PC plugs into the router where a modem would normally plug in.

---

### Post by CharlesA on 2010-11-06
> **Hovercat said:**
> The Ethernet from the modem plugs into eth1 on the Ubuntu PC. The Ubuntu PC broadcasts 192.168.0.1 through eth4. The Router uses a DHCP server to assign IPs to connected computers.

The Ubuntu PC plugs into the router where a modem would normally plug in.

Ok.

You'd need to install dhcp3-server on the ubuntu box and turn off the DHCP server on the netgear router as well as plug the ubuntu box into one of the LAN ports on the netgear, not the WAN port.

---

### Post by Hovercat on 2010-11-06
Oh, I get it now.

I'm going to be using it like a network switch?

---

### Post by CharlesA on 2010-11-06
Yep, that's right.

---

### Post by Hovercat on 2010-11-07
root@NETWORK-SERVER:~# sudo /etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                           [fail]
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics. [fail]

Output if tail /var/log/syslog:

root@NETWORK-SERVER:~# tail /var/log/syslog
Nov  7 02:10:04 NETWORK-SERVER dhcpd: Wrote 0 leases to leases file.
Nov  7 02:10:04 NETWORK-SERVER dhcpd:
Nov  7 02:10:04 NETWORK-SERVER dhcpd: No subnet declaration for eth4 (192.168.0.1).
Nov  7 02:10:04 NETWORK-SERVER dhcpd: ** Ignoring requests on eth4.  If this is not what
Nov  7 02:10:04 NETWORK-SERVER dhcpd:    you want, please write a subnet declaration
Nov  7 02:10:04 NETWORK-SERVER dhcpd:    in your dhcpd.conf file for the network segment
Nov  7 02:10:04 NETWORK-SERVER dhcpd:    to which interface eth4 is attached. **
Nov  7 02:10:04 NETWORK-SERVER dhcpd:
Nov  7 02:10:04 NETWORK-SERVER dhcpd:
Nov  7 02:10:04 NETWORK-SERVER dhcpd: Not configured to listen on any interfaces!

---

### Post by CharlesA on 2010-11-07
You have to configure it first. :)

[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

---

### Post by geoffmcc on 2010-11-07
Give 

> 
iptables -A PREROUTING -t nat -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.1.8:80


and then 

> iptables -A INPUT -p tcp -m state --state NEW --dport 80 -i eth1 -j ACCEPT


a try. Thats what i used when my router broke and had to wait a week for a new one. I also only had one nic card in the box at the time so i had to use a virtual cable but
i forget how to do that. obviously change the eth to match your needs

---

### Post by Hovercat on 2010-11-07
> **geoffmcc said:**
> Give 



and then 



a try. Thats what i used when my router broke and had to wait a week for a new one. I also only had one nic card in the box at the time so i had to use a virtual cable but
i forget how to do that. obviously change the eth to match your needs

I changed it to eth4 because that's my broadcast eth.

However, after I run those, I still lose all port 80 connections, such as I can't visit websites, but I can still play online-based games such as Garry's Mod, Half-Life 2: Deathmatch, and Counter-Strike.

---

### Post by The Cog on 2010-11-07
You NAT rule looks too permissive to me. It'll nat all HTTP queries coming in that port. I know only the internet should be coming in that way, but my instinct would be to go by IP addresses rather than by interface:
> iptables -A PREROUTING -t nat -p tcp -d 173.2.xxx.xxx --dport 80 -j DNAT --to 192.168.1.8:80

---

### Post by Hovercat on 2010-11-07
Well, I still have my internet, but it's not connecting to the webserver.

Also, I eliminated the NetGear router, so now my setup is like this:


ISP -> Cable Modem -> Ubuntu PC As Router (Receives 173.2.xxx.xxx, broadcasts 192.168.0.1/255) -> NetWork Switch -> PCs/NetGear Router (For Wifi)

And the IP of the Webserver is now 192.168.0.173

---

### Post by Hovercat on 2010-11-09
I'm still having issues.

I tried this document:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Didn't work.

I tried 

iptables -A PREROUTING -t nat -i eth4 -p tcp --dport 27019 -j DNAT --to 192.168.0.173:27019 

 	 	 	 		 			 				iptables -A INPUT -p tcp -m state --state NEW --dport 27019 -i eth4 -j ACCEPT 			 		

for a different service, and [www.canyouseeme.org](www.canyouseeme.org) says: "Connection Refused"

---

### Post by toekneewood on 2010-11-09
This is a setup I have used in the past if the Ubuntu machine has 2 nics and is acting as an in line router.  Sorry if it is a bit long, but hopefully something here will help you.


Before we start the configuration steps you will need to configure both of your NIC's with a static IP *Server Static IP for &#8220;eth0&#8221; & &#8220;eth1&#8221; - /etc/network/interfaces*
```

==== This one is connected to the Internet ====
auto eth0
iface eth0 inet static
address 10.1.32.32
netmask 255.255.255.0
network 10.1.32.0
broadcast 10.1.32.255
gateway 10.1.32.254
 
==== This one is connected to a hub or switch ====
auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

```

List of DNS Servers - /etc/resolv.conf
```
 
# OPEN DNS
echo "nameserver 208.67.222.222" | sudo tee -a /etc/resolv.conf > /dev/null
echo "nameserver 208.67.222.220" | sudo tee -a /etc/resolv.conf > /dev/null

```

Client IP for "eth0"
This one is connected to the Hub or Switch. You will also need &#8220;nameserver 208.67.222.222&#8221; in the &#8221;/etc/resolv.conf&#8221;
```

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

Turn on ip forwarding in kernel. Open linux kernel configuration file (you must be a root user or use su - command to become a root user):
```

nano /etc/sysctl.conf
# Add/modify following line:
net.ipv4.ip_forward = 1
# Type the following to enable IP forward
echo 1 > /proc/sys/net/ipv4/ip_forward

```

Restart network
```

/etc/init.d/network restart
OR
service networking restart

```

Setup IP forwarding and Masquerading (to act as router), you need to use NAT option of iptables as follows (add following rules to your iptables shell script) :
```

iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface eth1 -j ACCEPT

```

You are done! Test it with ping or dig:
```

#From the router do a test ping to the gateway via "eth1"
ping -I eth1 10.1.32.254
# now try to ping a DNS Domain name
ping your-isp.com
dig yahoo.com

```

---

### Post by Hovercat on 2010-11-09
None of this is working.

Is there any simple way to send incoming port 80 connections from eth1 to 192.168.0.173?

---

### Post by CharlesA on 2010-11-09
You'd have to use the forwarding chain wouldn't you?

Any traffic on port 80 coming from eth1 goes to 192.168.0.173.

I don't know what the rules would look like, unfortunately.

---

### Post by Hovercat on 2010-11-09
Hmm, I'll look it up on Google.

---

### Post by CharlesA on 2010-11-09
Found this: [http://www.socialhacker.com/howtos/port_forwarding.php](http://www.socialhacker.com/howtos/port_forwarding.php)

---

### Post by Hovercat on 2010-11-09
It didn't work.

---

### Post by toekneewood on 2010-11-09
Has the Ubuntu box got 2 nics.  I have done this before with 2 nics but never with 1 nic so that the data has to go in and out of the same eth0

---

### Post by Hovercat on 2010-11-09
Yes, it has two NICs.

The one connected to the internet is eth1, the one that broadcasts is eth4.

Those are the only NICs.

---

### Post by CharlesA on 2010-11-09
Checked the iptables settings on my router and this is what it says for the forwarding chain:

```
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
[COLOR="Red"]ACCEPT     tcp  --  0.0.0.0/0            192.168.1.2         tcp dpt:22
ACCEPT     tcp  --  0.0.0.0/0            192.168.1.30        tcp dpt:22[/COLOR]

```

---

### Post by Hovercat on 2010-11-09
I found this via Google:

[http://wiki.kartbuilding.net/index.php/Iptables_forward](http://wiki.kartbuilding.net/index.php/Iptables_forward)

It worked! :D

---

### Post by CharlesA on 2010-11-09
Glad you got it working. Don't forget to mark the thread as solved from the Thread Tools menu. :)

---

### Post by Hovercat on 2010-11-09
Done.

Thanks for your time.

---

### Post by Hovercat on 2010-11-11
I have an issue with this port forwarding.

When someone connects, it logs their ip as 192.168.0.1 (which is the IP of the Ubuntu server acting as a router). 

Is there a way to get their actual IP?

---

### Post by CharlesA on 2010-11-11
So it shows the private IP in the apache logs?

---

### Post by Hovercat on 2010-11-11
Lets say the user's actual public IP is 1.1.1.1.

When they connect to my website, it will show as if their IP is 192.168.0.1, which is the IP if I typed in my address bar, it would open up the webserver on my "Router" if it had one on port 80.

I need it so my webserver logs 1.1.1.1 instead of 192.168.0.1.

---

### Post by Hovercat on 2010-11-11
Also, I'm trying to forward port 27019.

I used the method that said it worked, but I keep getting "Connection Refused" on canyouseeme.org.

---

### Post by dozycat on 2010-11-24
The rules explained here worked for me, I only needed to remember to permit not only the DNAT in prerouting table.

But also the answers of private network PC in the FORWARD table from and to the private PC. 2 additional rules.

---

