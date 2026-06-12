---
title: "WIRED network not working 7.10"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by Sanity N/A on 2007-11-09
ive neve been a great fan of windows and recently i decided it was time to give linux a chance. i was impressed with ubuntu and installed it on a spare computer to get to know it a little better. 

the problem is that whatever i do i cannot get the network to work... 
ive been looking around trying to find a solution but so far ive only found out whats not causing problems, which isnt all bad i suppose but doesnt really give me a solution

this is what i got so far

> Interfaces
auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.1.9
network 192.168.1.0
broadcast 192.168.1.255
netmask 255.255.255.0
gateway 192.168.1.1

> ping 192.168.1.1

	PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

	From 192.168.1.9 icmp_seq=2 Destination Host Unreachable

	From 192.168.1.9 icmp_seq=3 Destination Host Unreachable

	...............

	--- 192.168.1.1 ping statistics ---

	16 packets transmitted, 0 received, +12 errors, 100% packet loss, time 14999ms, pipe 3


running ifconfig eth1 AFTER trying to ping gives
> eth1      Link encap:Ethernet  HWaddr 00:1B:2F:2F:30:A3  

          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::21b:2fff:fe2f:30a3/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

          Interrupt:10 Base address:0xcc00 


> route -n

	Kernel IP routing table

	Destination     Gateway        Genmask         	Flags 	Metric 	Ref    Use Iface

	192.168.1.0     0.0.0.0        	255.255.255.0   	U     	0     	0        0 eth1

	169.254.0.0     0.0.0.0        	255.255.0.0     	U     	1000   	0        0 eth1

	0.0.0.0           192.168.1.1     0.0.0.0         	UG   	100    	0        0 eth1


> sudo ethtool eth1

	Settings for eth1:

	        Supported ports: [ TP MII ]

	        Supported link modes:   10baseT/Half 10baseT/Full 

                                100baseT/Half 100baseT/Full 

  	      Supports auto-negotiation: Yes

 	       Advertised link modes:  10baseT/Half 10baseT/Full 

                                100baseT/Half 100baseT/Full 

  	      Advertised auto-negotiation: Yes

  	      Speed: 100Mb/s

 	       Duplex: Full

 	       Port: MII

 	       PHYAD: 32

  	      Transceiver: internal

 	       Auto-negotiation: on

 	       Supports Wake-on: pumbg

 	       Wake-on: d

 	       Current message level: 0x00000007 (7)

	        Link detected: yes



sudo mii-tool gives
> eth0: no link
eth1: negotiated 100baseTx-FD, link ok


and lastly running: tail /var/log/kern.log just after trying to ping gives me
> Nov 9 18:55:52 DNL kernel: [ 1863.319273] eth1: tx descriptor 3 is 0008a03c.
......[ 1863.319286] eth1: link up, 100Mps, fullduplex, lpa0x41e1
......[ 1875.300484] NETDEV WATCHDOG: eth1 : transmit timed out
......[ 1878.295844] eth1: Transmit timeout, status 0c0005 c07f media 10
......[ 1878.295850] eth1: Tx queue start entry 4  dirty entry 0.
......[ 1878.295854] eth1: Tx descriptor 0 is 0008a03c. (queue head)
......[ 1878.295857] eth1: Tx descriptor 1 is 0008a03c.
......[ 1878.295860] eth1: Tx descriptor 2 is 0008a03c.
......[ 1878.295863] eth1: Tx descriptor 3 is 0008a03c.
......[ 1878.295877} eth1: link up, 100Mps, full-duplex, lpa 0x41e1

any and all help is much appreciated

---

### Post by noob12 on 2007-11-09
First check your the quality of your ethernet cable.  If this persists with a known good cable, it suggests a timing or PCI routing issue.
```

NETDEV WATCHDOG: eth1 : transmit timed out
......[ 1878.295844] eth1: Transmit timeout, status 0c0005 c07f media 10
......[ 1878.295850] eth1: Tx queue start entry 4 dirty entry 0.
......[ 1878.295854] eth1: Tx descriptor 0 is 0008a03c. (queue head)

```

In this case, you might want to try booting with the **pci=noacpi** boot flag.

---

### Post by Sanity N/A on 2007-11-09
cable sholud be fine the other computers have no trouble wehen using it
even a brand new one makes no differens still the same problems

so, how do you set a boot flag?

---

### Post by Sanity N/A on 2007-11-10
adding the boot flag solves everything, i have no problems accessing network or internet
thank you very much

---

### Post by dreamsR4living on 2007-11-12
So, how do you set the boot flag?? I have the same problem too.

---

### Post by sionghua on 2007-11-13
I have the same problem too, not working even though DHCP configured correctly.

---

### Post by noob12 on 2007-11-13
Below I've pasted in some generic instructions on setting boot flags.


**Instructions for one-time boot flag entry**

When booting you'll normally see grub flash a menu of boot options up for a little while.  While it is up  with the default selection highlighted, press **e**, then use arrow keys to navigate to the line that starts with **kernel** and hit **e** again to edit it.  Put the flags at the end of the line, separated from each other and from prior material on that line by space or spaces.  Hit Enter to accept, then b to boot.

To confirm you got the flags entered properly, you should see them if you type
```

dmesg | grep 'Kernel command line'

```
after you boot.

The flags will only apply to that one boot.

**Making the flags permanent**

To make flags permanent (apply to all boots), you need to edit the file **/boot/grub/menu.lst** and find the kernel line corresponding to the boot menu entry you are using and add the options there.  Note that there will typically be some kernel lines that are commented out (preceded by # signs).  You can ignore those.

I suggest that you do not edit this file until after trying boot flags using the one-time per-boot method and establishing that they work and solve an issue.

You will need to be root or use sudo to start your editor.  

**Be careful editing the file**, because editing errors may get you stuck in a situation where you can't boot.   In most situations, you can fix minor errors with a one-time edit for one boot as above.  In the worst case you would have to fix this by booting from the LiveCD, mounting the hard drive, and editing the file.

---

### Post by sionghua on 2007-11-13
Found out my problem is actually because of incomplete realtek driver, fixed by
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
May be helpful for others as well.

---

### Post by dreamsR4living on 2007-11-14
My network is fixed too.

---

