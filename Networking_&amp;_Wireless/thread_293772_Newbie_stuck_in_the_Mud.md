---
title: "Newbie stuck in the Mud"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by pairajacks on 2006-11-05
Troube getting a new PC (loaded with Ubuntu 6.06) on my home (XP) network. To keep things simple, I figured I'd use static IP addresses;
192.168.0.1 for the gateway router
192.168.0.2 for my windows PC
192.168.0.3 for the ethernet adaptor on the motherboard, new Ubuntu PC


If I can get the new PC connected to the internet, I can start using the Package Manager and be on my way. (Everything seems to depend on getting on the internet for download)

First of all, from the Ubuntu menu, Network only shows a modem and wireless connection (not configured). Why doen't the motherboard ethernet show up?

So, following one web site; I tried using commands like:
  ifconfig eth0 192.168.0.2 up   (from root, ie sudo)
Ubuntu didn't recognize this

So.... following another web site; I edited the file etc/network/interfaces, hoping that when I do ifconfig, I'd see eht0. Didn't work; ifconfig continues to show 127.0.0.0

I changed the interfaces file to:

auto
ls loopback

iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1


Now, when I load Ubuntu, it hangs on configuring networks. 

Help.:-?

---

### Post by stream303 on 2006-11-10
Sorry - kind of a shotgun approach here. :)

Is the address range of the router itself really in the 192.xxx range?  Maybe doublecheck the specs...can you access the setup page in the router from your browser?

Be sure the address of the router doesn't conflict with the address of the dsl-modem or other device ahead of it.  I've seen this one before. :)

Be sure to set the gateway as the router address, ie the first device your ethernet card sees beyond itself.

Can you now use your browser to access the setup page in the router?

Later, if you can ping, but cannot browse by url, or it takes a really long time for pages to come up, check your /etc/resolv.conf file and make sure that one of your isp's nameservers are listed at the top.  Since you are running static, it should be easy to just edit that file.  If you later decide to go dhcp, be sure to look at:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)
for common dhcp situations...

Lets see if this helps...

---

### Post by Iowan on 2006-11-10
Perhaps it's just typos, but your **/etc/network/interfaces** file *should* look something like:```
auto lo 
iface lo inet loopback

auto eth0 
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

```

---

### Post by pairajacks on 2006-11-12
1. Yes, The router (Netgear model mr814) address is correct. I can access the router setup page (from my windows machine).
2. Don't have DSL or cable hooked up to the router yet. Just want to get the two PC's to see the router and each other.
-----------------
3. Why doesn't the motherbd ethernet show up? Do I need a driver? What should you see in device mgr? (asus A8N-VM CSM)

---

