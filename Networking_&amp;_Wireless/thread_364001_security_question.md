---
title: "security question"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by gaillard on 2007-02-17
Hi guys,

I am on a university network, and the absolutely only way I can connect to this thing is just direct wire.  I am running Ubuntu obviously and am wondering what other people can see.  I noticed the other day that I can see 20 or 25 people in the network servers.  To them can they see me?  I assume that if they tried to access me they would need a username and pass right?  This isn't like a unix environment of folders is it, where the folders have to have their permissions closed or people can view them?

Thanks!

---

### Post by gradedcheese on 2007-02-17
They can "see" what Windows advertises via Netbios (ie: Share Folders, printers, etc).  If you don't have Samba (windows file sharing) enabled, then there's nothing for them to 'see' this way.  Their network administrator can see the addresses handed out by the router and any names the PCs advertise, but that's about it.

By default, Ubuntu doesn't ship with anything that others can connect to.  The notable exception is the cups printer daemon. It allows them to connect and see your printer queues (ie: names of documents printed) but nothing else really.

---

### Post by gaillard on 2007-02-17
Awsome, thanks for the info, just what I was wondering.  

Oh, I have vmware server running with NAT, I guess I should turn off netbios then ?

---

### Post by gradedcheese on 2007-02-17
I don't think it will matter, if you're running Windows inside VMWare, it should suffice to turn off Windows when you don't want it to be 'seen'.  You could also un-bridge the virtual network interfaces (available inside VMware's options), and so on.  I can't remember what you'd do within Windows, but disabling Netbios would probably work.

---

### Post by gaillard on 2007-02-17
Well actually all I have selected in VMware is NAT no bridging, is NAT showing anyone anything?  Sorry I should probably ask that on the vmware forums...

---

