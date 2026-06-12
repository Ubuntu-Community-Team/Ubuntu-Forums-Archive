---
title: "NIC using IP100A chip not installing on Ubuntu 12.04"
date: 2015-07-06
forum: Networking &amp; Wireless
---

### Post by phil215 on 2015-07-06
The PC might be a clunky old thing operating on RAMBUS memory, but at least it can run WinXP without complaining.
 When I introduced it to Ubuntu in April last year it refused to configure the NIC.
 It was left as a 'work in progress' until now! (Clearly, the machine and it's problems are very low priority.)
 However, today I spent some time revisiting the problem and found that issuing a networking restart produced two errors, as follows:

 ```

 ifdown: failed to open lockfile /run/network/.ifstate.lock  Permission denied
 ifup: failed to open lockfile /run/network/.ifstate.lock  Permission denied
 
```
 
 I looked in the directory and didn't see any such lockfile.
 Does this mean it's expected, but not present?
 Surely, that would produce a 'not found' error, not 'permission denied'.
 Is the lock file hidden from view? – I find these error messages a little confusing.
 
Investigating the hardware inventory with lshw shows no driver has claimed the Ethernet controller.
 So, it looks like the Ethernet driver has failed to install.
 What steps must I take to get the NIC working under Ubuntu?

 For the record, the machine has an MSI motherboard type MS-6339, and the NIC is a TP-Link model TF-3200. Over the past 15 months I've successfully installed this model of NIC in three different computers, but this one is limbering up to become a very hard-won fourth!

---

### Post by chili555 on 2015-07-06
'Permission denied' usually indicates that the command needs sudo. Did you try:```
sudo ifup eth0
```...or whatever?
> Investigating the hardware inventory with lshw shows no driver has claimed the Ethernet controller.
So, it looks like the Ethernet driver has failed to install.
What steps must I take to get the NIC working under Ubuntu?What have you tried so far? May we see a bit more information about the card?```
lspci -knn | grep 0200 -A2
```Thanks.

---

### Post by phil215 on 2015-07-06
Thanks for your reply chili555. The machine in question is located elsewhere so I can't try your suggestions immediately. I'll try to post the outcome as soon as possible - hopefully before sundown on 7th July.

---

### Post by phil215 on 2015-07-07
The output of chili555's suggested lspci command is:
```
02:00.0 Ethernet controller [0200]: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY [13f0:0200] (rev 31)
    Subsystem: Sundance Technology Inc / IC Plus Corp Device [13f0:0201]
    Kernel modules: sundance
```

So, the NIC is recognized but no driver is installed, as evidenced by:
```
sudo ifup eth0
```
which failed with: Cannot find device "eth0". Failed to bring up eth0.

I can confirm that the file etc/network/interfaces contains:
```
auto eth0
iface eth0 inet dhcp

auto lo
iface lo inet loopback

```

In view of this problem and general speed restrictions during usage I've decided to upgrade the motherboard to one that's more Ubuntu friendly.
It's expected to arrive by the end of the week.
However, it would be good to nail this particular network setup problem for the benefit of others.

---

### Post by chili555 on 2015-07-07
It has a driver, sundance, it appears. Let's gather a bit more data:```
ifconfig
dmesg | grep -e sundance -e eth
```Thanks.

---

### Post by phil215 on 2015-07-09
Okay chili555, here's some more data:
Output of ifconfig:
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12616 (12.6 KB)  TX bytes:12616 (12.6 KB)
```

So, only the loopback connection is available, so far.
I wonder what went wrong with the eth0 setup?

Output of dmesg | grep -e sundance -e eth
```
[    6.173848] sundance.c:v1.2 11-Sep-2006 Written by Donald Becker
[    6.173906] sundance 0000:02:00.0: enabling device (0114 -> 0117)
[    6.173924] sundance 0000:02:00.0: found PCI INT A -> IRQ 10
[    6.174673] eth0: IC Plus Corporation IP100A FAST Ethernet Adapter at 00012000, 00:23:cd:00:2f:85, IRQ 10.
[    6.183462] eth0: No MII transceiver found, aborting.  ASIC status 63

```
This is interesting. The NIC is assigned to IRQ 10, but the final line shows the driver installation is aborted.
The reason "No MII transceiver found" is puzzling as I didn't think this particular NIC had one anyway!
If it does, then presumably it's faulty.
What's the next step? Substitute this NIC for a known good one?

Btw, the replacement mobo arrived earlier than expected and within a couple of hours I had it ready to install Ubuntu.
The onboard LAN port connected to the Internet straight away, without a hitch.
What's the make and model of this Ubuntu-friendly mobo? It's an Intel D946GZIS.

---

### Post by chili555 on 2015-07-09
>  then presumably it's faulty.
What's the next step? Substitute this NIC for a known good one?Exactly.> What's the make and model of this Ubuntu-friendly mobo? It's an Intel D946GZIS.As far as I can tell, the Intel D946GZIS is a microATX motherboard of circa 2006 vintage.  [http://downloadmirror.intel.com/15108/eng/D946GZIS_ProductGuide02_English.pdf](http://downloadmirror.intel.com/15108/eng/D946GZIS_ProductGuide02_English.pdf)

[http://www.intel.com/support/motherboards/desktop/d946gzis/sb/CS-026620.htm](http://www.intel.com/support/motherboards/desktop/d946gzis/sb/CS-026620.htm)

---

### Post by phil215 on 2015-07-12
Thanks for finding documentation for the new mobo chili555, that's a great help.
The only thing that I forgot to mention about the original post is that the computer in question is perfectly capable of connecting to the Internet under WinXP using the same NIC that fails under Ubuntu. I find that very puzzling.

I wonder if you saw my earlier post (now 6 days old) called "[SIZE=2]Network settings not retained after NIC change on Ubuntu 12.04[/SIZE]"?
No one has replied to this one, yet I'm sure the solution to the problem is very easy.
I wonder if you know which file I need to edit in order to make that computer connect without intervention.
Please give it a look if you missed it!

---

