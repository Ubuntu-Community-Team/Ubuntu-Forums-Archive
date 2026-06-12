---
title: "[SOLVED] Routing for VPN? What does NetworkManager do that I'm not doing?"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by rrwo on 2008-03-31
I am able to connect to a VPN using Gnome NetworkManager.  However, for various reasons I do not want to use NetworkManager, so I'd like to set it up manually.

I have the following script in /etc/ppp/peers/myvpn (with IP address and usename etc, changed and appropriate entry for myvpn in chap-secrets):
```
pty "pptp vpn.example.com --nolaunchpppd"
name username
remotename myvpn
linkname myvpn
file /etc/ppp/options.pptp
require-mppe-128
usepeerdns
```
When I use "sudo pon myvpn" it creates the ppp0 interface, according to ifconfig.  So I know it's connecting in some way to the vpn server.

Next I change the routing:
```
sudo ip route replace 169.254.1.10 dev eth0 via 192.168.1.1
sudo ip route replace default dev ppp0

```where 169.254.1.10 is the ip address of vpn.example.com (the real address is a different address which is publicly accessible over the internet) and 196.168.1.1 is the default gateway for my router.

When I run ip route" I get the following:
```
169.254.1.10 via 196.168.1.1 dev eth0 
196.168.1.0/24 dev eth0  proto kernel  scope link  src 196.168.1.1 
default dev ppp0  scope link 

```
which is exactly the same thing as when I use the VPN through NetworkManager.

But the routing doesn't work when I run the VPN manually. Name lookups don't work (even though /etc/resolve.conf is set properly), nor can I access any machines.

So I'm wondering what NetworkManager does when setting up the VPN that I'm not doing.  From all of the PPTP HOWTOs that I've found online, I can't figure out what else is going on.

---

### Post by koenn on 2008-03-31
with your vpn up, do a traceroute to an internet host (eg [www.google.com](www.google.com)) and to a host on the remote private lan you want to connect to. This will show you whether your routing is correct.

It looks to me as if you"re routing everything through your internet route, and nothing through the vpn tunnel, but it's a bit hard to follow with the addresses you replaced.

Also post output of
```
route
```
(I'm not used to ip route so I find it harder to read)

I don't know what exactly Network Manager does or could be doing, but in the end, all you need is a tunnel, routing, and possibly dns (eg use a name server on the remote LAN in stead of your usual DNS, so you get name resolution for LAN hosts)

---

### Post by rrwo on 2008-03-31
traceroute is of no help. I've already tried it.

The output of route isn't much different than ip route. I've compared the output of route on the manual VPN vs. NetworkManager and both are identical as well.

I'm also using DNS from the LAN (note the "usepeerdns" option and that I said that I checked /etc/resolv.conf in my post).

My point is that I've set up a tunnel that as far as I can tell is exactly the same as NetworkManager sets up, but mine doesn't work. Why?

---

### Post by The Cog on 2008-03-31
Your DNS server addresses are stored in **/etc/resolv.conf**. I guess that the VPN is updating this, but manually you haven't thought of it. Start the VPN with Network Manager to see what the entries get changed to.

---

### Post by rrwo on 2008-03-31
The entries are changed to the same values when I use NetworkManager or manually start the connection.

---

### Post by The Cog on 2008-03-31
Sorry, I must hae missed the bit about you changing resolv.conf.

Can you ping the DNS server? If not, you can check the routing with a command like this:
**ip route get 1.2.3.4**
Beyond that, I'm running out of ideas.

---

### Post by rrwo on 2008-03-31
I cannot ping the DNS servers.

When I use "ip route get addr" it looks ok:
```
169.254.1.2 dev ppp0  src 169.254.1.20 
    cache  mtu 1412 advmss 1372 hoplimit 64

```
where 169.254.1.2 is a nameserver and  169.254.1.20  the address that I have been assigned on the VPN (not the same as the gateway).

I don't think that my having a different address than the gateway is causing the confusion, since I get the same exact result from the command when connected using NetworkManager.

I took a look at the source code for the PPTP plugin.  It calls the command-line for initialising the PPTP connection, and as far as I can tell, I'm doing everything the same. I need to look at how the routing is updated, though.

---

### Post by rrwo on 2008-03-31
It seems that the cause of my problems is  [packet recursion]("http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lots_of_data").  That is, the packets for the tunnlt keep getting sent to itself.

I'm not sure what options are causing it, but I've found an *ugly* workaround to help diagnose it:
```
sudo ip route add 169.254.1.10 via 196.168.1.1  dev eth0
sudo pon myvpn
sudo ip route delete 169.254.1.10 dev ppp0
sudo ip route replace default dev ppp0

```
That is, I create a route for the VPN through my network *before* starting it.  Then I delete the old route and set the default route through it.   (It doesn't seem to work if change the route after starting the VPN, but then again, it's late so I should try again after some sleep...)

It's a kluge, and probably a stupid one at that.  I need to figure out what the evil options are. I can't find anything in /etc/ppp/options.pptp.  Advice would be helpful.

---

### Post by rrwo on 2008-04-01
I was able to use ```
ps -AF |grep pppd
``` to see the process launched by NetworkManager.  What I found isn't good for solving my problem:
```
/usr/sbin/pppd \
  pty "/usr/sbin/pptp 169.254.1.10 --nolaunchpppd" \
  remotename vpn.example.com \
  ipparam NetworkManager \
  usepeerdns \
  require-mppe-128 \
  nodeflate \
  nobsdcomp \
  lock \
  refuse-eap \
  refuse-chap \
  refuse-mschap \
  mtu 1416 mru 1416 \
  lcp-echo-failure 10 \
  lcp-echo-interval 10 \
  plugin nm-pppd-plugin.so

```
The main difference is the plugin.  It doesn't work if I call it from the command-line, and anyhoe, it's a NetworkManager plugin. So I don't want to use it anyhow.

---

### Post by rrwo on 2008-04-01
Ok, some poking around the web shows that other people have had the same problem, e.g. [here]("http://bornl33t.net/linux/vpn-tunneling").

Manually deleting the route after the connection is created doesn't work.  But setting up a script that is run automatically after connecting does work. (I'm not sure why it should matter, but it does.)

Create a file /etc/ppp/ip-up.d/no-loop:
```
#!/bin/sh

/sbin/route del -host $5 dev $1

```
and chmod +x the file.

---

