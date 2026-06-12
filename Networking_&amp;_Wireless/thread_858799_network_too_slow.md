---
title: "network too slow"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by cbwaters on 2008-07-13
My XP box and Ubuntu sever are connected ok and I can transfer files but it's VERY slow.  I'm getting like 7-800KB speeds on what should be a 100Mb network.
Between them is a netopia DSL gateway and a new Linksys 10/100 switch.  I took the DSL router out of the loop tonight to see if it was slowing me down but the transfer speeds are the same.
I'm using Samba to share.  
The XP box is a new nvidia onboard NIC and the ubuntu box has an old AMDtek nc100 10/100 NIC.  The Linksys switch says everything connected to it is ful duplex and 100Mbs.
I can drag a folder onto the server drive just fine but it's just hella slow..

Any ideas?
CW

---

### Post by cbwaters on 2008-07-15
bmp

---

### Post by netztier on 2008-07-15
> **cbwaters said:**
> 
Any ideas?


Install **iPerf** from the universe repos on Linux and the Windows binary from [http://dast.nlanr.net/Projects/Iperf/#download](http://dast.nlanr.net/Projects/Iperf/#download).

Then run it between the two boxes and see what your ethernet is capable of - on normal 100Mbps Full Duplex, you should be getting no less than 93Mbit/s.

More often than not, it's the choice of protocols that affects the throughput - are you working with Samba (windows file sharing), NFS (unix-style file sharing), scp/sftp on top of SSH, or FTP?

regards

Marc

---

### Post by cbwaters on 2008-07-15
I'll try those when I get home.  
I'm using Samba.
I really don't know if the problem is with one computer or the other.  I don't have another of either box to try data transfers with.

CW

---

### Post by cbwaters on 2008-07-15
wow, I don't even know what I'm supposed to do with iperf...  What the heck is it?

---

### Post by netztier on 2008-07-16
> **cbwaters said:**
> wow, I don't even know what I'm supposed to do with iperf...  What the heck is it?

It's a command-line tool that can either be run as "server" (weirdly enough the *receiver* of the data stream) or "client" (the *sender*). To do a throughput test, you must run two instances of iPerf on two systems in your network, obviously.

```

server/receiver: **iperf -s** 
client/sender:   **iperf -c <server ip> -t 30 -i 5**

```

Results will be reported by the iperf instance running as client. With the above example, the throughput test will run for 30 seconds (-t 30) and will report at 5-seconds intervals (-i 5).

Make sure that you turn off any firewalls on the systems involved - or configure them to allow communication on tcp/5001 in- and outbound.

Set sender and receiver roles the way you observe the "slow" data transfers in your network, then try the opposite to see if it makes a difference.


regards

Marc

---

