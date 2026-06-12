---
title: "Ubuntu OpenVPN Gateway - IPTABLES and Routing Mutiple Subnets through the VPN"
date: 2020-12-13
forum: Networking &amp; Wireless
---

### Post by zaleon46 on 2020-12-13
I posted this in Specialized Support -> Servers too, but I guess it is more of a networking question so I'm posting it here too in case someone can help.

Hello All,

   I found a good Craft Computing video ([https://www.youtube.com/watch?v=xFficDCEv3c](https://www.youtube.com/watch?v=xFficDCEv3c)) and this other post for virtualbox ([https://mschoofs.blogspot.com/2020/08/vpn-gateway-vm-in-virtualbox.html](https://mschoofs.blogspot.com/2020/08/vpn-gateway-vm-in-virtualbox.html))  on how to setup an OpenVPN gateway for the whole network. I was able to  set it up and get everything working on Ubuntu 20.04 LTS, but for my  home network I run multiple subnets/VLANS to segregate IoT devices,  security cameras, streaming devices etc. off my main network and I'm  having trouble getting any of them to pass traffic to the VPN server.

Are there any IPTABLES/ufw gurus here that could help solve this issue?

I thought it might be an easy solution by just adding extra IP subnets  to the existing input/out statements then adding some static routes, but  that doesn't seem to be the case. Doing this allowed me to ping these  subnets from the Ubuntu VPN server, but they still don't pass any VPN  traffic!

My current IPTABLES look like this:
```
# Flush all existing settings:
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X

# Block All:
iptables -P OUTPUT DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Allow Localhost communictaion:
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# Allow communication with a DHCP server:
iptables -A OUTPUT -d 255.255.255.255 -j ACCEPT
iptables -A INPUT -s 255.255.255.255 -j ACCEPT

# Allow communication within your local network
iptables -A INPUT -s 10.10.1.0/24,10.60.1.0/24,192.168.5.0/24 -d 10.10.1.0/24,10.60.1.0/24,192.168.5.0/24 -j ACCEPT
iptables -A OUTPUT -s 10.10.1.0/24,10.60.1.0/24,192.168.5.0/24 -d 10.10.1.0/24,10.60.1.0/24,192.168.5.0/24 -j ACCEPT
## Replace this CIDR with your ##

# Allow established sessions to receive traffic:
 iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow TUN
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A FORWARD -o tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE
iptables -A OUTPUT -o tun+ -j ACCEPT

# allow VPN connection
iptables -I OUTPUT 1 -p udp --destination-port 1194 -m comment --comment "Allow VPN connection" -j ACCEPT

# Block All
iptables -A OUTPUT -j DROP
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP

echo "saving"
echo "done"


```
The only network that is passing traffic to the VPN is the main subnet  10.10.1.0/24 which is also where the Ubuntu VPN server resides.

This is output of route -n where I've added static routes for all the subnets/VLANS I want to pass through the VPN.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.1.1       0.0.0.0         UG    0      0        0 ens192
10.10.1.0       0.0.0.0         255.255.255.0   U     0      0        0 ens192
10.20.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
10.30.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
10.40.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
10.60.1.0       10.10.1.1       255.255.255.0   UG    0      0        0 ens192
192.168.5.0     10.10.1.1       255.255.255.0   UG    0      0        0 ens192


```

Also attached [ATTACH=CONFIG]287543[/ATTACH] is a screenshot of the output from iptables -L -n -v

Any suggestions will be greatly appreciated!

---

### Post by SeijiSensei on 2020-12-13
deleted

---

### Post by SeijiSensei on 2020-12-13
Let's start with a simple test. What if you change
```

iptables -P OUTPUT DROP
iptables -P FORWARD DROP

```
to
```

iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

```
Does it work now? What if you restore the OUTPUT policy to DROP? Still okay?

I'm also a bit concerned about the generic
```
iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE
```
What if you used rules like
```
iptables -t nat -A POSTROUTING -s 10.10.1.0/24 -o tun+ -j MASQUERADE
```
instead? Any better?

Oh, and please confirm you enabled "net.ipv4.ip_forward=1" in /etc/sysctl.conf. If it's still set to zero, that's the problem and not the iptables rules.

---

### Post by zaleon46 on 2020-12-13
Hi SeijiSensei,

    Thanks for your reply. I tried testing what you suggested with the 10.10.1.0/24 and 10.60.1.0/24 subnets. My results are below.

```

iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

```

This seemed to have no effect on any other subnet working, but 10.10.1.0/24 continued to work as normal.

```
iptables -t nat -A POSTROUTING -s 10.10.1.0/24 -o tun+ -j MASQUERADE
```

Also had no effect on the other subnets, but 10.10.1.0/24 continued working properly.

I also tried changing the above to ```
iptables -t nat -A POSTROUTING -s 10.10.1.0/24,10.60.1.0/24 -o tun+ -j MASQUERADE
``` and testing 10.60.1.0/24 subnet again, but it continued not to have an internet connection due to the VPN not passing its traffic.

Lastly I tried changing all drop statements to accept, but this also had no effect. Initially when switching my static IP over to the 10.60.1.0 subnet it appeared I had Internet access, but within 30 seconds this had reverted back to the usual not connected.

All of the entries in /etc/sysctrl.conf were commented out, but I uncommented the "net.ipv4.ip_forward=1" and rebooted the server. However, I believe based on the instructions that this was being done another way by placing it in the startup script rc.local which pointed it to apply ```
[COLOR=#000000][FONT=Arial]sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"[/FONT][/COLOR]
```

When viewing the iptables now [ATTACH=CONFIG]287545[/ATTACH], it appears some traffic passed between the 10.10.1.0 and 10.60.1.0 subnets, but as best I could ascertain this was just ping traffic from the console, which is successful.

---

### Post by Doug S on 2020-12-14
Your iptables rules listing does not match your actual iptables rules. Please fix, showing the last OUTPUT unconditional DROP rule. Then add a logging rule just before that rule so that you will get information about those 36 packets (well, next time).

EDIT: Oh you have some logging.  suggest to not use a logging chain, use individual logging rules with a unique comment per rule so you know from where the log entry came.

We also need to see the resulting nat rules do "sudo iptables -t nat -xvnL" and post the output not as a picture but as text between codes tags.

Run tcpdump sessions on each NIC, so you can correlate activity with iptables packets counters.

---

### Post by zaleon46 on 2020-12-15
Thanks for your suggestions and assistance. Sounds like it is getting complex and might be easier to do with an actual router or routing OS like Pfsense/OPNsense/OpenWRT so I may try that first.

---

