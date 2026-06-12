---
title: "VERY slow NFS speed after starting burst"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by nashant on 2014-01-09
I have a problem with my NFS server. When starting the transfer of a large file (22GB) I get a burst of speed, ~45MB/s. When it reaches ~720MB it hangs. After some investigation with ls -ahl in the target directory, and seeing the temp file steadily grow, it looks like it's taking the server a while to catch up to this, but once it does it carries on and levels out ~6MB/s, sometimes going down below 1MB/s.

Why would it be taking the server so long to write the data to disk, when the client has already sent it? It's not a disk problem because it's a tested, brand new Samsung EVO 840 SSD.

Server:
AMD A6 3.2GHz
8GB PC1066 RAM
Wired GBit connection

Exports:
/ssd 192.168.1.6/255.255.255.0(rw,async,insecure,no_subtree_check)
/data 192.168.1.6/255.255.255.0(rw,async,insecure,no_subtree_check)

Can anyone out there help me speed up this bloody thing???


Edit:

Something else I've just noticed. It's causing the irq/42-iwlwifi process on the laptop I'm transferring from to shoot up to ~10% cpu usage.
Laptop:
Intel i3 3.4GHz
4GB RAM
~240MB/s wifi connection via Centrino N6250 to an Asus RT-N16 running dd-wrt

---

### Post by TheFu on 2014-01-09
Wifi for NFS? Not good.  Can you plug the laptop into a wired ethernet port and try again?

I think your *240MB/s wifi connection* is wrong.  It is probably Mb/s - 8x slower and that is just a reported connect speed, not real-life performance.

Wifi connections are highly variant. Local conditions matter hugely and nobody else's experience will match yours. From second to second, the atmospheric conditions change, which makes wifi connectivity extremely unstable.  For surfing, this doesn't matter. Humans don't see the issue, but file systems need steady, reliable, predictable network connections.

I think the initial speed in your setup is from Linux using RAM for disk buffers. When the buffers are full, the slow performance of the spinning HDD matters. 80-120MB/s is normal for a spinning HDD, but with RAID or a slow interface (like USB2), this can be much slower.

I'm seeing 9.1MB/s for NFS transfers to a VM and from a core i5 NFS server.  Slower read drive - writes to a black WD preallocated VM virtio disk. Wired GigE network. Small memory on the target machine, so OS buffers are not really involved.

Not that it is related, but I'm seeing 11MB/s rsync (over ssh) transfers here to slow USB2 storage. Core i5 and i7 systems. This is over a GigE network with all wired connections.

Is local access to the HDD still fast? i.e. not using NFS?
[http://www.robthomson.me.uk/2011/03/30/tuning-kvm-guests-you-need-to-do-it/](http://www.robthomson.me.uk/2011/03/30/tuning-kvm-guests-you-need-to-do-it/) might be helpful too.

---

### Post by SeijiSensei on 2014-01-09
Well, I'll just say that I use NFS over wifi all the time, particularly between my server and the computer connected to my TV.  Even when I had an 802.11g router, I could stream video just fine. NFS runs rings around Samba for this application.

How are you mounting the NFS shares, nashant?  If it is via /etc/fstab, change the options entry to "defaults,rsize=32768,wsize=32768" and see if that helps.  You're already using "async" on the server, which made a big improvement in speeds for me.

I did some quick tests with rsync; my speeds averaged about 3 Mbytes/sec.  The adapter claims to be running at 72 Mbit.

Wifi is inherently slower than a wired connection because wifi uses a "[half-duplex]("http://www.sysopt.com/showthread.php?174753-Is-WIFI-full-or-half-duplex&p=1223265&viewfull=1#post1223265")" connection, while a wired Ethernet connection is full-duplex.  (In a full-duplex setting communication can go in both directions at once.  A half-duplex connection means that the transmission must stop whenever the client needs to send upstream confirmation packets as in TCP.)

---

### Post by nashant on 2014-01-09
Ok, after extensive testing it looks like the biggest problem is using wifi from ubuntu on the laptop. various tests with dd if=/dev/zero, and rsync.
The active disk in the server is a Samsung Evo 840 SSD, which is internally writing at 260MB/s.

The wired connection here is 100Mbit. Laptop doesn't have a Gbit NIC. All tests were run with `dd if=/dev/zero of=test bs=1M count=2048` as a write to the server, and `rsync -vP <path>/test <path>` in both directions.
Test results:
Ubuntu -> Ubuntu (wired) - r=9MB/s,w=10MB/s
Ubuntu -> Ubuntu (wifi) - r=6MB/s,w=4MB/s(often fails completely)
Debian -> Debian (wired) - r=12MB/s,w=10MB/s
Debian -> Debian (wifi) - r=16MB/s,w=14MB/s

---

### Post by TheFu on 2014-01-10
Thanks for your most excellent post.  These are desktop installations, not server, correct?  "Network Manager" is being used?

---

### Post by nashant on 2014-01-10
Yeah, both desktop installations with network manager in use. Laptop is a work/play machine. Server is file, media and development server. Both need to be desktop installs.

---

### Post by TheFu on 2014-01-10
> **nashant said:**
> Yeah, both desktop installations with network manager in use. Laptop is a work/play machine. Server is file, media and development server. Both need to be desktop installs.

All of my installs are "server", then I add a GUI, if needed on 1 or 2 of them.  Started this when Unity became the default GUI.  Usual add fvwm or LXDE. Network manager does not get installed, which is a blessing AND a curse. There are times when I miss it, but I need/want complete control over which networking is used always when traveling. There are times when connecting to any network just isn't a good idea.

Not that this helps you in any way. ;(

I'm still at a loss for a root cause.

---

