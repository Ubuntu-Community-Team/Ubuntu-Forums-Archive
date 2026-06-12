---
title: "Default Gateway with DHCP"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by shahzeb.ihsan on 2008-01-25
Hi,

**This problem has been mentioned in other posts, but the only solution suggested was to add a default gateway manually.**

OK, so here's the problem. In my office we have a DHCP based network where the server assigns IP addresses based on the MAC address and also sets up the defaul gateway. This works fine for systems running Fedora or CentOS. I have Ubuntu 7.10 Gusty Gibbon, which picks up the IP jcorrectly but the default gateway doesn't get set.

Suppose the IP address assigned to me is 192.168.1.54, my routing table looks like this:

> 
```

$ /sbin/route -n
Kernel IP routing table
Destination    Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.54    0.0.0.0         UG    100    0        0 eth0

```


As you can see, the default gateway is set to the the IP assigned to my machine instead of 192.168.1.1 (the ACTUAL default gateway).

> 
sudo route add default gw 192.168.1.1


Is there any way around this problem so I don't have to set the gateway manually?

Regards,
Shahzeb

---

### Post by jeffus_il on 2008-01-25
Are you using Network Manager? Which Network card do you have?

---

### Post by shahzeb.ihsan on 2008-01-25
I've done this "exercise" using both the Network Manager and the */etc/network/interfaces* file.

My Ethernet card as reported by *lspci* is:

> 
$ lspci | grep Ethernet
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)


---

### Post by jeffus_il on 2008-01-25
If Network Manager is in the Browsing mode (I forget what they call it, there's a little checkbox), cancel it, use their manual setup, and dhcp, so you won't have to set up the gateway. The incorrect gateway may be given by Avahi, possibly due to a weak radio signal and dhcp timing out, What is your signal strength like?

---

### Post by shahzeb.ihsan on 2008-01-25
It's called "Roaming Mode" :)

But I'm not using it, we have a simple wired network. Don't know much about Avahi though, I'm something of a n00b here :oops: but I've seen it being updated by the "Update Manager" during system updates.

But, for the sake of argument, if it is being timed out how do I increase the timeout value (if it can be changed)? If timeout was the issue, would I be assigned an IP correctly? In my Ubuntu correctly picks up the IP from the DHCP server, but also sets my default gateway to the IP assigned to me.

---

### Post by deltaprime on 2008-01-25
ok guyz dont give away network information like that 
its not a good idea (for your own security)
smudge it or paint over it with some image processing tool
DELTA

---

### Post by shahzeb.ihsan on 2008-01-25
Its just a simple LAN setup and the IP scheme is pretty common, but thanks, I'll be careful in the future.

---

### Post by jeffus_il on 2008-01-25
There is a file called /etc/nsswitch.conf.

There line:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

determines how the address is resolved.

file refers to your hosts file.

mdns4 using the avahi host resolution system.

comment out your original line to save it and play with this, it may solve your problem.

for example a line like this would resolve the host name locally
```
hosts:          files
```

Be careful, I once solved a problem this way,  but do a bit of research.

---

### Post by Zack McCool on 2008-01-25
> **deltaprime said:**
> ok guyz dont give away network information like that 
its not a good idea (for your own security)
smudge it or paint over it with some image processing tool
DELTA

Why?  Nothing routable was given.  Here, my machine is at 192.168.0.101.  Have fun with it...

---

### Post by jeffus_il on 2008-01-25
> **shahzeb.ihsan said:**
> Its just a simple LAN setup and the IP scheme is pretty common, but thanks, I'll be careful in the future.

Don't worry, nothing here to have a sleepless night about. All IP addresses are local.

---

### Post by deltaprime on 2008-01-25
dont get me wrong
just making sure cause i know whats possible
=)
DELTA

---

### Post by jeffus_il on 2008-01-25
> **deltaprime said:**
> dont get me wrong
just making sure cause i know whats possible
=)
DELTA
and also what's impossible ???

---

### Post by shahzeb.ihsan on 2008-01-25
DNS isn't a problem here, Ubuntu picks up the DNS server correctly too :-k (verified using both the NetworkManager and the */etc/resolv.conf* file).

But the default gateway doesn't get set correctly. On each system boot-up, the default gateway is set to my IP, so I have to change it manually :(

---

### Post by jeffus_il on 2008-01-25
Isn't the default gateway set by DHCP? I have had similar problems and since my wireless network is from my desktop, not laptop, I use the interfaces file to set it up, I only had trouble with Network Manager, What does work fine for roaming is Wicd.

---

### Post by deltaprime on 2008-01-25
you are making yourself an easy target to hackers with a corrupt mind
they can get into your system which is not too hard with all the information given and can get data off of it. This includes passwords you type in rthe future, passwords that are stored in your computer which can give them the option to steal your identity which im sure you wouldnt like.
i am not saying that this will happen now but in future be more careful.
you can probably find more information about this on remote-exploit.org or just search it on google if your interested.
i guess youll be fine though ;)

DELTA

---

### Post by shahzeb.ihsan on 2008-01-25
> **jeffus_il said:**
> Isn't the default gateway set by DHCP? I have had similar problems and since my wireless network is from my desktop, not laptop, I use the interfaces file to set it up, I only had trouble with Network Manager, What does work fine for roaming is Wicd.

The default gateway should be set by DHCP but it isn't being set. Our current network setup works great for all WinXP, Fedora and CentOS machines. I'm the only oddball using Ubuntu :-P and at the moment Ubuntu isn't picking up the default gateway from DHCP, as it should be...

---

### Post by jeffus_il on 2008-01-25
OK, I suspect Network Manager and it's dhcp client dhcdbd using dbus. They have always given me trouble on a number of systems. Wicd and dhcp3-client or the plain old interfaces file with dhcp3-client has always done a good job for me.

---

### Post by imdano on 2008-01-25
> **deltaprime said:**
> you are making yourself an easy target to hackers with a corrupt mind
they can get into your system which is not too hard with all the information given and can get data off of it. This includes passwords you type in rthe future, passwords that are stored in your computer which can give them the option to steal your identity which im sure you wouldnt like.
i am not saying that this will happen now but in future be more careful.
you can probably find more information about this on remote-exploit.org or just search it on google if your interested.
i guess youll be fine though ;)

DELTAThat actually isn't the case.  The IP Address he was given was assigned to him by a local router, which means the only you'd be able to access his machine with that IP Adress is if you were also directly connected to that router.  Which would require you to be in his office.  Even then you would have to exploit some vulnerability on an open port to do any damage.

---

### Post by shahzeb.ihsan on 2008-01-28
> **jeffus_il said:**
> OK, I suspect Network Manager and it's dhcp client dhcdbd using dbus. They have always given me trouble on a number of systems. Wicd and dhcp3-client or the plain old interfaces file with dhcp3-client has always done a good job for me.

OK, I tried using Wicd, better than NetworkManager, but it still didn't solve the problem :oops:
For the moment I've written a small script which executes at startup and deletes the "extra" route and adds the proper default gateway.

---

