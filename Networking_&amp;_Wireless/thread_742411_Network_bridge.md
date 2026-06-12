---
title: "Network bridge"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by chrisdeeley on 2008-04-01
I've recently purchased a new laptop and i'm trying to setup a bridge so I can access my files from both my desktop computer and laptop.

The setup is as follows

wireless router ---- [COLOR="Red"]WIRELESS[/COLOR] -----> Ubuntu Server -------- [COLOR="Red"]ETHERNET[/COLOR] -------> Desktop PC

with my wireless laptop connecting directly to my router.

I'm trying to set the bridge up on my server so that the Desktop PC can connect to the router and vice versa. Mainly to save me buying a wireless adapter for my PC, although i'll probably give up and buy one in the end.

The commands I'm using to set the bridge up are as follows:

[I]iwconfig wlan0 essid XXXXXX channel 11 enc XXXXXXX
ifconfig eth0 0.0.0.0
ifconfig wlan0 0.0.0.0
brctl addbr bridge
brctl addif bridge wlan0
brctl addif bridge eth0
ifconfig bridge up
ifconfig bridge 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.255.255
route add default gateway 192.168.0.1[/I]

The devices all have fixed IP addresses, 192.168.0.1 for the router, 192.168.0.2 for the server and 192.168.0.21 for the desktop PC. The desktop PC is set to use 192.168.0.1 as its default gateway and DNS server. 

The problem is the server can ping and communicate with the router and the Desktop PC but the desktop PC cannot communicate with the router, only with the server. Is there something wrong in my config? or can this not be done?

---

### Post by prshah on 2008-04-01
> **chrisdeeley said:**
> The devices all have fixed IP addresses, 192.168.0.1 for the router, 192.168.0.2 for the server and 192.168.0.21 for the desktop PC. The desktop PC is set to use 192.168.0.1 as its default gateway and DNS server. 


A bridge acts as a link between TWO NETWORKS; in this case, your wireless (laptop, router, desktop) and wired (desktop, server). However, by giving BOTH networks the same "class" of IP address, I think you are headed for a ton of grief.

Why not assign a different subnet to your wired network; eg. 192.168.[color=red]2[/color].xxx? Then configure the eth0 on the server to use the same type of IP address, and THEN bridge?

---

### Post by andguent on 2008-04-01
> **chrisdeeley said:**
> 
[I]iwconfig wlan0 essid XXXXXX channel 11 enc XXXXXXX
ifconfig eth0 0.0.0.0
ifconfig wlan0 0.0.0.0
brctl addbr bridge
brctl addif bridge wlan0
brctl addif bridge eth0
ifconfig bridge up
ifconfig bridge 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.255.255
route add default gateway 192.168.0.1[/I]

The devices all have fixed IP addresses, 192.168.0.1 for the router, 192.168.0.2 for the server and 192.168.0.21 for the desktop PC. The desktop PC is set to use 192.168.0.1 as its default gateway and DNS server. 

This all looks correct. It sounds like the static settings are keeping things simple for now. The only change I would do above is adjusting the broadcast from 192.168.255.255 to 192.168.0.255. Between your netmask and your broadcast together, you should have a total of four 255's.

> **chrisdeeley said:**
> I've recently purchased a new laptop and i'm trying to setup a bridge so I can access my files from both my desktop computer and laptop.


Laptop? Lets focus on the desktop and the router connecting. If you are asking something about the laptop, I would recommend moving it to phase 2. This is of course, assuming I am understanding your question.

The ultimate fix to your problem may be doing this on your server as root:
**echo "1" > /proc/sys/net/ipv4/ip_forward**
or edit the line:
net.ipv4.conf.default.forwarding=1 within the file /etc/sysctl.conf


> A bridge acts as a link between TWO NETWORKS; in this case, your wireless (laptop, router, desktop) and wired (desktop, server). However, by giving BOTH networks the same "class" of IP address, I think you are headed for a ton of grief.

prshah you are thinking of a router. Bridges have the same IP on both sides, routers have different IPs on each side. Chris is on the right track.

---

### Post by kevdog on 2008-04-01
Do you need the broadcast statement?

Also wouldn't it be something like this:

brctl addbr br0
brctl addif br0 wlan0
brctl addif br0 eth0
ifconfig wlan0 0.0.0.0 promisc
ifconfig eth0 0.0.0.0 promisc
sudo ifconfig br0 192.168.0.2
sudo route add default gw 192.168.0.1

---

### Post by prshah on 2008-04-02
> **andguent said:**
> prshah you are thinking of a router. Bridges have the same IP on both sides, routers have different IPs on each side. Chris is on the right track.

