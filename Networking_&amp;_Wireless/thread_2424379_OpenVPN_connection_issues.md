---
title: "OpenVPN connection issues"
date: 2019-08-07
forum: Networking &amp; Wireless
---

### Post by cropicana on 2019-08-07
Hi all,
I'm currently working on my first project with Linux setting up a VPN server on the Microsoft Azure cloud. I've gotten as far as fully configuring the server and clients with a tutorial, but then the tutorial ended and the training wheels fell off lol. I've gotten a client to connect to the server successfully after much trial and error, but I cannot get that client to connect to the internet through the server. I'd usually try to troubleshoot my way through it, and I have messed around with network configurations and the server's firewall, but this is just such a vague and seemingly complicated issue I think it's time to swallow my pride and ask for help.

The server is running Ubuntu 18.04 LTS, and I've connected with both an Ubuntu and a Windows machine. 

Could anybody give me any networking advice, or any advice as to what the most likely issues are?
Please let me know if there is any additional information I should add here lol.

Thanks for your time!

---

### Post by SeijiSensei on 2019-08-07
Ubuntu will not pass packets between interfaces by default as a security measure.  So if you have packets arriving on tun0 intended to go out to the Internet via eno0, they'll be blocked.

To fix this, remove the hash mark ("#") from the line

```
net.ipv4.ip_forward=1
```

in the file /etc/sysctl.conf.  (You'll need root privileges, e.g., "sudo nano /etc/sysctl.conf").  Then reboot.  Any better?

If that doesn't fix the problem, show us the results of running "route -n".

---

### Post by cropicana on 2019-08-07
No luck with the sysctl.conf after reboot.

Here's the return of "route -n":
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
168.63.129.16   10.0.0.1        255.255.255.255 UGH   100    0        0 eth0
169.254.169.254 10.0.0.1        255.255.255.255 UGH   100    0        0 eth0



```

---

### Post by SeijiSensei on 2019-08-08
I've never used Azure. All my cloud machines are [Linodes]("https://www.linode.com/") with public IP addresses.  I'm not sure that's how Azure works from reading [this](https://docs.microsoft.com/en-us/azure/virtual-network/what-is-ip-address-168-63-129-16). Does the Azure machine have a unique public IP address?  It can't just have an address in 10.0.0. since addresses like that aren't public.  

Assuming that it has some public address, you next have to set things up so that the machines on both ends can see each other over the public Internet. 

Let's start with the client at your end.  Suppose it has an address of 172.18.18.18, and connects to your router at 172.18.18.1 then out to the Internet.  Let's also suppose the public IP address of the Azure machine is 172.16.16.1.  Also we'll assume that the tunnel address on your end is 10.8.0.2 with 10.8.0.1 on the Azure machine. Then on your end you'd need to add this route:

```
ip route add 172.16.16.1 via 172.18.18.1
```

with this default route:

```
ip route add default via 10.8.0.1
```

Now the encapsulated traffic that originates on the client knows to use the public Internet to reach the Azure machine via your network's default router, while all other traffic goes through the tunnel.

Can you ping 10.8.0.1 from the local machine?  

This stuff isn't easy.

---

### Post by cropicana on 2019-08-11
Yeah it does have a public IP, I've used it to connect to with PuTTY.

> [COLOR=#000000]Let's start with the client at your end. Suppose it has an address of 172.18.18.18, and connects to your router at 172.18.18.1[/COLOR]
Ok, so I'm still not quite sure which addresses you're referring to here. How would I find the actual adress of my client machine, and where it connects to the router?

Also what is the tunnel address stuff?

> [COLOR=#000000]Now the encapsulated traffic that originates on the client knows to use the public Internet to reach the Azure machine via your network's default router, while all other traffic goes through the tunnel.[/COLOR]
I think I understand what you are saying, but this sparked another question: will this solution work if my client is switching between different routers and access points when I use it in public?

> [COLOR=#000000]This stuff isn't easy.[/COLOR]
I've never read a more truthful statement in my life lol. Thanks so much for helping me learn this :).

---

### Post by SeijiSensei on 2019-08-12
> **cropicana said:**
> Ok, so I'm still not quite sure which addresses you're referring to here. How would I find the actual adress of my client machine, and where it connects to the router?
From the point of view of the Azure server, your public IP address is the address assigned to the Internet-facing side of your router.

> Also what is the tunnel address stuff?

Each end of the tunnel has its own IP address like 10.8.0.1.  All the tunnel traffic flows between these two addresses.  On my machine that is the OpenVPN client, running the command "ip addr" returns
```

3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 100
    link/[65534] 
    inet 10.1.1.30 peer 10.1.1.1/32 scope global tun0

```
10.1.1.1 is the tunnel address I assigned to the server; the tunnel address on the client is 10.1.1.30.  These are assigned in the "ifconfig" directive in the OpenVPN .conf file.  For instance, on the server:

```
ifconfig 10.1.1.1 10.1.1.30
```

with the reverse order of addresses on the client:
```
ifconfig 10.1.1.30 10.1.1.1
```

> I think I understand what you are saying, but this sparked another question: will this solution work if my client is switching between different routers and access points when I use it in public?
I assume you have some kind of the firewall running on the Azure machine.  You'll need to open up the OpenVPN port on that machine to all remote IP addresses. Suppose you chose a random high port for OpenVPN like 43210 instead of the default 1194 (which I suggest you do).  Then you'd need iptables rules on the Azure server that look something like
```

iptables -A INPUT -p tcp -d Azure.server.public.ip --dport 43210 -j ACCEPT
iptables -A INPUT -p udp -d Azure.server.public.ip --dport 43210 -j ACCEPT

```

> I've never read a more truthful statement in my life lol. Thanks so much for helping me learn this.

You're welcome!

I don't try to pass all my traffic through the tunnel. Stuff like HTTP requests just go out from my router to the Internet. I use the tunnels to communicate privately with the remote servers I have running at Linode.  If someone wants to sniff my traffic to see I visit ubuntuforums.org routinely, I honestly don't care.

---

