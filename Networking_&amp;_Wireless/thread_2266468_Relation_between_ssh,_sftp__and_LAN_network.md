---
title: "Relation between ssh, sftp  and LAN network"
date: 2015-02-23
forum: Networking &amp; Wireless
---

### Post by spacexion on 2015-02-23
Hi everybody,

I'm not a Linux specialist so please be patient if my explanations are not totally clear :)

This is not a great issue nor a real problem, but I would really appreciate to understand some network and linux topics, maybe you can help me.

My question involves 5 machines on my lan:

**R00 **> Router: Trendnet N450 + gigabit ethernet
**L01 **> My personal laptop >>>> Ubuntu 14.04, connected to LAN through wireless
**L02 **> A linux box for remote LAN administration, OwnCloud, PLEX server, etc... >>>> Lubuntu 10.04, connected to LAN  through gigabit ethernet
**L03**  > A clone of L02 >>> Lubuntu 10.04, connected to LAN through gigabit ethernet 
**W04 **> A NAS/file server, hosting all my media files >>> Windows 7 connected to LAN through gigabit ethernet

L02 is a test machine I configured as a server, but I underestimated  certain aspects so I'm now migrating this machine to its clone L03 which has got  more powerful hardware.

After cloning, I had to move certain media files from L02 to L03 and this is what I did:
- I connected remotely to L03 (eth) from L01 (wireless) with ssh
- within ssh session, I started an sftp session from L03 (eth) to L02 (eth)
- within sftp, I copied files from L02 to L03

There were about 40GB of data to move, so while the copy was running, I started to listen to some MP3. To do this, I opened wireless a share on W04 from L01. 
Well, the wireless network was totally stuck and the MP3 files can't play on my laptop.
I went back to my terminal windows connected through ssh and I noticed that the file copy between L02 and L03 was abnormally slow. Certainly not what I could expect from a gigabit connection.
I was on a hurry so I did not have time to deeply inspect what was going on. I just canceled the file copy. Then I physically went to L03 (instead of ssh), logged in on the machine locally, and started again the file copy from L02 to L03 through sftp. Now everything seemed to work fine: file copy was fast, and I was able again to stream music from W04 to L01.

I am little bit confused about what happened here.
As I opened an ssh session on L03 and then the sftp session between L03 and L02, I expected to have a direct data transfer through ethernet between these 2 machines. From my point of view, remote command started in ssh (L01 to L03) should be executed locally on L03 (such a kind of a "remote desktop" thing...).
Actually, it seems instead that data was transferred wireless from L02 to L01, then forwarded again from L01 to L03, totally dragging down my wireless network.

Does anybody can explain me what happened?

Thanks a lot!

---

### Post by tgalati4 on 2015-02-23
Just because a router is gigabit does not mean you get gigabit performance between ports.  The backplane bandwidth of the router determines how much throughput you will get between one port and another.  The protocols used between the machines will also dictate the speed and overhead of the transfer.

It's possible that the CPU of the router got overwhelmed.  If you installed another firmware (such as dd-wrt or openwrt) on the router, you could see the CPU load and free RAM on the router.  When you run out of one or the other, the bits will cease to flow.

You obviously found a Use Case for which your router does not handle well--Using wireless to stream an mp3 file from Machine A to Machine D while Machine B is copying a 40 GB file to Machine C.

Solving this type of problem requires *decomposition*--break the big problem into a series of smaller problems to solve.

Turn off wireless.  Plug in your laptop with an ethernet cable.  Perform the same set of steps.  Note the behavior.  Don't cancel the file transfer.  Let it continue and log into the other machines and get their statistics with *htop*.  How long does it take to transfer a 40GB file over your network?  How long while streaming an mp3?  Why are you using *ssh* and *sftp*?  Why can't you just use *scp* and specify both machines?

```
man scp
```

Next, using the wired laptop, log into the router and monitor the status page.  Most routers have a log file.  Clear it and run your tests, then download the log file.  Examine the "Status" page during the transfer and while trying to play music.  It's possible that your Win7 box is flooding the network with resent packets because of latency--or because that is just how Windows is.

Now unplug the Win7 machine and repeat your steps but this time, stream a music file (the same file perhaps) from one of your Linux boxen.  Note the performance differences.

If everything looks OK, then set a Quality of Service (QoS) that improves mp3 streaming--but at the expense of slower file transfers.

Without any data, it's hard to figure out what is going on.

---

### Post by TheFu on 2015-02-23
Most home router backplanes are 2-3x the port speeds. It has been that way for years.

WiFi sucks.  Avoid whenever possible. The computer sees the connection fluctuate all over the place with wifi. To a human, it seem fine, but that is never the real connection situation. There is always interference from other devices, neighbors.

I completely agree with 2 of tgalati4's suggestions:
* simplify and test.  Capture real data using real bandwidth tools like iperf.  See if the encryption matters or if it is the connectivity. Wired NICs don't alway provide the stated bandwidth - many of the cheap GigE NICs or onboard chips only do 300Mbps, for example.
* While I like ssh, and sftp, for UNIX to UNIX transfers, scp is more efficient.  Also, if these systems will only communicate inside the LAN, you might want to use a less-strong crypto module as the default. If you like, using rsync will actually use scp by default, so that can be easier when there are multiple files.  [http://www.cyberciti.biz/tips/sshd-server-optimization.html](http://www.cyberciti.biz/tips/sshd-server-optimization.html) has tuning ideas.
* On the Win7 box, WinSCP is a nice client.

Inside my LAN, I'm lazy and use NFS to transfer files. It is fast because it doesn't use encryption (v3). Might that be an option for a longer term solution?

---

