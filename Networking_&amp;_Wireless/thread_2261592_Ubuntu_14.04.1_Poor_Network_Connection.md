---
title: "Ubuntu 14.04.1 Poor Network Connection"
date: 2015-01-20
forum: Networking &amp; Wireless
---

### Post by Fmt662 on 2015-01-20
Hi all,

I have 2 servers running in my house both running 14.04.1.

One is a dell 1950 with twin network connections, one to my cable modem and the other to a switch, and is acting as my router.
The other is a supermicro with twin connections bonded together using LACP. My switch is configured properly for LACP and is working great streaming data to my home network.

The problem is that the 2 servers won't talk well to each other.

From my laptop using iperf i can communicate with both servers at 850+ mbits, which isn't bad on a gigE network with 2 switches between my laptop and the servers. But iperf between the servers sits and hangs. Mounting NFS or SMB shares between is barely functional. Download speed at my storage server are slow, 16 mbit on a 50mbit connection. Netstat shows no bad packets on either box.

I've tried to google this but haven't found many posts for issues that appear only between ubuntu servers but not outside devices.

Any help would be appreciated.

Thanks!

---

### Post by TheFu on 2015-01-20
Test and simplify until you find the issue.
Try different ports on the switch, on the server.
Try different cables.
Try a different switch.

Test after each change, hoping to isolate the problem.

Of course, this assumes the network settings and logic there is correct. Obviously, we can't help on that without you posting all the relevant data.

---

