---
title: "How to correctly configure Ubuntu to use a static IP address?"
date: 2015-07-17
forum: Networking &amp; Wireless
---

### Post by johann-petrak on 2015-07-17
I need to give my computer a static IP address on my local network - the router I use does not allow me to configure things so that the router always gives the same IP address to my computer based on the MAC address.

I tried to edit my /etc/network/interfaces file to contain

```

[COLOR=#000000][FONT=monospace]iface eth0 inet static 
[/FONT][/COLOR][FONT=monospace]address 192.168.0.2
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
[/FONT]
```
but I still get a different IP assigned.

Also my changes in  [COLOR=#000000][FONT=monospace]/etc/resolv.conf (where I wanted to enter my own DNS server addresses) got overridden. 

I have searched for answers and got a number of - usually rather old - pages which all describe the same problem but no working solution. One page suggested to uninstall dhcp-client, but this would also uninstall network-manager, network-manager-gnome and ubuntu-minimal
and I think I need those.

This should be a trivial task, surely there must be an easy and correct procedure to just set the IP address of my computer to the value I want and be done with it?[/FONT][/COLOR]

---

### Post by NoWayWin8 on 2015-07-17
> **johann-petrak said:**
> [COLOR=#000000][FONT=monospace]
This should be a trivial task, surely there must be an easy and correct procedure to just set the IP address of my computer to the value I want and be done with it?[/FONT][/COLOR]

First you should undo the changes to /etc/interfaces.

You also need to login to your internet router and make sure there's an IP outside of it's starting and ending DHCP IP range. It's probably set to the full range of 2 - 255, so if you want that 192.168.0.2 address you need to set the router's starting DHCP IP to 3. Also note which DNS addresses the router uses for its connection.

Now open Network Manager and just set the Wired Connection's "IPv4" tab to MANUAL, then by "addresses" click ADD and type in the address, netmask, and gateway (192.168.0.2 , 255.255.255.0 , and 192.168.0.1, respectively), then by "additional DNS servers" enter the DNS addresses used by your router (use a comma to separate multiple addresses).

Save settings and (hopefully) Viola! Static IP :)

---

### Post by johann-petrak on 2015-07-17
Thank you that does indeed look trivial! :)
(I already configured the router IP range to  use addresses starting at 192.168.0.10 for dynamic addresses)

What I do not understand is why it is better to undo the changes in /etc/network/interfaces? Even if they do get eventually ignored, surely they cannot harm either if the values are the same as what I entered in the network manager? Is there some kind of dependency or relationship between them?

---

### Post by tgalati4 on 2015-07-17
Welcome to the forums.

You can make changes to /etc/network/interfaces--this is the old school method and is still used for servers.  New school method uses Network Manager with a GUI and there is a configuration setting to select how your IP's are managed.  As you discovered, /etc/resolv.conf got changed as well to a new framework that better handles quick changing of wireless networks--such as a laptop moving around.

> 
tgalati4@Mint17 /etc/NetworkManager $ cat NetworkManager.conf 
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=**false**


---

### Post by dieter-erich on 2015-07-21
Hi, I am having the same problem: I cannot set a static IP address in ubuntu whereas it workes under WinXP (without setting the IP range on the router outside the address I want to use). For example, my router is configured to use the DHCP address range 192.168.0.2-128 and my WinXP always connects as 192.168.0.10 (as specified under WinXP and not on the router). I have tried the suggested settings but it simply does not connect. I have to say that I configured the same IP (and MAC) on the router as static address as well but it does not work when specified only on the router, only on the PC, and on both. As was said above: this cannot be so difficult......
Thanks for hints!.

---

### Post by tgalati4 on 2015-07-21
Did you set *managed=true* in /etc/NetworkManager/NetworkManager.conf?

---

### Post by dieter-erich on 2015-07-22
Thanks, 
yes, I set 'manged=true' and outcommented 'dns=dnsmasq'

I also tried (in addition and independently) 
setting the following in 'interfaces' as found somewhere in the net as well:

iface wlan0 inet static (yes, I want to connect via wlan) 
address 192.168.0.11 (this is the same address I have statically assigned to this PC in the router)
netmask 255.255.255.0
gateway 192.168.0.1 (this is the routers address)
broadcast 192.168.0.255
dns_nameservers  8.8.8.8.8.8.4.4 (I do not understand this)

With any of these settings the PC simply does not connect to the router. However, I can connect to a repeater where the PC is assigned the IP address 192.168.0.128 (the first IP address specified in the address range of the repeater).

---

