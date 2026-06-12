---
title: "Networking subnets and confusion"
date: 2019-07-06
forum: Networking &amp; Wireless
---

### Post by dbarron on 2019-07-06
Ok, I have a headless cube pc with Ubuntu server 19.04 installed on it.  I had originally wanted to use it (besides other things) to replace my Buffalo WZR router (kinda old).  I had never gotten IP forwarding working right in the past, so I decided to work on it today.  I only had to umm rescue via attaching a monitor and keyboard once (lol).
Ok, the network is thus:  DSL_Cable modem->Cube(ext interface: enp1s0-192.168.1.1) -> (each a subnet) Internal ethernet(enp2s0-192.168.10.1), Internal Wireless)(enp3s0-192.168.2.1) (the Buffalo router as WAP).
My problem is that my ethernet devices can't see my wireless devices, and my wireless can't get internet, nor probably see the ethernet devices.
I'll provide below the current iptables rules that I got off an article somewhere.  I've tried things, but apparently not the 'right' things.
Just to confirm the Ubuntu device can access everything.
```
# Default policy to drop all incoming packets.
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Accept incoming packets from localhost and the LAN interface.
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i enp2s0 -j ACCEPT
iptables -A INPUT -i enp4s0 -j ACCEPT
# Accept incoming packets from the WAN if the router initiated the connection.
iptables -A INPUT -i enp1s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT
# Default policy to drop all incoming packets.
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Accept incoming packets from localhost and the LAN interface.
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i enp2s0 -j ACCEPT
iptables -A INPUT -i enp4s0 -j ACCEPT
# Accept incoming packets from the WAN if the router initiated the connection.
iptables -A INPUT -i enp1s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT

# Forward LAN packets to the WAN.
iptables -A FORWARD -i enp2s0 -o enp1s0 -j ACCEPT

# Forward WAN packets to the LAN if the LAN initiated the connection.
iptables -A FORWARD -i enp1s0 -o enp2s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT

# NAT traffic going out the WAN interface.
iptables -t nat -A POSTROUTING -o enp1s0 -j MASQUERADE
# Forward LAN packets to the WAN.
iptables -A FORWARD -i enp2s0 -o enp1s0 -j ACCEPT

# Forward WAN packets to the LAN if the LAN initiated the connection.
iptables -A FORWARD -i enp1s0 -o enp2s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT

# NAT traffic going out the WAN interface.
iptables -t nat -A POSTROUTING -o enp1s0 -j MASQUERADE
```

I bet the solution is very simple...but my head hurts and I can't really get there.  I would much appreciate what steps would be necessary on the Ubuntu gateway to facilitate this.  Links to another very similar suggestion are also welcome, I did do some searching, but not thoroughly, as there were too many results.

---

### Post by TheFu on 2019-07-06
Don't use the WAN port on the Buffalo.  Just take the cable from the WAN port and connect it to one of the LAN ports instead. Now, your wifi and wired LAN should be on the same subnet.  The PC would run the DHCP server and provide addresses to wifi devices.  Effectively taking a wifi-router and making it into a wifi-AP.

If you care more about security, there are different topologies to be considered.

---

### Post by dbarron on 2019-07-06
DOH!  I thought of that when I was starting this endeavor, then dang if I didn't do that.   Off to try!
Nope..by some dumb luck, I didn't use the WAN port :(  But thank you..I don't think I consciously didn't do.

---

### Post by SeijiSensei on 2019-07-06
Ubuntu by design will not forward packets across interfaces as a security measure. You need to uncomment the line
```
net.ipv4.ip_forward=1
```
in /etc/sysctl.conf, then reboot.

---

### Post by dbarron on 2019-07-06
Yes, since I have the first subnet working, you can assume I did that (which I did).  Definitely good to cover the bases though. Thank you.
Oh, I ssh'd into the Buffalo router and I can telnet back out, so that device has internet access working as well, though the wireless clients don't yet.
I feel fairly confident I can fix the wireless clients if I can actually get to the GUI from my wired workstation.

---

### Post by TheFu on 2019-07-06
If the modem is providing a subnet, then it isn't just a modem. It is a router.  Double-NAT isn't the best choice. Many modem/routers will let you setup "bridge mode" so the public IP is passed through to the internal router (your cube).  If you aren't 100% certain of your network skills, perhaps using a router distro like pfSense, OpnSense or one of the Linux router distros would be a smarter idea? Then you don't need to wonder if a tiny mistake was made and all sorts of unintended traffic is getting passed the router.  That would be bad, yes?

