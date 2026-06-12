---
title: "routing problem on internel network"
date: 2022-01-10
forum: Networking &amp; Wireless
---

### Post by bjlockie on 2022-01-10
This is my laptop's routing table:
```
$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    600    0        0 wlp0s20f3
192.168.68.0    0.0.0.0         255.255.252.0   U     600    0        0 wlp0s20f3
```
I can ping the desktop on my internal network and use the Internet but i CAN'T ping my raspberry pi.

This is my desktop:
```
$ sudo route                                                                      
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    600    0        0 wlp4s0
192.168.68.0    0.0.0.0         255.255.252.0   U     600    0        0 wlp4s0
```
i can ping my laptop and desktop and raspberry pi and use the Internet.

This is my raspberry pi:
```
$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    600    0        0 wlp0s20f3
192.168.68.0    0.0.0.0         255.255.252.0   U     600    0        0 wlp0s20f3
```
**I pinged my laptop and now the laptop can ping it.**

```
What is happening?
```
The raspberry pi is not visible from my cell phone.
I can't ping my cell phone from the raspberry pi.
I ping my cell phone from my laptop and desktop and the raspberry pi was able to ping my cell phone. :-)
I don't want to have to ping everything to get it to work plus I wonder if it is a temporary fix.

---

### Post by TheFu on 2022-01-11
Can you ping _gateway by name AND by IP?

---

### Post by bjlockie on 2022-01-12
> **TheFu said:**
> Can you ping _gateway by name AND by IP?

Yes, the raspberry pi can ping 192.168.68.1 and _gateway.
It can ping my desktop and laptop but not my cellphone (my desktop and laptop can ping my cell phone).

---

### Post by bjlockie on 2022-01-12
I wonder if it is a firewall so I ran sudo iptables --list on all the computers.

Desktop:
```
$ sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere             multiport dports 4011
ACCEPT     udp  --  anywhere             anywhere             multiport dports mdns
ACCEPT     tcp  --  anywhere             anywhere             multiport dports 4000
```

Laptop:
```
$ sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere             multiport dports mdns
ACCEPT     tcp  --  anywhere             anywhere             multiport dports 4000

```

Rasberry Pi:
```
$ sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
```

Port 4000 is for GUI remote desktop software (NoMachine).
I don't know what 4011 or mdns are.

---

