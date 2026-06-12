---
title: "What Could Be Stopping This Wired Connection From Pinging Anything But Itself?"
date: 2021-10-13
forum: Networking &amp; Wireless
---

### Post by davidahillman on 2021-10-13
I have a Dell Precision 5810 tower on which I've installed a freshly-downloaded ISO of Kubuntu 20.04.3 LTS ( to an SSD drive ).  This system has Intel's i217-LM on-board ethernet interface.  Despite all of the configuration being apparently correct, it fails to ping any address other than its own.

So the question is, what could cause that?

Troubleshooting that has already been done includes:

[LIST]
[*]the system's network hardware is known to be functional -- when I boot it into Windows 10 from an alternate drive, the network works flawlessly
[*]not only that, but I have Virtualbox installed on Windows 10, and two Kubuntu 20.04.3 virtual-machines use a bridged network adapter, again flawlessly
[*]obviously, the network works correctly, and other Kubuntu 20.04.3 systems use it without issue
[*]booting this particular desktop into Kubuntu 20.04.3 ISO off a usb drive also results in no network connection
[/LIST]

Despite the above, the problematic desktop reports that it has a (statically-assigned) IP address, correct netmask, correct gateway, correct routes, and everything else I can think of to check.  An adjacent Kubuntu 20.04.3 system with all the same configuration -- except a different IP address -- works just fine, on the same network.  No other systems on the same subnet can ping the problematic desktop, either.

For kicks, I shut down the adjacent system that works correctly, and changed the problematic host's IP address to the address of the working system.  And unsurprisingly, that made no difference either.

```

# ip addr show
<snip>
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000    link/ether 64:00:6a:6d:bd:80 brd ff:ff:ff:ff:ff:ff
    inet 192.168.96.21/24 brd 192.168.96.255 scope global noprefixroute enp0s25
       valid_lft forever preferred_lft forever
    inet6 fe80::347c:d63b:42d0:f74f/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```

```

# ip link show
<snip>
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 64:00:6a:6d:bd:80 brd ff:ff:ff:ff:ff:ff

```

```

# ip route
default via 192.168.96.1 dev enp0s25 proto static metric 100 
169.254.0.0/16 dev enp0s25 scope link metric 1000 
192.168.96.0/24 dev enp0s25 proto kernel scope link src 192.168.96.21 metric 100 

```

```

# ufw status
Status: inactive

```

```

# cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=true


[device]
wifi.scan-rand-mac-address=no

```


```

# ping 192.168.96.1
PING 192.168.96.1 (192.168.96.1) 56(84) bytes of data.
From 192.168.96.21 icmp_seq=1 Destination Host Unreachable
From 192.168.96.21 icmp_seq=2 Destination Host Unreachable
From 192.168.96.21 icmp_seq=3 Destination Host Unreachable
From 192.168.96.21 icmp_seq=4 Destination Host Unreachable
From 192.168.96.21 icmp_seq=5 Destination Host Unreachable
From 192.168.96.21 icmp_seq=6 Destination Host Unreachable
From 192.168.96.21 icmp_seq=7 Destination Host Unreachable


--- 192.168.96.1 ping statistics ---
8 packets transmitted, 0 received, +7 errors, 100% packet loss, time 7068ms

```

```

# ping 192.168.96.21
PING 192.168.96.21 (192.168.96.21) 56(84) bytes of data.
64 bytes from 192.168.96.21: icmp_seq=1 ttl=64 time=0.037 ms
64 bytes from 192.168.96.21: icmp_seq=2 ttl=64 time=0.038 ms
64 bytes from 192.168.96.21: icmp_seq=3 ttl=64 time=0.026 ms
64 bytes from 192.168.96.21: icmp_seq=4 ttl=64 time=0.025 ms
64 bytes from 192.168.96.21: icmp_seq=5 ttl=64 time=0.025 ms
<snip>

```

I have installed Ubuntu at least dozens of times, and a bunch of other OSes, and I have never seen a machine this resistant to talking on a network -- and I'm out of ideas.  The hardware is good.  The network is good.  The configuration is good.  Security is disabled.  The interface is up.  What else is there?

 So if you have any suggestions, please advise.  Thanks.

---

### Post by TheFu on 2021-10-14
Have you tried NOT using network-manager?  Configure the static IP using just the netplan YAML file?
The route table above seems a little odd too.

---

### Post by The Cog on 2021-10-14
Right after trying to ping the default router, use ip nei to list the known neighbour MAC addresses. I expect it will say FAILED, but it would be good to confirm this.
My next step would be to run the following command to view what packets go in and out while you try to ping the router:
```
sudo tcpdump -nntU -i enp0s25
```
I would hope to see ARP packets being sent, and even if no direct reply then you should see some background network traffic being received. What you see could tell you a lot.

---

### Post by davidahillman on 2021-10-14
> **TheFu said:**
> Have you tried NOT using network-manager?  Configure the static IP using just the netplan YAML file?


I have not, but if the resulting configuration is identical to a working machine -- which it is, per ifconfig and every other interface -- then I do not see how that can be the problem.

> The route table above seems a little odd too.

Again, it's identical to those on working machines.  If nothing else, it's surely sufficient to route to the gateway, and even that fails.

Thanks.

---

### Post by TheFu on 2021-10-14
So ... will you try something we suggest or should we just stop trying to find a working solution?
Nobody 100% knows the solution. We are trying to think of things that have caused problems with other users.

The hardware works with other OSes. Great. That doesn't prove anything about Ubuntu or the state that those other OSes may have left the registers in after a warm reboot into Ubuntu.  Some drivers don't clear the registers.  Some NICs seem to only work after a full, BRS, power-cycle first. Crappy driver software port.  There have been issues with the 217-v NICs.  I don't have any of that NIC, but have run into plenty of issues from other vendor NICs.

One post that got marked solved says that the hostname was inconsistent and correcting that fixed the problem. I find that hard to believe, but who knows what mDNS does?

NM has been a cause of issues for many people for 10+ yrs.

---

