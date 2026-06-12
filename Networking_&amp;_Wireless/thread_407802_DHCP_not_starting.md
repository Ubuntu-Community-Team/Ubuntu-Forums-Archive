---
title: "DHCP not starting"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by leyse on 2007-04-12
I have been trying to get the 2Xthinclient to run on linux for about 3 weeks.  I started on SUSE and decided to move to Ubuntu 6.10 Desktop.  

I have a PC with 2 NICs. One external and one internal.  We are inside a school's network and already have a DHCP server, but we are trying to start up a thinclient server and so we need this PC to have a DHCP server just for the thinclient network.  So I'm trying to set up this DHCP server on the internal NIC.  

The external NIC's settings are 172.16.1.234  Bcast:172.16.3.255   Mask:255.255.252.0   It's gets it's info from the main DHCP server.  

I set the internal NIC up with 192.168.0.1   Bcast:192.168.0.255    Mask:255.255.255.0   

I know the external NIC works, cuz I can get internet access; however, the internal NIC I'm not sure about.  For some reason the DHCP3-server won't start up.  When I try it just says fail.  I followed [this guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_network_connections").  I don't know if I need to set up anything in the route tables.  I don't really want the clients to have internet access, only OpenOffice.  

I don't know what else to do and am getting aggravated.  

Thanks in advance. 

-Leyse

---

### Post by spd106 on 2007-04-13
Your set-up sounds ok, perhaps you should check that the internal interface is up and configured before the dhcp server is started. The /etc/network/interfaces file should be set to a static address with an auto line.

It also might be worth double checking the dhcpd.conf, maybe post it here if you are unsure.

I've not been to the ubuntuguide for a while, it certainly grown long... while still seeming to be too brief when it matters.

---

### Post by leyse on 2007-04-16
Thankyou for your help.  I found another problem.  eth0 is the internal and eth1 is the external.  If both are enabled, the internet doesn't work.  If i disable eth0, the internet will work.  Is there a way to set which interface the internet uses? 

Back to the original problem, the eth0 and eth1 lines read like this:

iface eth0 inet static
address 192.168.0.1
netmast 255.255.255.0
gateway 192.168.0.1

iface eth1 inet dhcp
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1

at the very bottom is a line that reads "auto eth0"

My dhcp.conf file looks like this:

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.200;
  option domain-name-servers 172.16.1.254;
  option domain-name "thin@accs.k12.in.us";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default - lease - time 600;
  max - lease - time 7200;
}

---

### Post by spd106 on 2007-04-16
Your eth0 stanza looks ok, except that you don't need a gateway, it _is_ the gateway.

Your eth1 stanza doesn't need any address, netmask or gateway. These will be obtained from the DHCP server.
I would seriously consider setting these to static if that's at all possible. You will have to talk to whoever controls the external network about the correct settings.

Two "auto" lines are needed if you want both interfaces to be brought up at boot, one for each interface.

The dhcp.conf looks ok.

Have you enabled NAT and port forwarding? You won't be able to share the Internet to the other PCs without doing that. There is a [router]("https://help.ubuntu.com/community/Router/") guide in the wiki or try the edubuntu wiki for a more holistic guide.

---

### Post by leyse on 2007-04-17
OK, I removed the gateway on eth0, changed eth1 to static and 172.16.1.234   255.255.252.0    172.16.1.254.  I also made sure there is an auto line for both interfaces.  

Again, the external network(internet) will work if i disable eth0, but won't work if both are enabled.  

And I still can't get the DHCP server to start.  Could I be missing some helper packages?

I don't want the clients on this network to have internet access, only programs like openoffice, so I don't think I need NAT and port forwarding.  

Anything else you can think of?  

Thanks so much for helping.

---

### Post by spd106 on 2007-04-17
For the Internet problem I suggest that you check the routing table for multiple default lines. This command will let you do that.
```
ip route
```

Did you follow this part of the guide [http://ubuntuguide.org/wiki/Ubuntu_Edgy#DHCP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#DHCP_Server)?
Particularly the bit about editing the /etc/default/dhcp3-server file.

---

### Post by leyse on 2007-04-17
Yes, I followed the guide.  I checked the syslog file and it said something like this:

"can't bind to dhcp address:  address already in use.  please make sure no other DHCP server is running and there is no entry for dhcp or bootp in /etc/inetd.conf.  Also check that you are not running JetAdmin"  

I did a search for bootp and jetadmin.  jetadmin returned nothing and bootp returned the dhcp3-server.  And there is no inetd.conf file.  I saw somewhere that the dhcp-server version is 3.0.4 and it is suppose to support multiple NICs.  

As far as the internet with the external NIC.  when I enable both and type ip route i get this. 

255.255.255.255 dev eth0  scope link
192.168.0.0/24 dev eth0 proto kernel  scope link  src 192.168.0.1
172.16.0.0/22 dev eth1 proto kernel  scope link  src 172.16.1.234
default via 172.16.1.254 dev eth1
default via 192.168.0.1 dev eth0 scope link

Does that tell you anything?

---

### Post by spd106 on 2007-04-17
You need to remove the second default route. If there is a gateway 192.168.0.1 line in the interfaces file then remove it. The first line in the routing table is rather weird, I wonder where that came from:confused:

---

### Post by leyse on 2007-04-17
i removed the 192.168 gateway, but can't find where to remove the default line.

---

### Post by spd106 on 2007-04-17
The routing table will be set right if you take the interfaces down then bring it back up or run ```
sudo ip route del default via 192.168.0.1 dev eth0
```

Have you run netstat to see if there is a service already running on port 67?

---

### Post by leyse on 2007-04-17
awesome, the internet works now with both interfaces enabled.  

But the DHCP server still won't start.  I tried netstat and didn't see 67 listed anywhere.  Is there a command to check specific ports?

---

### Post by leyse on 2007-04-18
If I go under networking tools and choose netstat is lists udp as running on port 67 with the ip source being 0.0.0.0.   Is that what's keeping it from running?  If so how do I shut that down?  I can't figure it out.  

Thanks

---

### Post by leyse on 2007-04-18
well, I don't know what happened,  I decided to restart it and it fired right up.  

Thanks for all your help

---

