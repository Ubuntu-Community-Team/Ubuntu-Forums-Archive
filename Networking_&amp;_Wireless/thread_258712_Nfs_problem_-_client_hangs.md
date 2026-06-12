---
title: "Nfs problem - client hangs"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by Mr.Hulot on 2006-09-16
Hi. I am trying to share file between my desktop pc and my laptop using an ethernet connection. The configuration is as follows:

my desktop pc has internet through a wireless card and shares it with the laptop through its ethernet card. The desktop runs Ubuntu 5.10 while the laptop runs Ubuntu 6.06. The internet sharing works like a charm.

In the ethernet network I have assigned to desktop the IP 193.168.0.1 and to the laptop the IP 193.168.0.5

I use firestarter for the sharing process. Next I wanted to be able to mount through NFS certain directories of the desktop to the laptop. By searching the net I found several guides describing this procedure. So I installed the necessary tools on both pcs. I exported the directories from the server, and mounted the on the laptop. Everything works like a charm until the moment I try to copy/read large amounts of data from the desktop share using the laptop. For example I am copying a directory with mp3s from the desktop, it copies the first 2-3 songs and then it hangs...
And when I say it hangs it hangs ... The copying process hangs and I lose all communication between the 2 pcs. I lose internet sharing and i cannot even ping from/or to the laptop (not even in broadcast adress).

In the laptop I get the following dmesg:

[17180015.224000] NETDEV WATCHDOG: eth0: transmit timed out
[17180015.224000] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[17180015.224000] eth0: Tx queue start entry 4  dirty entry 0.
[17180015.224000] eth0:  Tx descriptor 0 is 0008a04b. (queue head)
[17180015.224000] eth0:  Tx descriptor 1 is 0008a062.
[17180015.224000] eth0:  Tx descriptor 2 is 0008a062.
[17180015.224000] eth0:  Tx descriptor 3 is 0008a04b.
[17180015.224000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17180015.224000] eth0: Promiscuous mode enabled.

and my lspci output for the laptop and desktop are:

laptop:

0000:09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

desktop:

0000:01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)

I suspect that the network 'fills up' and hangs ... I tried to resize the blocks but with no result and also using read only mode...

Any help would be appreciated , thanks

---

### Post by Mr.Hulot on 2006-09-21
Since the last time I did a fresh install of ubuntu dapper on the desktop but with no luck, so I guess it is not a matter of software (nfs versions) but of hardware. All the solutions on the net say to try a different rsize/wsize but I had no luck when I changed them ... Any ideas? 

If in the end I dont get this to work, I am thinking of going through samba. What is the tranfer rate then? Does it only depend on hardware or the protocol itself has limitations?

---

### Post by dvarsam on 2006-12-05
Hello!

Can you provide the _exact_ steps you performed to Setup NFS.

Also, the packages that you installed to set it up.

Thanks.

---

### Post by FrodoB on 2006-12-05
Have you tried flushing your firewall to see if it works afterwards:

 sudo iptables -F
 sudo iptables -L

Then run you copy to see if you get the same results.


It could be a firewall issue.

You also may want to try user mode NFS if you are using Kernel mode or vice versa.

---

### Post by doquar on 2006-12-15
I have had the exact same problem and it took me a long time to figure it out.

This part about overflow of fragmented on the nfs howto: 
[http://nfs.sourceforge.net/nfs-howto/ar01s05.html#fragmented_packets]("http://nfs.sourceforge.net/nfs-howto/ar01s05.html#fragmented_packets")
is what made me realize what was happening.  I do think lowering the rsize and wsize could help, but what fixed it for me was increasing /proc/sys/net/ipv4/ipfrag_high_thresh and /proc/sys/net/ipv4/ipfrag_low_thresh.  ipfrag_high_thresh specifies only 256KB for assembling fragmented packets, which is pretty small. I don't know exactly how much you should increase them by, but I would first try to at least set ipfrag_high_thresh to 524288 and ipfrag_low_thresh to 393216.

You can do this by:

```

echo 524288 > /proc/sys/net/ipv4/ipfrag_high_thresh
echo 393216 > /proc/sys/net/ipv4/ipfrag_low_thresh

```

If this works for you and want this change to be permanent, then add the following to /etc/sysctl.conf:

```

net/ipv4/ipfrag_high_thresh=524288
net/ipv4/ipfrag_low_thresh=393216

```

If you are still having connection problems, try increasing the values even more.

---

