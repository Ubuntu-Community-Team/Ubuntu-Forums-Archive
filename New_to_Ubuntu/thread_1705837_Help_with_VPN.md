---
title: "Help with VPN"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by djyoung4 on 2011-03-12
So I dont know where else to post this.  I have a [Netgear Prosafe VPN Firewall]("http://www.netgear.com/products/business/VPN-firewalls-appliances/wired-VPN-firewalls/FVS338.aspx") that I would like to hook to my custom box running Ubuntu 10.04 and be able to watch the movies that are on it when I am not at home.  The problem is I have no idea where to begin.  Any help is greatly appreciated

---

### Post by sandyd on 2011-03-12
> **djyoung4 said:**
> So I dont know where else to post this.  I have a [Netgear Prosafe VPN Firewall]("http://www.netgear.com/products/business/VPN-firewalls-appliances/wired-VPN-firewalls/FVS338.aspx") that I would like to hook to my custom box running Ubuntu 10.04 and be able to watch the movies that are on it when I am not at home.  The problem is I have no idea where to begin.  Any help is greatly appreciated
[http://www.shrew.net/support/wiki/HowtoNetgear](http://www.shrew.net/support/wiki/HowtoNetgear)

I used this guide to setup IPSec for my Cisco router, but it should work anyways. [http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc](http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc)

---

### Post by djyoung4 on 2011-03-12
> **sandyd said:**
> [http://www.shrew.net/support/wiki/HowtoNetgear](http://www.shrew.net/support/wiki/HowtoNetgear)

I used this guide to setup IPSec for my Cisco router, but it should work anyways. [http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc](http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc)
thank you sir.  they look like useful reads.  i had a cisco router but it was the wrong version and didn't support vpn.  highly annoying.  now i can get a wireless router to work with the prosafe vpn firewall.  also do you think i can get this to work with openvpn

---

### Post by sandyd on 2011-03-13
> **djyoung4 said:**
> thank you sir.  they look like useful reads.  i had a cisco router but it was the wrong version and didn't support vpn.  highly annoying.  now i can get a wireless router to work with the prosafe vpn firewall.  also do you think i can get this to work with openvpn
nope. Business routers only use IPSec.
That is, unless you setup your own OpenVPN server on a computer thats on the network.

---

### Post by djyoung4 on 2011-03-13
> **sandyd said:**
> nope. Business routers only use IPSec.
That is, unless you setup your own OpenVPN server on a computer thats on the network.
That sounds like a better idea.  Then I don't have to mess with any routers or this netgear box.  im a little frustrated.  I have a couple questions though.  Do I need to set up a domain name in order to set up an OpenVPN server or can I just use my external IP address

---

### Post by djyoung4 on 2011-03-13
any ideas or links?

---

### Post by sandyd on 2011-03-13
> **djyoung4 said:**
> That sounds like a better idea.  Then I don't have to mess with any routers or this netgear box.  im a little frustrated.  I have a couple questions though.  Do I need to set up a domain name in order to set up an OpenVPN server or can I just use my external IP address
just use external ip
Your probably going to have to map the port (whatever it is gonna be) to the server ip address using the router.

---

### Post by djyoung4 on 2011-03-13
> **sandyd said:**
> just use external ip
Your probably going to have to map the port (whatever it is gonna be) to the server ip address using the router.
ok I found [this site about setting up an openvpn server]("https://help.ubuntu.com/10.10/serverguide/C/openvpn.html").  It first told me to bridge the network using [this site.]("https://help.ubuntu.com/10.10/serverguide/C/network-configuration.html#bridging")  Everytime I try that though it cuts the connection to my server and deletes auto eth0.  
```
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```
heres what that site gives me for bridging and im assuming I set the ip's to static and then just put in the right ips.  the problem is when I did that I got no auto eth0 connection nor could I access the internet from the server.  any ideas?

---

### Post by djyoung4 on 2011-03-18
bump

---

### Post by vncoder on 2011-03-19
I have the same issue but on Ubuntu 10.10 and I have used these commands:
#brctl addbr br1
#brctl addif br1 eth1
 
After that my SSH connect got cut as well.

---

### Post by djyoung4 on 2011-03-19
> **vncoder said:**
> I have the same issue but on Ubuntu 10.10 and I have used these commands:
#brctl addbr br1
#brctl addif br1 eth1
 
After that my SSH connect got cut as well.
I just can't figure out which IP addresses to put in what fields.   Im sure if I get the right ones then it will work fine.  any help is appreciated

---

### Post by vncoder on 2011-03-21
You may want to read this page:
[http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge](http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge)
[FONT=monospace]
[/FONT]# ifconfig eth0 0.0.0.0[FONT=monospace]
[/FONT]# brctl addbr mybridge[FONT=monospace]
[/FONT]# brctl addif mybridge eth1
# dhclient mybridge

   I got the eth1 using static IP while the bridge using dynamic ip. 

   You should do this at the console or connect via eth0 if you have one.
   The only thing is mybridge got the IP but when I tried to ping the router/dhcp server - I get timeout. I've checked the route table and it does have correct default gateway.

---

### Post by djyoung4 on 2011-03-22
> **vncoder said:**
> You may want to read this page:
[http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge](http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge)
[FONT=monospace]
[/FONT]# ifconfig eth0 0.0.0.0[FONT=monospace]
[/FONT]# brctl addbr mybridge[FONT=monospace]
[/FONT]# brctl addif mybridge eth1
# dhclient mybridge

   I got the eth1 using static IP while the bridge using dynamic ip. 

   You should do this at the console or connect via eth0 if you have one.
   The only thing is mybridge got the IP but when I tried to ping the router/dhcp server - I get timeout. I've checked the route table and it does have correct default gateway.
Ok so I have only one box that is connected to eth0 (besides a couple xboxs). In the page you gave me it talks about multiple network cards.  I'm only using one though.  Sorry, I'm jst a bit confused

---

### Post by djyoung4 on 2011-03-28
any ideas

---

### Post by vncoder on 2011-03-29
This is my interface file.

I have two bridge interfaces - br0 and br1. I use them for virtualisation not for VPN. However it would be the same. I will run a firewall as a guest inside a ubuntu host. The firewall itself will also have it own bridges.

I still leave the old IP addresses for eth0 and eth1 on there but once the bridges are active, the IP addresses for eth0 and eth1 no longer active/needed.
I will remove the IP addresses later when I have a bit of time.
However, the configuration works.

If you do this, please make sure you are at the console because  eth0 and eth1 will go down when you restart the network.

I can connect to the bridges remotely without any issue. If you get disconnected then you may try to connect using the IP addresses of the bridges.




# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth1 br0 br1
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.0.7
        netmask 255.255.255.0
        network 192.168.0.0
        post-up iptables-restore < /etc/iptables.up.rules

iface eth1 inet static
        address 10.1.1.2
        netmask 255.255.255.0
        network 10.1.1.0

iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

iface br1 inet static
        address 10.1.1.10
        network 10.1.1.0
        netmask 255.255.255.0
        broadcast 10.1.1.255
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
        gateway 10.1.1.1

---

