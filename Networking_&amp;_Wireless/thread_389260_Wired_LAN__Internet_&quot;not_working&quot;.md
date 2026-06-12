---
title: "Wired LAN / Internet &quot;not working&quot;"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by redeemer on 2007-03-20
Hi,

I have been following this thread closely: [http://ubuntuforums.org/showthread.php?t=387600](http://ubuntuforums.org/showthread.php?t=387600), my problem is very similar. Reason I am posting this new thread is that the output of *ifconfig* for me is quite different (see attachment).

**The Issue**
I booted Ubuntu 6.10 from the Live CD, and everything seemingly worked. I could connect to the internet (Firefox, GAIM, xchat, etc.) without any problems. I then installed the operating system fully to HDD, and cannot access the internet from it (I can still access the internet from the Live CD version). I have attached the output for *ifconfig* and *dmesg* to this post.

**Attempted Solutions**
After seeing that DHCP didn't work, I tried setting up a static IP by providing the Gateway and Subnet - still no good. I have attached a screenshot of my eth0 properties.

Can anyone help? :) Would be muchly appreciated! Let me know if you need me to provide any more info.

Thanks,
Tom

---

### Post by redeemer on 2007-03-20
Some extra potentially useful info: Ubuntu has prompted me to dowload ~140 software updates. Surely it only knows about these because it got the information from a remote server at some point (over the internet)?!

---

### Post by Mr. C. on 2007-03-20
You actually have a different NIC than the OP in the link above.

You have a VIA Rhine II, which is the same chip as:

[http://ubuntuforums.org/showthread.php?t=388402](http://ubuntuforums.org/showthread.php?t=388402)

Your dmesg output shows you have an eth0:
> 
[17179592.648000] eth0: VIA Rhine II at 0x1e300, 00:40:d0:57:d3:c7, IRQ 201.
[17179592.648000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.

but then your ifconfig is missing eth0.  I see that you have two NICs.  Try to use Network Manager to disable the second one (eth1),  and then enable the first one.

If that fails, try this from a terminal window:

```
sudo ifdown eth1
sudo ifdown eth0
sudo ifup eth0

```

If that fails, provide output from
```
sudo lspci
sudo lspci -class network
sudo lsmod

```
MrC

---

### Post by redeemer on 2007-03-20
Hi Mr C, thanks for your quick response.

This command connected me to my network (and internet works! Woohoo): 

sudo ifup eth0

Will this fix the issue permanently? Or will I need to do this every time I boot up/login (not ideal)? If the answer to the latter is "yes", is there anything I can do?

Cheers,
Tom

---

### Post by Mr. C. on 2007-03-20
Excellent!

It may not be a permanent fix.  You may have encountered the bug I investigated this morning.  Look at my last post for a summary:

[http://ubuntuforums.org/showthread.php?t=387319&page=2](http://ubuntuforums.org/showthread.php?t=387319&page=2)

MrC

---

### Post by redeemer on 2007-03-20
Alright, cheers!

*plods off to sort out ATI Radeon 9600 drivers...*

---

### Post by redeemer on 2007-03-21
Just to keep people informed, I'm having to use the *sudo ifup eth0* command every time I boot up/login to get online. Is there a way I can file this as a bug report (assuming it is a bug)??

---

### Post by Mr. C. on 2007-03-21
This is a known bug/limitation in Network Manager.  If you have two NICs, and you use Network Manager, you must select one, and disable the other.  If both are selected, one will be chosen as up, and the others will be brought down.

MrC

---

### Post by sageb1 on 2007-10-10
i had  a similar problem after moving my HD to a new box (from HP e-PC to e-Vectra).

it detected the new nic as eth1 and disabled the non-existant eth0.

After fixing DHCP, it bound eth1 to the IP number.

---

