---
title: "SSH problem: Can ssh through ip address, but not computer name/hostname"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by jfenwick on 2006-11-21
Hi there,

I'm using Edgy Eft, 6.10, and I'm having a problem with ssh.

If I ssh directly to the ip address of this computer (ie, [email]root@xxx.xx.xxx.xx[/email]), I can ssh into the bot, but if I try to use the hostname (ie, [email]root@mycomputer.mynetwork.org[/email]) then it doesn't work.

When I go into System | Administration | Network Settings | General, I see that Host Name is correct, but Domain Name doesn't seem to be set, could this have something to do with it?

---

### Post by Frobber on 2006-11-21
I have found the easiest way to associate names and IP addresses, for home networks, is to add the IP address and hostname.network in the Static Hosts section of your network settings. 

After the change, reboot and try to connect using the hostname.:-?

---

### Post by jfenwick on 2006-11-21
Frobber, can you explain this in slightly more detail?

What I assumed you meant is to go System | Administration | Network Settings | Hosts and add my ip address with the hostname.network.

I tried that, didn't work. Rebooted, tried again, still didn't work.

I don't really understand why this would even work, because I would assume this creates an alias for your computer, not the computer that is trying to connect to you.

Also, this isn't a home network, it's a corporate network.

If anyone else has a suggestion let me know.

---

### Post by Frobber on 2006-11-22
For the 'host' computer you do not need to do anything because you are able to get to it via IP address.

If you problem is like the one I had, I could see the host. An icon would appear when I attempted network connect, the hostname was under the icon. If I clicked on the icon I would get hostname not found. I could connect by using the IP address in the finder field of the browser but not by using hostname. 

So for the network settings in the 'client' I added the setting for the 'host' computer in my static host network settings. I used the same format as other addresses in the list (mostly identifying the computer I am working at - 127.0.0, etc). 

The down side of this is when using DHCP you need to boot the computers in a sequence that ensures each has the address you expect.

A fairly good description for networking files and such can be found at HMUG.org. I have found their site useful in explaining some networking concepts.

---

