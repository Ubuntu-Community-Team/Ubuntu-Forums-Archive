---
title: "[SOLVED] VMWare LAMP server &amp;amp; NAT on an inexpensive Router"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by altonbr on 2007-01-28
I've installed a Ubuntu Dapper 6.06.1 LAMP server running on VMWare player. It's internal IP address is currently "192.168.182.128".

My question is, using an inexpensive router such as my SMC7004ABR, is there a way to do NAT with port 80 on such an IP address? I've heard that to do this sort of procedure, you would need a commercial-grade router. Is that true?

My router gives me the option to change the last digits in the IP only. Example: 192.168.2.___

Maybe a better way around this would be to change the vmnet1 and vmnet8 subnet masks to match my "real" network.

The ultimate goal is to use altonbr.dyndns.org as my "website" and route it to this virtual server.

The reason why I'm using VMWare player and not VMWare server on a seperate box is because I currently only have one box and still need my GUI for day-to-day operations. This was the clearest solution security-wise without compromising my desktop environment.

---

### Post by altonbr on 2007-01-29
The executables I can run are:

vmnet-bridge, vmnet-dhcpd, vmnet-natd, vmnet-netifup, vmnet-sniffer, vmplayer, vmstat, vm-support, vmware-config-network.pl

---

### Post by dmizer on 2007-01-29
you need to bite the bullet and use vmware server.

vmware server is useful because you can configure a network bridge when you install the virtual machine.  that way your virtual machine pulls a network ip that you can forward port 80 to.  then when you run the virtual machine, vmware server makes use of vmware player.  far less of a headache than trying to tweak player by itself.

so vmware server to build your virtual machine, and vmware player to run it (both are a part of the same package when you install vmware server)

just fyi ... NAT = network address translation.  if you have a router, it is already doing network address translation.  your virtual machine needs a network ip (via a network bridge) rather than a subdomain hosted from your primary box (which is the way you currently have it configured)

---

### Post by altonbr on 2007-02-01
I recently found out you just have to change this in your .vmx file:

> ethernet0.connectionType = "nat"

to

> ethernet0.connectionType = "bridged"

then run:

```
$ sudo dhclient
```

To obtain a new IP address from your router.

For example, my broadcast address is 192.168.2.255, which turned my server from 192.168.182.100  (when on NAT) to 192.168.2.103 (when bridged). Now I can successfully NAT from my router on port 80!

Now I just need to figure out a way to launch vmplayer from BASH without launching the GUI. I doubt that's possible, but it would make remote administration a breeze (simply because if I can't launch a virtual server remotely, then I'm "dead in the water").

Anyone know of a executable I can use, or a flag I can tag onto "vmplayer" when launching from a terminal to do so?

---

### Post by shoki on 2007-03-06
> **altonbr said:**
> I recently found out you just have to change this in your .vmx file:



to



then run:

```
$ sudo dhclient
```To obtain a new IP address from your router.

For example, my broadcast address is 192.168.2.255, which turned my server from 192.168.182.100  (when on NAT) to 192.168.2.103 (when bridged). Now I can successfully NAT from my router on port 80!



You guys amaze me! great stuff! I was reading everything on earth. It so cool how simple (and obscure) the solutions turn out to be.

Thank you!

---

### Post by altonbr on 2007-04-22
When you learn more about networking, the fix isn't so "obscure".

---