If you might want to run a VPN server on this machine, it would be smart to ensure the internal LAN uses some non-standard LAN subnet. Avoiding collisions with any other LANs you might encounter out in the world.  If you do it now, it will save hassles later.

---

### Post by Doug S on 2019-07-06
> **TheFu said:**
> Don't use the WAN port on the Buffalo.  Just take the cable from the WAN port and connect it to one of the LAN ports instead. Now, your wifi and wired LAN should be on the same subnet.  The PC would run the DHCP server and provide addresses to wifi devices.  Effectively taking a wifi-router and making it into a wifi-AP.+1. I do exactly this. My wifi router is basically a switch. It also has a static LAN ip addresss outside of my dhcp server dynamic address pool, so that I can still talk to it, when needed. It has been years since I have actually had to talk to it.

OP: your iptables rules seem to be largely repeated.

---

### Post by dbarron on 2019-07-06
I do have the modem in passthru mode.  I thought of installing a router distro, and maybe i should, but I already had Ubuntu Server there.  I wanted to continue to use the server with regards to Plex and Nextcloud for machines behind the firewall only.  This is a home network, but I'm an ex-IT person, so I have umm like 7 linux distros running back there (lol).  I would not be adverse to running a router distro, if I could still provide the internal services.  This could end up being the answer (though it wasn't the question I asked), do you have knowledge to impart about my qualm there?
Doug, I assure you, I do not speak *iptable*, so if you point out a better way, I'll be certain to try it.  As I pointed out, I basically got that from a blog post/article.

---

### Post by joshuax12 on 2019-07-07
> **dbarron said:**
> Ok, I have a headless cube pc with Ubuntu server 19.04 installed on it.  I had originally wanted to use it (besides other things) to replace my Buffalo WZR router (kinda old).  I had never gotten IP forwarding working right in the past, so I decided to work on it today.  I only had to umm rescue via attaching a monitor and keyboard once (lol).
Ok, the network is thus:  DSL_Cable modem->Cube(ext interface: enp1s0-192.168.1.1) -> (each a subnet) Internal ethernet(enp2s0-192.168.10.1), Internal Wireless)(enp3s0-192.168.2.1) (the Buffalo router as WAP).
My problem is that my ethernet devices can't see my wireless devices, and my wireless can't get internet, nor probably see the ethernet devices.
I'll provide below the current iptables rules that I got off an article somewhere.  I've tried things, but apparently not the 'right' things.
Just to confirm the Ubuntu device can access everything.
```
# Default policy to drop all incoming packets.
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Accept incoming packets from localhost and the LAN interface.
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i enp2s0 -j ACCEPT
iptables -A INPUT -i enp4s0 -j ACCEPT
# Accept incoming packets from the WAN if the router initiated the connection.
iptables -A INPUT -i enp1s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT
# Default policy to drop all incoming packets.
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Accept incoming packets from localhost and the LAN interface.
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i enp2s0 -j ACCEPT
iptables -A INPUT -i enp4s0 -j ACCEPT
# Accept incoming packets from the WAN if the router initiated the connection.
iptables -A INPUT -i enp1s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT

# Forward LAN packets to the WAN.
iptables -A FORWARD -i enp2s0 -o enp1s0 -j ACCEPT

# Forward WAN packets to the LAN if the LAN initiated the connection.
iptables -A FORWARD -i enp1s0 -o enp2s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT

# NAT traffic going out the WAN interface.
iptables -t nat -A POSTROUTING -o enp1s0 -j MASQUERADE
# Forward LAN packets to the WAN.
iptables -A FORWARD -i enp2s0 -o enp1s0 -j ACCEPT

# Forward WAN packets to the LAN if the LAN initiated the connection.
iptables -A FORWARD -i enp1s0 -o enp2s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT

# NAT traffic going out the WAN interface.
iptables -t nat -A POSTROUTING -o enp1s0 -j MASQUERADE
```

I bet the solution is very simple...but my head hurts and I can't really get there.  I would much appreciate what steps would be necessary on the Ubuntu gateway to facilitate this.  Links to another very similar suggestion are also welcome, I did do some searching, but not thoroughly, as there were too many results.

