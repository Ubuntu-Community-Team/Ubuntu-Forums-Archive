---
title: "Extreme memory consumption by NFS server hangs system."
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by K_V_B on 2006-12-02
Hello,

This morning I noticed my server was not reachable over the net. Since this machine has no keyboard or monitor I had to push the power button.
The machine appeared to shut down gracefully, and after a new start I set out to investigate what had happend.

In /var/log/messages I found lots of messages of the following kind:

kernel: [6220761.475991] oom-killer: gfp_mask=0xd0, order=0

This means that the kernel started killing of processes because it had run out of memory. This explains why I couldn't ssh in to the system anymore (as it had been killed) and also explains why the system still made a grafefull shutdown when I pressed the power butten. The system was still up, but most services had been stopped.

I looked at the system statistics "collectd" and noticed that shortly before the system started running out of memory and killing of processes the folling things happened, within the space a few minutes:

- Load went up from the usual 0.1 to over 20.
- Free memory went from +- 200 Mb to 0, and free Swap went from 1,5 Gb, to 0. 
- Disk IO spiked, ethernet traffic spiked too.
- processor usage on both processors went to 100%
- NFS "read" procedures peaked at 1500/s. 


This is a lightly used system. The hardware is a Dell Poweredge server, with dual core Pentium processor, 512Mb ram and three SATA disks. One of the disk contains the OS, the two others are combined using the volume manager into one big disk and exported using NFS. The NFS share is used by a Diskless Linux machine, and by a Apple iMac (one of the new intel ones).

The server OS is Ubuntu dapper, kernel is 2.6.15-26-amd64-server

I have a suspicion that the cause is NFS usage, and that the system that caused it was my iMac. I was copying stuff over to a USB disk from the NFS share at the time. 

So my question is:
- How can I protect my system so that overuse of the NFS server doesn't bring it down. If it is possible that 10 minutes of heavy NFS reading can make the system run out of memory there is something wrong.
- How can I increase the performance of my NFS server. Is there an _up to date_ NFS tuning guide somewhere? (What I found using google was two kernel versions behind...)

Thanks in advance for any help or pointers.

---

### Post by FrodoB on 2006-12-02
As for the apparent memory leak I would recommend switching from kernel to user mode nfs or vice versa.  I had to do this in a Debian Sarge server. At that time kernel mode nfs has a memory leak, but your case may be just the opposite.

You can easily make the change in Synaptic.

---