No wonder that I have never gotten a friggin' bridge to work. There's no way to thank you twice, so you have to be satisfied with one.

---

### Post by andguent on 2008-04-02
> **prshah said:**
> No wonder that I have never gotten a friggin' bridge to work. There's no way to thank you twice, so you have to be satisfied with one.

You are very welcome.

I tried searching online for a good read on comparing bridges to routers. The few minutes I spent googling was in vain. This link here describes how to configure a bridge using shorewall. If you don't care about the config, then just look at the pictures.
[http://shorewall.net/3.0/NewBridge.html](http://shorewall.net/3.0/NewBridge.html)

**kevdog**: It is true that the broadcast is optional, however the netmask is not. Keeping the 'netmask 255.255.255.0' is extremely recommended. It may technically apply settings without the netmask being set, but if it does then some system is guessing what you want your netmask to be. If it guesses differently then the rest of your network it can cause a mess.

Basic IP addressing rules:
* All devices on a LAN should have the same netmask (this includes the INSIDE connection of a router, but NOT the OUTSIDE)
* Unless you know what you are doing, a netmask of 255.255.255.0 is best.
* If your netmask is 255.255.255.0, then the first three numbers (IE: 192.168.0.) need to be the same on all computers on your LAN. The last number in the IP address must be unique.

As far as I can tell, the OP had most of the above correct. Chris, any word?

---

### Post by kevdog on 2008-04-02
Yes a bridge works on stack layer 2 and hence only forwards packets according to MAC address, not IP address (which is layer 3 -- the layer routers direct traffic on).

---

### Post by paphko on 2008-04-09
I have *exactly* the same setup (wireless router, ubuntu server as a bridge, desktop pc, static IPs) and the same problem:

> **chrisdeeley said:**
> 
The problem is the server can ping and communicate with the router and the Desktop PC but the desktop PC cannot communicate with the router, only with the server. Is there something wrong in my config? or can this not be done?

As I understood it that would be the correct setup...
I have also enabled promisc mode, but nothing changed.

Did you get it working now?

---

### Post by kevdog on 2008-04-09
Im no expert, however it would seem the iptables need to be modified to allow passthrough.  Perhaps not, however that could be the reason, why the desktop pc cant get beyond the server.

---

### Post by andguent on 2008-04-09
> **andguent said:**
> 
The ultimate fix to your problem may be doing this on your server as root:
**echo "1" > /proc/sys/net/ipv4/ip_forward**
or edit the line:
net.ipv4.conf.default.forwarding=1 within the file /etc/sysctl.conf


paphko, were you able to try the above? Does that change anything for you?

---

### Post by paphko on 2008-04-09
> **andguent said:**
> paphko, were you able to try the above? Does that change anything for you?

I just tried that, but nothing changed :-(

---

### Post by andguent on 2008-04-09
.

---

### Post by timbobsteve on 2008-04-10
I was under the distinct impression that only certain types of wireless NIC supported bridging. Something to do with the firmware not wanting to route traffic when the MAC address is the same for sender and recipient.
There are onyl a few cards (mainly Lucent Chipsets) that support correct wireless bridging.

... of course, I would love to be proven wrong ;-)

---

### Post by paphko on 2008-04-10
> **timbobsteve said:**
> I was under the distinct impression that only certain types of wireless NIC supported bridging. Something to do with the firmware not wanting to route traffic when the MAC address is the same for sender and recipient.
There are onyl a few cards (mainly Lucent Chipsets) that support correct wireless bridging.

[HERE]("http://www.linux-foundation.org/en/Net:Bridge#It_doesn.27t_work_with_my_Wireless_card.21") you see some additional information about this topic. Btw, I'm using a [BELKIN USB ADAPTER]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=272959"), model F5D9050b..

I resigned... and I have set up a new subnet, routing works just fine. :-)

Thanks anyway for the help.

---

### Post by andguent on 2008-04-10
If you got it working, can you document what you did, or at least just post the configuration files you did most of your changes in? Thanks.

---

### Post by paphko on 2008-04-11
I *didn't* get the bridge working!

So I created a new subnet:

wireless router (192.168.0.1)
 |
(wlan0, 192.168.0.10; eth0, 192.168.1.10) ubuntu server
 |
(ethernet switch)
 |
Desktop PC (192.168.1.20)

You find plenty of [HOWTOs via google]("http://www.google.com/search?q=ubuntu+router+howto"). Btw, by setting the nameserver to 192.168.0.1 at the desktop PC, I am also able to access the 192.168.0.X computers :-)

---