### Post by The Cog on 2022-01-13
Can I ask everyone to use **[FONT=Courier New]sudo iptables-save[/FONT]** rather than **[FONT=Courier New]sudo iptables --list[/FONT]** when showing iptables rules. iptables --list does not show all the relevant information - it omits interface names (in and out) so that perfectly working rule sets can end up looking as though they accept anything from anywhere, and also doesn't show any NAT rules which could possibly be important. What's more, iptables-save prints the rules in the exact format you need to enter them, which can be helpful (you can even save the iptables-save output and use it to restore the rules later - who'd have thought it?).

The above rules do have some things wrong:
Your INPUT rules have an ACCEPT policy (accept everything by default) but no REJECT or DROP rules. So the firewalls are not blocking anything incoming, and all the other ACCEPT rules are pointless.
You have no OUTPUT rules - not even a default ACCEPT or REJECT policy. 

Given that nothing is being blocked incoming, one could perhaps suspect that outgoing traffic is being blocked, but the absence of any FORWARD or OUTPUT policy suggests that maybe iptables is completely broken. I can't think of anything other than a reboot or failing that a reinstall to get a working iptables setup.

Once you have iptables working correctly, I suggest the following:
* Drop all incoming connections by default 
* Allow incoming responses to outgoing connections (that were allowed out): This means your incoming rules can be quite short and simple:
* Allow the computer to talk to itself (otherwise odd services like print spooling don't work)
* Allow incoming connections on a protocol by protocol basis (e.g. allowing incoming pings perhaps)
```
sudo iptables -P INPUT DROP
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT
```

Unless you are really paranoid, I would default alllow outgoing connections. If blocking OUTPUT by default then you need to consider adding the inverse of the above rules to the OUTPUT chain, but this can get quite long as you discover more and more things that don't work because you have blocked outgoing connections.

---

### Post by TheFu on 2022-01-13
I'm hardly an iptables guru, but all my VPNs have iptable rules to ensure packets get from the VPN-LAN to the locations they need to get - be that other LANs or the internet.
For a desktop, I find the rules created by ufw to be sufficient. Typically I allow everything on the LAN and nearly all outbound. No direct inbound except ssh for desktops.  All my systems have ssh running, but only allow key-based authentication from outside the LAN.

For servers, I tend to block everything inbound, except for the exact services needed and block SMTP out that doesn't go to my main MTA server. No systems get to send email directly without going through 2 MTA systems first.  DNS and time are allowed, but only to LAN systems providing those services (except the servers actually doing DNS get to go external and my time server gets to do NTP in the pool.ntp.org sites.  Lots of little details to track, so it is best not to "wing it" and hope.  

I've played with end-user firewall GUIs. If there aren't any services, those can be fun, but the one I tried was beta-quality. It was good to see outbound connections asking for permission.  I can't remember the name of the firewall, but it was an attempt at porting the OSX firewall to Linux, if that helps searching.

---

### Post by bjlockie on 2022-01-13
Desktop:
```
$ sudo iptables-save
# Generated by iptables-save v1.8.7 on Thu Jan 13 19:48:37 2022
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -p udp -m multiport --dports 4011 -j ACCEPT
-A INPUT -p udp -m multiport --dports 5353 -j ACCEPT
-A INPUT -p tcp -m multiport --dports 4000 -j ACCEPT
COMMIT
# Completed on Thu Jan 13 19:48:37 2022
```

Laptop:
```
$ sudo iptables-save
# Generated by iptables-save v1.8.7 on Thu Jan 13 19:49:23 2022
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -p udp -m multiport --dports 5353 -j ACCEPT
-A INPUT -p tcp -m multiport --dports 4000 -j ACCEPT
COMMIT
# Completed on Thu Jan 13 19:49:23 2022

```

Nothing on the ubuntu-server.
I want to make the server be a media server.
I tried minidlna but the server is wifi and it seems flaky.
The server is 1GB so it has to be headless.
I'm going to try samba.

---

### Post by TheFu on 2022-01-13
Some routers have a wifi mode that prevents systems on the same LAN from accessing each other.
Also, what does this mean?
> The server is 1GB so it has to be headless.
Is that storage, RAM, ethernet speed, something else?

Samba isn't a good answer as a media server.  NFS is better. For a Raspberry Pi (v2 or later), I can recommend using OSMC.  I've been using it on v2 and v3 Pis for years now.  It is connected via wired ethernet to my Jellyfin server which provides both NFS and DLNA services (among others).  Jellyfin is a F/LOSS fork of Emby media server.

Using wifi for clients will never be as good as wired ethernet, powerline, or MoCA networked. It just isn't.

---

### Post by The Cog on 2022-01-13
Thanks for the iptables-save outputs. These confirm that the firewall rules are completely open - accept everything in all directions. So whatever problem you have, it's not the firewalls on the desktop or the laptop. I'll look again later, but I need sleep now.

---

### Post by The Cog on 2022-01-14
My next step would be to check make a note of the IP address and MAC address of each device. 
You can find these by using **[FONT=Courier New][COLOR="#0000FF"]ip address[/COLOR][/FONT] **on each device and looking at the relevant interface. link/ether is the MAC address, and inet is the ip address. Then you can try to ping things from one machine to another. 
Try to ping by name first. If that works, all is well.
If not, try to ping by IP address. If that works the problem is with name resolution.
If not, use the command **[FONT=Courier New][COLOR="#0000FF"]ip neighbor[/COLOR][/FONT]** to see if the MAC address has been resolved to an IP address. 
Once we know whether it's name->IP resolution or IP->MAC resolution that's the issue, we know what problem to work on.

---

### Post by bjlockie on 2022-01-30
got it all working.
I suspect it was a power supply issue. :-(

---

