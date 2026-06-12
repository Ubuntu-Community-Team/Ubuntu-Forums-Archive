---
title: "[SOLVED] Please help setting up routing"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by radarman on 2008-07-31
Hello, I could use some help from you linux experts with setting up routing on my home network. The network looks like this:

```


            internet                      internet
               |                             |
            [modem]                       [modem]
               |                             |
               |                           eth0
               |                    [  linux router  ]
           [netgeat]                eth1          br0
          192.168.1.1          192.168.1.2    192.168.10.1
           /        \              /                   \
          /          --------------                     \
    192.168.1.5                                   192.168.10.10
	 
	 

```

I have setup a static route on the netgear router with network address being 192.168.10.0, netmask 255.255.255.0 and gateway being 192.168.1.2.

On the linux router, the routing table looks like this:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.10.0    *               255.255.255.0   U     0      0        0 br0
72.XX.XX.0      *               255.255.252.0   U     0      0        0 eth0
default         cpe-72-XX-XX-XX 0.0.0.0         UG    0      0        0 eth0

```

The situation is like this. The linux router can see every computer and the netgear router. 192.168.10.10 can see the linux router and the netgear router, but cannot see 192.168.1.5. Likewise, 192.168.1.5 can see netgear and the linux router, but cannot see 192.168.10.10. I really want 192.168.1.5 and 192.168.10.10 to talk to each other without changing my network setup. Please help.

---

### Post by bab1 on 2008-07-31
Why are you bridging 192.168.10.1?  The idea of routing is to pass packets between separate networks.  Have you set up routing or are you just using it as a bridge?  If you route then you will need metrics to keep the traffic destined for 192.168.1.0 from leaving via eth0

---

### Post by radarman on 2008-07-31
Fixed it!

Netgear router was to blame. Updated the firmware and the static route works perfectly.

Having a bridge interface on the linux router was indeed my intent. It's a few ethernet ports and a wireless access point bridged together. I still want to keep it separate from the computers on the netgear network. Hence i need routing to pass things between the two :)

---

### Post by bab1 on 2008-07-31
Don't 'ya just hate that!  All the thought and self doubt and then bam it's fixed mby something out of your control.  What made you think of firmware?

Let's make this one solved, so others know.

---

### Post by radarman on 2008-07-31
Well, the static route page on the Netgear router seemed a little janky. For example, it wouldn't let you add a single host, saying that submask 255.255.255.255 was invalid. I thought it was strange that you couldn't add a single host, especially when the page's help says you can. The updated firmware turned out to have none of these problems. The router is a cheap off the shelf Netgear WGR614v6, if anyone is curious.

Now then, onto windows file sharing across different subnets! Also, should probably make sure that routes on the linux box stay as they are even after I reboot.

---

