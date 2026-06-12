---
title: "Help With ufw Trouble?"
date: 2017-11-04
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2017-11-04
1
down vote
favorite
	

I am running a vpn on my laptop. To ensure that traffic to and from the internet is only allowed through that vpn, I am running ufw with the following rules:

```

    Status: active
    Logging: on (low)
    Default: deny (incoming), deny (outgoing), disabled (routed)
    New profiles: skip

    To                         Action      From
    --                         ------      ----
    Anywhere on tun0           ALLOW IN    Anywhere                  
    1194/udp                   ALLOW IN    Anywhere                  
    192.168.1.0/24             ALLOW IN    192.168.1.0/24            
    Anywhere (v6) on tun0      ALLOW IN    Anywhere (v6)             
    1194/udp (v6)              ALLOW IN    Anywhere (v6)             

    Anywhere                   ALLOW OUT   Anywhere on tun0          
    1194/udp                   ALLOW OUT   Anywhere                  
    192.168.1.0/24             ALLOW OUT   192.168.1.0/24            
    Anywhere (v6)              ALLOW OUT   Anywhere (v6) on tun0     
    1194/udp (v6)              ALLOW OUT   Anywhere (v6)             

```

Now this works fine with one exception - I am unable to connect to octopi.local from my laptop without disabling the firewall. I can connect just fine through the direct IP address, but since that isn't a static address, that's not a reliable solution. How can I make sure that the octopi.local name is resolved through the firewall?

EDIT I found this page - [https://askubuntu.com/questions/861966/ufw-hostname-resolution](https://askubuntu.com/questions/861966/ufw-hostname-resolution) - and I tried the tail command, but I didn't really know what I was looking at. I did see "SPT=5353 DPT=5353" so I tried the "allow in 5353" command, but that didn't seem to help. Then I looked at my /etc/services file and found this:

```

    hostnames	101/tcp		hostname	# usually from sri-nic
    hostmon     5355/tcp            # hostmon uses TCP (nocol)
    hostmon     5355/udp            # hostmon uses UDP (nocol)

```

so I tried "allow in|out 5355". I also tried "allow in|out 101/tcp". That still didn't allow ssh to resolve the hostname. I thought I'd let you know what I'd tried...

---

### Post by TheFu on 2017-11-05
When it works, what is the IP for octopi.local?

---

### Post by rebeltaz on 2017-11-05
Right now it is 192.168.1.59, but like I said, that's not static. It hasn't changed in a while., but being dynamic, that's not to say it won't.

---

### Post by TheFu on 2017-11-06
> **rebeltaz said:**
> Right now it is 192.168.1.59, but like I said, that's not static. It hasn't changed in a while., but being dynamic, that's not to say it won't.

I use dhcp reservations so all my devices effectively have static IPs on my LAN.  Then there are other options available for letting each system know where to find the other systems on the network.  Avahi just doesn't work that well, IME.  

The reason I asked what the IP was - was to determine if it was outside the existing rules.  It is not.  I would look more closely at the order of the rules to ensure the LAN subnet ALLOW was first.

---

### Post by rebeltaz on 2017-11-06
> **TheFu said:**
> I use dhcp reservations so all my devices effectively have static IPs on my LAN.  Then there are other options available for letting each system know where to find the other systems on the network.  Avahi just doesn't work that well, IME.  

The reason I asked what the IP was - was to determine if it was outside the existing rules.  It is not.  I would look more closely at the order of the rules to ensure the LAN subnet ALLOW was first.

By "dhcp reservations" do you mean within the router itself? I don't think my router has that ability, or so I am told.

---

### Post by TheFu on 2017-11-06
> **rebeltaz said:**
> By "dhcp reservations" do you mean within the router itself? I don't think my router has that ability, or so I am told.

A router is 1 way. There are others.  I use a lite router software that doesn't do routing inside a VM that manages my internal network. The VM runs pfSense on a 256MB VM with 1 vCPU.  There's a webgui for it, but it isn't meant for home users (non-pro IT people).

I find most home routers to be a security nightmare. The firmware isn't maintained consistently or not at all.  For example, even dd-wrt stopped supporting my old physical router years ago, so I moved to an x86 (12W) router platform and put pfsense on it.  They are excellent at patching.  There are other Pro-level routers which take patching seriously for around $35-$100 - mikotek rb750-something is one. Ubuquiti is another.  These are pro-grade, not for end users, but there are plenty of youtube videos to explain things for both of these vendor routers.

And keep your wifi WAP separate from the router.  Routers should last 10-15 yrs. WAP standards change all the time, so a $80 WAP update keeps your wifi network fast.

---

### Post by rebeltaz on 2017-11-06
You do this for a living, don't you? :) lol... I think setting a static IP address in the OctoPrint server would be a simpler solution than that. Don't get me wrong, I do appreciate your help and advice. I was just hoping that there was a simple setting in a config file that I was missing. I guess when you try to make technology do things outside of the average user arena like I usually do, you should expect issues. God knows I have my fair share. I doubt I will ever attempt your setup, but I will read up on it. I've never heard of "router software."

---

