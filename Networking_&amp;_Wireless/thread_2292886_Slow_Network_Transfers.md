---
title: "Slow Network Transfers"
date: 2015-08-31
forum: Networking &amp; Wireless
---

### Post by cranerja on 2015-08-31
I have a 5e network with a file server and a client where I am only getting around 10 MB/s for file transfers. What am I doing wrong?
Running ubuntu 14.04 on both machines.

---

### Post by SeijiSensei on 2015-09-01
Are you using Samba or NFS?  NFS is the better choice for an all Linux network.  For maximum speed, you need to use the "async" parameter in the share definition in /etc/exports.

---

### Post by tgalati4 on 2015-09-02
Try making the mount between the machines in /etc/fstab, that seems much faster than using a Network mount in Nautilus.

---

### Post by papibe on 2015-09-02
Hi cranerja.

It looks like something in the way is only 100Mb/s.

Could you confirm that both machines have gigabit ethernet? You can do this with this command:
```
sudo ethtool eth0
```
Could you check the specs of your router or switch and make sure it has gigabit ports?

If all that checks out, I'd recommend making an iperf test ([here]("http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes")'s how).

Let us know how it goes.
Regards.

---

### Post by cranerja on 2015-09-13
> **papibe said:**
> Hi cranerja.

It looks like something in the way is only 100Mb/s.

Could you confirm that both machines have gigabit ethernet? You can do this with this command:
```
sudo ethtool eth0
```
Could you check the specs of your router or switch and make sure it has gigabit ports?

If all that checks out, I'd recommend making an iperf test ([here]("http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes")'s how).

Let us know how it goes.
Regards.

Thanks for the answer, and it turns out I am only on 100Mb/s. Silly mistake on my part. Thanks for the info!

---

### Post by tgalati4 on 2015-09-13
100 Megabits/sec ethernet speed (100BaseT) is 100/8 bits per Byte or 12.5 MegaBytes/second maximum throughput.  With networking (TCP/IP) overhead, 10 MegaBytes/second is about right.  If you have a lot of network traffic, then you would experience 5 MB/sec.

---

