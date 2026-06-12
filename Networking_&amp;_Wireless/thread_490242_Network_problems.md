---
title: "Network problems"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by jonttix on 2007-07-02
When I try to start system -> administration -> network the window comes up but it is no text or anything in it only a white rectangular. And many of my other programs is allso very slow. Can anybody help mee?

---

### Post by milton1 on 2007-07-02
It sounds like either a graphics problem or, more likely, that your system is having memory issues. How is your memory usage? ```
free -m 
```

---

### Post by jonttix on 2007-07-02
This is the output:

             total       used       free     shared    buffers     cached
Mem:          1002        626        376          0         12        293
-/+ buffers/cache:        320        682
Swap:         4149          0       4149

---

### Post by milton1 on 2007-07-04
Hmm... Does not appear to be a memory issue, as you have plenty of free memory (though it is still possible that you have a bad stick of RAM). Does the network window ever fill in, or is it always remaining blank? Do you have something else hogging your processor power? "top" will give you a list of running processes, and might show what is sucking up your machine's abilities.

It could also be a bad NIC, or bad software for the NIC.

```
 sudo ifdown -a 
```

will bring down all of your network interfaces, then maybe you can try and configure them and bring them back up with ifup.

Good luck!

---

### Post by jonttix on 2007-07-04
sudo ifdown -a gave following:

/etc/network/interfaces:15: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"

the interfaces file:

auto lo
iface lo inet loopback


iface eth1 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto eth1
iface eth1 inet dhcp

any help?

---

### Post by dbott67 on 2007-07-04
There's a duplicate eth1 interface listed (not sure if that would cause the problem though).  Try removing or commenting out the line that I've noted below:

```
auto lo
iface lo inet loopback


[I][COLOR=Purple]# iface eth1 inet dhcp
[/COLOR][/I] 

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto eth1
iface eth1 inet dhcp


```

-Dave

---

