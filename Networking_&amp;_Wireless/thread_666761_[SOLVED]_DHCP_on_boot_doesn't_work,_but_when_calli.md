---
title: "[SOLVED] DHCP on boot doesn't work, but when calling ifup manually, it does"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by sqrt2 on 2008-01-13
Hello everyone,

I'm experiencing a strange problem with my WPA-encrypted wireless network. When booting, I do not get any DHCPOFFERs on my wireless interface (eth1). 

[INDENT]kernel: [   50.472298] bcm43xx driver
kernel: [   70.607726] ADDRCONF(NETDEV_UP): eth1: link is not ready
dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
dhclient: No DHCPOFFERS received.[/INDENT]

When I then ifup eth1 manually (after ifdowning it first, avahi-autoipd has assigned the interface a link-local address), I get

[INDENT]kernel: [  128.734046] ADDRCONF(NETDEV_UP): eth1: link is not ready
kernel: [  128.888218] SoftMAC: Open Authentication completed with [...]
kernel: [  129.204129] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
dhclient: DHCPOFFER from [...]
dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
dhclient: DHCPACK from [...][/INDENT]

It looks like WPA authentication only happens when I call ifup manually, not on boot. The authentication is configured in /etc/network/interfaces:
[INDENT]iface eth1 inet dhcp
        wpa-ssid [...]
        wpa-psk [...][/INDENT]
This setup actually worked fine for quite some time, but broke a while ago (probably already when I used feisty, I upgraded to gutsy since).

Does anybody have an idea what could be wrong here and how I can fix it? I wasn't particularly successful with googling, probably because I don't really know what I should be googling for here.

Thanks in advance,
sqrt2

---

### Post by kevdog on 2008-01-13
Put a sleep 20 or sleep 40 statement in your interfaces file before your network configuration statements.  This might give the network time to load other modules first.  Ive seen this problem before, but I dont know what causes it.

---

### Post by sqrt2 on 2008-01-13
Ah, thanks a lot. :) Adding
[indent]pre sleep 20[/indent]
to eth1 in /etc/network/interfaces makes the problem go away.

---

### Post by kevdog on 2008-01-13
Good to know it work.  Sorry about not telling you about the pre part.  Glad you looked that up, shouldnt it technically be 

preup sleep 20
...

---

### Post by sqrt2 on 2008-01-13
Actually, I was just posting the actual line to add for people who stumble upon this thread via Google, I didn't have to look it up anyway. Stupid enough, I posted something different from what I actually did, because
[indent]pre-up sleep 20[/indent]
is correct of course; sorry. I don't think "pre" only would work.

---

