---
title: "Need Help With DHCP On Ubuntu 6.10"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by Zyck_titan on 2007-08-15
I've just Gotten Ubuntu on My box, and setup was albeit a little painful, so I wasn't expecting setup to be any better, and it wasn't, so what I really need is to set up my wired connection for my Linux machine, I think I can do pretty much everything afterwards, but I just need the wired connection.

Kind of a roadblock ](*,)

---

### Post by heimo on 2007-08-15
> **Zyck_titan said:**
> I've just Gotten Ubuntu on My box, and setup was albeit a little painful, so I wasn't expecting setup to be any better, and it wasn't, so what I really need is to set up my wired connection for my Linux machine, I think I can do pretty much everything afterwards, but I just need the wired connection.

Kind of a roadblock ](*,)

If you have a question somewhere there, you will need to provide a lot more information before anyone will be able to give you specific advice. 

Go to System->Administration->Network and setup your network.

Try running sudo dhclient eth0 on command line.

---

### Post by noob12 on 2007-08-15
Do you mean you've got the wired ethernet working but you are not able to get a DHCP address assignment?

Does **ethtool eth0** (substitute the actual interface name if it is not eth0) show that you have a link established?

Does **sudo lshw -C network** show your device with a driver assigned?

If you have no connection on the box right now, you should try to find a flash drive so that you can transfer files to and from the box until you get the network working.  In particular, we'll probably need various outputs you grab so we can help diagnose the problem.

It would be useful if you could post the output from
```

lspci -nn

sudo lshw -C network

ifconfig -a

# assuming eth0 is your ethernet interface
ethtool eth0

```

If you need instructions for setting up a static IP, let us know.

---

### Post by Zyck_titan on 2007-08-15
I think I found a workaround, using my windows computer to find all the DNS server info as well as netmask and IP address

---

### Post by noob12 on 2007-08-15
Try to pick a different IP address from the windows box, in the same subnet, but preferably in a range not used by your router/server for DHCP.

---