Check if the 192.168.1.1 works normally on the browser...
If the previous method doesn't work for you, you can send me the model of your router I'll check on [COLOR=#1155cc][FONT=Arial]_[https://192-168-1-1ip.mobi/](https://192-168-1-1ip.mobi/)_[/FONT][/COLOR][COLOR=#1155cc][FONT=Arial]__[/FONT][/COLOR] for a solution.

---

### Post by dbarron on 2019-07-07
Umm, depending on POO (point of origin) intended, from my 192.168.10.* desktop, no, I can't, but that's kinda typical of NAT schemes I think, I can access the modem at 192.168.1.254 though. From the Buffalo, it's also not accessible.
Of course, the server is available if addressed at the interface on that subnet from each.

Addressing prior thoughts, the only thing that seemed appropriate (as in still in active development/support) and possibly has the software needed might be the FreeBSD OpnSense distro.  Thoughts?  I haven't been able yet to validate that I will be able to add basic FreeBSD packages in OpnSense...asking that now on their forum.

---

### Post by TheFu on 2019-07-07
> **dbarron said:**
> I do have the modem in passthru mode.  I thought of installing a router distro, and maybe i should, but I already had Ubuntu Server there.  I wanted to continue to use the server with regards to Plex and Nextcloud for machines behind the firewall only.  This is a home network, but I'm an ex-IT person, so I have umm like 7 linux distros running back there (lol).  I would not be adverse to running a router distro, if I could still provide the internal services.  This could end up being the answer (though it wasn't the question I asked), do you have knowledge to impart about my qualm there?
Doug, I assure you, I do not speak *iptable*, so if you point out a better way, I'll be certain to try it.  As I pointed out, I basically got that from a blog post/article.

The only "knowledge" I would strongly impart is that WAN routers shouldn't be providing data services like nextlcoud or plex. One tiny config problem and it will be sharing that data with the world. The WAN router is the first line of defense. It should do "router/firewall" things, not data serving, unless your intent is to share all that data with the world.



IMHO.

I run both plex and nextcloud here. Neither are available directly over the internet. They are only available from the LAN or over the internet with either an ssh-based SOCKS proxy or full VPN.  No way would i risk my WAN router with either of those tools. NO FREAKIN' WAY!

My WAN router runs pfSense on an x64 AMD router box (APU2c4).

---

### Post by dbarron on 2019-07-07
I don't intent to make them available over the internet at all.  They will bind only to the internal interfaces.
It may not seem like it, but I worked for 20 years in Computer Security and was certified on Checkpoint FW1.  I however, am not running a business nor a high security installation, I'm making do like most...on a shoestring.
So the clients have to run on the server, but whether the server is better as the firewall or an antiquated DDWRT Buffalo appliance is better ?

---

### Post by Doug S on 2019-07-07
> **dbarron said:**
> Doug, I assure you, I do not speak *iptable*, so if you point out a better way, I'll be certain to try it.  As I pointed out, I basically got that from a blog post/article.iptables can take considerable time to learn thoroughly, but I think it is worth it. However, and as mentioned earlier, I only have experience with one local sub-net.

While overly complicated as a starting point for you, I'll pm you a link to my current iptables rule set (it is on my web site, but I don't advertise the link).

---

### Post by TheFu on 2019-07-07
> **dbarron said:**
> I don't intent to make them available over the internet at all.  They will bind only to the internal interfaces.
It may not seem like it, but I worked for 20 years in Computer Security and was certified on Checkpoint FW1.  I however, am not running a business nor a high security installation, I'm making do like most...on a shoestring.
So the clients have to run on the server, but whether the server is better as the firewall or an antiquated DDWRT Buffalo appliance is better ?
 
If you don't want to spend much,  spend $50 and get a small biz router that will be well supported (ubiquity edgerouterX, routerboard) for 5+ yrs.  I wouldn't merge a media server with my WAN firewall.  Can't be any clearer than that. Seen too many failures over the years, at homes, small businesses and by enterprises with 150K employees.

Did the checkpoint firewalls run a media server?

Huge professional organizations make mistakes on their routers and firewalls with all their change management, peer reviews, and approved maintenance windows.  The way to combat that problem for small networks is to have 2 layers of protection and hope that only 1 has a failure/misconfiguration at a time.

---

### Post by dbarron on 2019-07-07
Changed server to OpnSense, configuring now.  Thanks for all your input.  Even if it's based on iptables, I may well be back :) 
As you may have noted, I like to try things.  Thank you all.  Marking solved.

---

