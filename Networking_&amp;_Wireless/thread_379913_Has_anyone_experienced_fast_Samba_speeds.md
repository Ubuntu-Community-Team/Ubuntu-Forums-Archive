---
title: "Has anyone experienced fast Samba speeds?"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by btboudreaux on 2007-03-09
Because I would like to know your secret!

I have two Ubuntu workstations, both running Samba. The Desktop has gigabit ethernet connected to a gigabit switch. The laptop is 100Mbps.  I should have at least (or close to) a 100 Mbps (12.5MBps) transfer rate but I get 3-3.5MBps. It's extremely slow when transferring large files. When both workstations were Windows based, the transfers went with blinding speed. 

I've read all the post and tried different things but nothing is speeding up samba. I've mounted with nautilus, with smbfs, I've checked to see if my ethernet was running Full Duplex at 100Mbps, I've changed the buffer sizes.

I'm just wondering if anyone who is transferring samba to samba has had 100Mbps or 1000Mbps speeds because I sure aint.

---

### Post by Mr. C. on 2007-03-09
I just copied a 14.5meg file Windows->Samba in about 2 seconds.  Are you troubles bi-directional, or uni-directional ?

You will not get 12.5MBps, as there is overhead in the connection.  You might approx 10, but you can expect much higher speed than 3-3.5.

Don't start tweaking Ethernet and network settings you don't understand.  The Linux kernel has very fast Ethernet and is tuned quite well.

Some global Samba options recommended are:

socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

This should be sufficient.  You clearly have a 100mbit connection, because you won't get 3-3.5Mbit on a 10Mbit network, so that's not the trouble.

Give me an update,
MrC

---

### Post by netztier on 2007-03-09
> **btboudreaux said:**
> I've read all the post and tried different things but nothing is speeding up samba. I've mounted with nautilus, with smbfs, I've checked to see if my ethernet was running Full Duplex at 100Mbps, I've changed the buffer sizes.

I'm just wondering if anyone who is transferring samba to samba has had 100Mbps or 1000Mbps speeds because I sure aint.

With Samba, I'm sitting in the same boat and I haven't so far been able to figure out why.

My server: P-III 500Mhz, 512MByte RAM, Ubuntu 6.06 LTS. Intel NIC with e100 module, 100Mbit full duplex with flow control. According to **hdparm -t /dev/hdc**,  we have close to 30MByte/s from the disk.

As socket options, I have this line:

```
socket options = TCP_NODELAY
```

I haven't yet set the SO_RCVBUF and SO_SNDBUF values, since I want to adhere to Ubuntu's "just works" philosophy, and because in earlier days when the server still ran Debian stable and the clients were Gentoo and Windows,  changing these options had no effects at all.

Other testing shows:
[LIST]
[*] iperf reaches 95Mbps in both directions.
[*] iperf even does 180Mbps over a (round-robin) bonded pair of these Intel NICs when connected to a gigabit switch and sending to a gigabit client. So it's not a bus system, NIC or ethernet issue.
[*] NFS is also around the 10-11MByte/sec mark. 
[*] single SMB downloads won't go beyond [COLOR="Red"]6-7MByte/s[/COLOR]
[/LIST]

However:
[LIST]
[*]multiple parallel SMB downloads will go near [COLOR="Blue"]11MByte/sec[/COLOR]
[/LIST]

This makes me think of "latency". At work, whe have two 50mbps LAN links from Zurich to London, one with ~25ms round trip time, the other with ~16ms. With a single TCP stream, and standard window sizes, you just can't get more than ~8 on the slower link and ~12Mbps on the fast one. Multiple parallel TCP connections however can easily saturate the links.

To verify and cross-check, I have set up a Compaq ProLiant 1850R (don't forget the earplugs!) with Compaq SmartArray 3200 Controller and 4x36G Disks and two P-III 600MHz processors yesterday. As soon as I'll have figured out why I can't yet properly log in with Samba, I'll redo the speed testing with that box. No "lame hardware" excuses anymore. This thing just will have to fly! I'll keep posting the results.


best regards

Marc

---

### Post by netztier on 2007-03-09
> **Mr. C. said:**
> socket options = TCP_NODELAY [COLOR="Red"]IPTOS_LOWDELAY [/COLOR]SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192


I've been looking up in books and googled around about "IP TOS low delay", and what I have found makes me reluctant to set the IPTOS options for samba. Assuming that these options actually set/flip the "Delay" and "Throughput" bits in the IP header, playing with these could have unwanted adverse - or even opposite - effects in some network environments.

I'll have to do some checks to verify which bits in the IP header are actually set with samba's IPTOS options. 


Here's my considerations:

See [http://www.rhyshaden.com/ipdgram.htm](http://www.rhyshaden.com/ipdgram.htm) (at the end of the page).

If the delay and throughput bits are set, the IP packet requests "low delay" or "high throughput". [COLOR="Green"]**On a "flat", routerless LAN, they have no effect at all**[/COLOR]. If there are routers and WAN lines between server and client, the routers may interprete these bits and adjust the queuing/processing of the SMB packets accordingly.

Now "classical" IP ToS based mechanisms have not been seen too often in"real world networks".  The IP ToS field (8 bits) has however been redefined to be read as the "DSCP field" (6bit +2 unused). The delay and througput bits from the old 8bit ToS field make up bits 4 and 5 of the redefined 6bit DSCP field. in In modern QoS-enabled networks, these are interpreted and influence packet processing, queuing and forwarding.

See [http://www.rhyshaden.com/qos.htm](http://www.rhyshaden.com/qos.htm), especially the diagram and table at 1/3 of the page that show how the "old" ToS bits are mapped to the "new" 6bit DSCP field.

Setting bits 4 and 5 of thde DSCP field will *increase* the drop probability for a given traffic class (!). So packets with these bits risk getting lower-quality service when being processed by a router that has a DSCP-interpreting QoS policy.

Hm. I think I'll have to play around with ethereal in these next days a bit. I want to know about this.


best regards

Marc

---

### Post by btboudreaux on 2007-03-09
> **Mr. C. said:**
> I just copied a 14.5meg file Windows->Samba in about 2 seconds.  Are you troubles bi-directional, or uni-directional ?

You will not get 12.5MBps, as there is overhead in the connection.  You might approx 10, but you can expect much higher speed than 3-3.5.

Don't start tweaking Ethernet and network settings you don't understand.  The Linux kernel has very fast Ethernet and is tuned quite well.

Some global Samba options recommended are:

socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

This should be sufficient.  You clearly have a 100mbit connection, because you won't get 3-3.5Mbit on a 10Mbit network, so that's not the trouble.

Give me an update,
MrC

Before I made this post, I had set the RCVBUF and SNDBUF to 8192, then to 32768 on both machines with no results. I don't know what the problem is and no one seems to have a 100% workable solution.

---

### Post by Mr. C. on 2007-03-09
netztier,

It is really good to see actual benchmarking results vs. so much hogwash posted in various threads.   These tools are very good at helping find issues.

It is important that folks understand that these tools must be used correctly, and understood that they can only be used to diagnose and optimize a given network path.  Since the net is a very dynamic beast, there will be no single configuration or setting the will produce optimal results in all cases.  Too many believe if they just tweak this parameter, they will get double the performance for free.  It simply isn't that simple.

btboudreaux - start learning how to diagnose these problems by learning the underlying protocols and fundamentals of various network layers, and their affect on networking performance.

MrC

---

### Post by dannyboy79 on 2007-03-09
> **btboudreaux said:**
> Because I would like to know your secret!

I have two Ubuntu workstations, both running Samba. The Desktop has gigabit ethernet connected to a gigabit switch. The laptop is 100Mbps.  I should have at least (or close to) a 100 Mbps (12.5MBps) transfer rate but I get 3-3.5MBps. It's extremely slow when transferring large files. When both workstations were Windows based, the transfers went with blinding speed. 

I've read all the post and tried different things but nothing is speeding up samba. I've mounted with nautilus, with smbfs, I've checked to see if my ethernet was running Full Duplex at 100Mbps, I've changed the buffer sizes.

I'm just wondering if anyone who is transferring samba to samba has had 100Mbps or 1000Mbps speeds because I sure aint.

have you tried to mount them using cifs instead of smbfs? I have read that smbfs is out the door and cifs will be taking it's place. don't know if that will have any effect. are you using the best cat5 cable or some junky one to your 100Mbps laptop? Are you using solid cat5e or cat6 for your gigabit connections? that will slow your performance even more. here is a link to a .pdf which contains many linux tweaks of the overall system to improve stuff rangning from i/o to the filesystem: [ftp://ftp.kalamazoolinux.org/pub/pdf/PerfTune2001.pdf](ftp://ftp.kalamazoolinux.org/pub/pdf/PerfTune2001.pdf)

---

### Post by btboudreaux on 2007-03-09
> **Mr. C. said:**
> netztier,


btboudreaux - start learning how to diagnose these problems by learning the underlying protocols and fundamentals of various network layers, and their affect on networking performance.

MrC

This a home PC and home laptop connected to a switch which had great transfer speeds when Windows was running on both. Since my switch to Ubuntu, the speeds arent even close. I see tons of post on the board about slow samba speeds. There needs to be a solution. I'm not a Samba developer/coder and I don't know/understand every configuration command and I don't think everyone should be expected to. The fact that this issue exist on lots of machines is unacceptable. This should work out of the box. There needs to be an update/patch/or some configuration to fix this. Telling everyone to "start learning" really doesn't help anyone. If people can post what worked for them, I think that helps alot more.

---

### Post by btboudreaux on 2007-03-09
> **dannyboy79 said:**
> have you tried to mount them using cifs instead of smbfs? I have read that smbfs is out the door and cifs will be taking it's place. don't know if that will have any effect. are you using the best cat5 cable or some junky one to your 100Mbps laptop? Are you using solid cat5e or cat6 for your gigabit connections? that will slow your performance even more. here is a link to a .pdf which contains many linux tweaks of the overall system to improve stuff rangning from i/o to the filesystem: [ftp://ftp.kalamazoolinux.org/pub/pdf/PerfTune2001.pdf](ftp://ftp.kalamazoolinux.org/pub/pdf/PerfTune2001.pdf)

Trying cifs is my next course of action although I'm doubtful. I won't be able to try it till tomorrow evening. Thanks for the input.

---

### Post by Mr. C. on 2007-03-09
> **btboudreaux said:**
> This a home PC and home laptop connected to a switch which had great transfer speeds when Windows was running on both. Since my switch to Ubuntu, the speeds arent even close. I see tons of post on the board about slow samba speeds. There needs to be a solution. I'm not a Samba developer/coder and I don't know/understand every configuration command and I don't think everyone should be expected to. The fact that this issue exist on lots of machines is unacceptable. This should work out of the box. There needs to be an update/patch/or some configuration to fix this. Telling everyone to "start learning" really doesn't help anyone. If people can post what worked for them, I think that helps alot more.

We understand that you experience issues in your setup.  Windows and *Nix are so different that it is impossible to give a single answer or debug tip as to why you experience issues.

That the test is fast in Windows only gives you one upper limit of what a system can do with your hardware.  It does not help find where the problem is though.  This will require analysis.

One cannot conclude that the system in general is broken from your apparent observation that a problem exists "on lots of machines".   There is *no* such piece of computer software ever written that works "out of the box" for all of the varieties and combinations of hardware in existence today.   There will be problems, and diagnosis is difficult for everyone.

The infinite variety of "what works for me" only polutes threads with hearsay and belief in magic or voodoo.

You may not understand how the systems work, but you can work with those people who are trying to help you resolve the issue.  That's what we're trying to do.

MrC

---

### Post by muso on 2007-03-10
I'm also getting slow samba speeds.  I've tried the suggested "socket options" which made no noticeable difference for me.  I know what you mean, MrC, about "what works for me" but frankly it's precisely that approach that's got me on Feisty with a working webcam and video-conferencing.

Anyway, hopefully by posting my experience of it I might help to paint a more complete picture: I have a ATMT network drive which supports Samba and FTP access, and it's on my 10/100 network.

I copy a 400MB file:
Copying to Windows it takes around 1 minute
FTPing to Ubuntu takes a little over 1 minute (1;15)
SMBing to Ubuntu takes a little over 5 minutes.

There is clearly something wrong in the settings of Samba in Ubuntu, but I haven't been able to track it down.

Someone might ask: why don't I just use FTP?  Okay, I guess I could do that for transferring files... however, I use this drive mainly for sharing movie files, and it streams nicely enough to play easily in Windows across the network.  In Ubuntu I can't play (don't know how to) stream the files to a player with FTP, and with Samba, because it's sooo slow, it only gets into so far into the movie file before it starts stuttering and losing sound.

Let me know if there are more specific details that I can provide that might help diagnose this problem.

Also know that I'm a complete n00b with Ubuntu (I've only had it installed for a couple of months).  Oh, I'm running Feisty, from a fresh install of Edgy, and haven't changed much yet.  I also had the same problem on Dapper, which I previously had installed.

---

### Post by Mr. C. on 2007-03-10
I just ran another trial.

I used a 715Mb file, transfered in both directions, and found almost essential identical upload and download speeds: 1:59 (windows->linux) and 2:01 (linux->windows).  Let's call it 2:00 even.

A 5.95Mb/sec, that's fairly respectable.  Although some are clearly experiencing some performance issue, it is too much of a generalization to say there something wrong with Ubunta Samba performance as a whole. 

Each situation must be analyzed to find the problem.  This has to start with eliminating as many variables as possible, and isolating minimal test cases that allow reproducing the problems.

What other desktop apps are being run ?
Is upload / download speed the same ?
Is the copy the foreground task ?
Are there any Ethernet errors ?
Is IPv6 enabled/disabled ?
Are source/destination file system's the same in the FTP v. Samba transfers?

MrC

---

### Post by btboudreaux on 2007-03-10
I mounted with cifs instead smbfs. My transfer rate went from 3-3.5 to 5. A little improvement but still dog slow. 

I agree with Muso, there is something wrong with the settings of Samba in Ubuntu.

---

### Post by Mr. C. on 2007-03-10
What percentage of the CPU is smbd using when you do the copy?

How does memory and paging look while you are doing it?

Watch "top -d 1" during the time the copy is in progress.

MrC

---

### Post by btboudreaux on 2007-03-10
From Windows to Samba I get a 9.5 - 10 MBps transfer speed. Maybe its just a samba to samba problem?

---

### Post by Mr. C. on 2007-03-10
Now, ya see!  This is why I object so much to gross generalizations like "something's wrong with Samba in Ubuntu".  :-)

Watch top -d 1 as you do your samba-samba copy.  Compare the things I indicated in my previous post.

MrC

---

### Post by btboudreaux on 2007-03-10
> **Mr. C. said:**
> Now, ya see!  This is why I object so much to gross generalizations like "something's wrong with Samba in Ubuntu".  :-)

Watch top -d 1 as you do your samba-samba copy.  Compare the things I indicated in my previous post.

MrC

Yeah... I see your point. 

Alright, Im getting 7-7.5 from samba to samba now since switching to cifs. My cpu on both machines is around 5-10 percent. Swap file and memory look fine. I have 2 gigs in one and 1 gig in the other. Maybe its just the samba overhead slowing it down? I do see improvements since switching to cifs, but I would like it to go at least 10MBps. I'll keep trying different things/suggestions until I can get those few extra MBps out of it.

Thanks for your help, and if anyone else has experimented, let us know the results.

---

### Post by Mr. C. on 2007-03-10
The previous poster "muso" achieved 6.66Mbps via FTP.  I achieve 9.6Mbps sustained via FTP, and almost 6Mbps via Samba.  It seems unlikely you are going to achieve 10Mbps.  Your 7 to 7.5 is very realistic.

Samba, like NFS, has its own overhead, and it is not insignificant.

MrC

---

### Post by btboudreaux on 2007-03-10
Yeah, I agree.

Mounting with nautilus and smbfs is what I guess was slowing me down.

cifs is the way to go.

---

### Post by netztier on 2007-03-12
> **btboudreaux said:**
> Yeah, I agree.

Mounting with nautilus and smbfs is what I guess was slowing me down.

cifs is the way to go.

That's what I was advised, to: "Do a CIFS hard-mount in /etc/fstab". In **smb.conf**'s man page, I found a reference to *disable netbios*(using tcp/139) altogether - can't remember the exact syntax right now.  But I'll disable it on the server anyway. Like this, I can force all clients to use tcp/445 (aka CIFS) only.

Those of you having experienced increased performance with switching to CIFS, here's suggestions on what to test next:

[LIST]
[*]what happens if you copy the same file in two parallel (same direction) connections between the server and one client?
[*]what happens if you copy two different files in parallel (same direction) between the server and one client?
[*]what happens if you copy the same file in parallel (same direction) between server and two different clients?
[*]what happens if you copy two different files in parallel (same direction) between the server and two different clients?
[/LIST]

Please report your results (where reproducible by your network landscape). I wonder if you can reproduce what I have observed: one TCP connection can't saturate a 100Mbps FDX pipe, but multiple connections can. Which then again would show that Samba is actually up to it's main task: be a file server for multiple clients.


best regards

Marc

---

### Post by muso on 2007-03-12
Damn, I forgot that I have to ask for email notifications for subscribed threads (I didn't get any yesterday, and I was messing on with Ubuntu).

Yeah, I'd be as happy as an idiot in idiotland on idiots get in free day to get 6Mbps, or even close... also, don't get me wrong, I think Samba is fantastic, and it clearly works for most people most of the time.  I just need to find out what to tweek!

> What other desktop apps are being run ?
Is upload / download speed the same ?
Is the copy the foreground task ?
Are there any Ethernet errors ?
Is IPv6 enabled/disabled ?
Are source/destination file system's the same in the FTP v. Samba transfers?

**What other desktop apps are being run ?**

Possibly Skype or Ekiga, but I'm sure that doesn't make a significant difference - although there is some other factor that I'm not aware of because I tried again yesterday, and it said that it was going to take 40 minutes to copy that 400MB file onto my Desktop!  Other than that, all I had running was Yakuake.  I don't have any desktop enhancements active either.

**Is upload / download speed the same ?**

Good question.  It seemed like they were, but I'll have to confirm that tonight.

**Is the copy the foreground task ?**

Yes.

**Are there any Ethernet errors ?**

Not sure how to test that.

**Is IPv6 enabled/disabled ?**

I'm on default settings. (that means I don't have the foggiest!)

**Are source/destination file system's the same in the FTP v. Samba transfers?**

Because, in my case, it's a network HDD, I can only compare against a Window's system.  I said a little under 1 minute to copy 400MB in Windows (oh, this Windows system is actually the same computer, in dual-boot - so the hardware is identical), which was a little underestimated.  It's actually closer to 2 minutes.

It looks like CIFS is another option for me to try now (assuming that I can mount it, or access files from a movie player with it); I had looked at it before, but there was a page I found somewhere that mentioned a serious sercurity flaw in it so I discounted it then (I can't find the page again, which is really annoying me now).

---

### Post by netztier on 2007-03-12
> **muso said:**
> **Are there any Ethernet errors ?**

Not sure how to test that.


There's quite a good way to verify that your underlying connectivity runs well: Do a raw TCP throughput test. If the underlying ethernet or wireless is bad shape or mood, you'll notice instantly. 

You can use **iperf** from the universe repositories and for Windows and other OSs from [http://dast.nlanr.net/Projects/Iperf/#download](http://dast.nlanr.net/Projects/Iperf/#download) . It's command-line based, but really easy to use. You must install it on both nodes.

Then, on the "server" node, you start it with

```
iperf -s
```

and on the client, you do this:

```
iperf -c <server's ip address> -t 60  -t 5
```

This will cause the client to *send* to the server (note the directions!!) for 60 seconds (**-t 60**) and to report the results with an interval of 5 seconds (**-i 5**).

If you add the **-d** switch, you'll get a simultaneous bidirectional transfer, with **-r**, there's one direction first, then the other one.

Transfer rates to expect:

[LIST]
[*] 54Mbps WLAN: ~20-25Mbps
[*] 100Mbps Full Duplex Ethernet: ~95Mbps
[*] Gigabit Ethernet: ~600Mbps for a single transfer, +900Mbps for multiple parallel transfers (**-P** command line switch).
[/LIST]

On the other hand, you can always check the outputs of **ethtool** and **mii-tool** / **mii-diag**.


best regards

Marc




best regards

Marc

---

### Post by dannyboy79 on 2007-03-12
> **netztier said:**
> That's what I was advised, to: "Do a CIFS hard-mount in /etc/fstab". In **smb.conf**'s man page, I found a reference to *disable netbios*(using tcp/139) altogether - can't remember the exact syntax right now.  But I'll disable it on the server anyway. Like this, I can force all clients to use tcp/445 (aka CIFS) only.

Those of you having experienced increased performance with switching to CIFS, here's suggestions on what to test next:

[LIST]
[*]what happens if you copy the same file in two parallel (same direction) connections between the server and one client?
[*]what happens if you copy two different files in parallel (same direction) between the server and one client?
[*]what happens if you copy the same file in parallel (same direction) between server and two different clients?
[*]what happens if you copy two different files in parallel (same direction) between the server and two different clients?
[/LIST]

Please report your results (where reproducible by your network landscape). I wonder if you can reproduce what I have observed: one TCP connection can't saturate a 100Mbps FDX pipe, but multiple connections can. Which then again would show that Samba is actually up to it's main task: be a file server for multiple clients.


best regards

Marc

If I disable netbios, then wouldn't my name resolution stop working? I like being able to use the computer name instead of ip addresses in my fstab and when I ssh into it so on and so forth. if you could clarify this I would appreciate it. thank you. i have never actually timed my tranfers but  I have ntoiced that they seem to take way to long but what is weird is that I can stream movies and music from my ubuntu server (running dapper) to my xbox media center and it plays great!!! it just seems like it takes forever when I transfer files from my windows xp pro box to or from my ubuntu server using nautilus windows drag and drop or even doing it from windows explorer drag and drop. what is the best way to measure the amount of time instead of actually timing it with a stop watch as I don;t want to haev to sit there and wait to see when it finishes? some cases I am transferring a 600mb file and others I am trasnferring a 4.5gb file. any help would be much appreciated.

---

### Post by Mr. C. on 2007-03-12
> **muso said:**
> 
**Is IPv6 enabled/disabled ?**

I'm on default settings. (that means I don't have the foggiest!)


Disable IPv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

MrC

---

### Post by dannyboy79 on 2007-03-12
i have heard of disabling ipv6 before but only for faster web surfing. i did some research to see if this has any relation to samba, nfs, or ssh. it turns ou that a user did see a dramtic increase in his network traffic when he disabled ipv6 within his mac so hopefully it will be the same increase for linux. This is what he says:

"I had slow access times on my network copying files via scp, samba, and nfs. And my ssh logins seemed slow as well. However, my only XP laptop it didn't seem like an issue. I found a post somewhere's while searching for what I thought was an OS X Samba problem and it suggested disabling IPv6 on all interfaces. Hmmm, I thought. I sorta felt OS X having this turned on outta the box was kinda a neat thing. However, when I did turn v6 off, ALL my network traffic sped up dramatically.

I haven't really dove into this, but it would be interesting to find out why this is and because others mentioned the same thing, I know it's not my home network. For those of you experiencing slow network speeds, I recommend giving this a try"

---

### Post by Mr. C. on 2007-03-12
All hardware in the path must be IPv6 compliant.  If it is not, there will be problems.  Ubuntu made the choice to enable IPv6 by default; this is unnoticeable by most, but some experience problems.

MrC

---

### Post by muso on 2007-03-12
> **Mr. C. said:**
> All hardware in the path must be IPv6 compliant.  If it is not, there will be problems.  Ubuntu made the choice to enable IPv6 by default; this is unnoticeable by most, but some experience problems.

MrC

Thanks.  I tried disabling it, but no noticeable difference (it was taking around 4:40 to copy the 400MB file this time).  All my hardware is less than a few years old, so I guess it has IPv6 support, but if it improves internet browsing to remove it, I ain't gonna complain.  I assume there aren't any benefits from having IPv6 enabled on the short term, are there?

I'm going to try setting up CIFS now anyway, and see if that makes a difference... (I'll report back).

---

### Post by Mr. C. on 2007-03-12
> **muso said:**
> I assume there aren't any benefits from having IPv6 enabled on the short term, are there?

The benefits are only towards stabilizing the support of IPv6 in the distributions.  There's a chicken / egg problem here.  IPv6 cut over cannot occur until the majority of all devices support it reliably, and that requires real-world testing.  But we cannot get real-world testing until the support is enabled by default.  These sorts of transitions occur fairly rarely, but are always painful for some.

MrC

---

### Post by netztier on 2007-03-12
> **netztier said:**
> 
Please report your results (where reproducible by your network landscape). I wonder if you can reproduce what I have observed: one TCP connection can't saturate a 100Mbps FDX pipe, but multiple connections can. Which then again would show that Samba is actually up to it's main task: be a file server for multiple clients.


Now let's fill in some data here:

The server is Ubuntu 6.06 LTS Server on a Compaq ProLiant 1850R with **2x P-III 600Mhz,** 768MBytes RAM and a Compaq SmartArray 3200 Controller, with 1x 36Gig Wide Ultra-SCSI and a **4x36Gig RAID5** array. It's  NIC is a Compaq Netelligent Integrated 10/100 TX UTP, with the **tlan** module. AND THE BOX IS SO LOUD that now I have a NAGGING RINGING in the ears AFTER SITTING NEXT TO IT FOR THREE HOURS! *brrrr*

The RAID array has been clocked at **40.5MBytes/sec** by **hdparm -t /dev/ida/c1d0**, and it hosts the directory with the ~660MByte sized files.

All mounts are done via **/etc/fstab** or **mount -t cifs //<ip>/share -o username=<user>,password=<pw>,iocharset=utf8**, not via GNOME.


First client is  Ubuntu 6.06 LTS on an **AMD Atthlon 64 ** Venice 3000+ (1.8Ghz, 1GB RAM) with a Marvell Yukon Gigabit Chip (skge module) at 100Mbps FDX. 

Second client is Ubuntu 6.10 on a HP Compaq nc6000 Laptop with a  **Pentium M 1.6GHz**, 1GB RAM and a Broadcom Gigabit Chip (tg3 module) at 100Mbps FDX, 

The Ethernet switch is a Linksys SD-205 5 port 100Mbps switch. All systems have been iperf'd at >92Mbps from any to any system, both with generated data and one of the test file used as input.


[COLOR="Navy"]smb.conf has socket options = TCP_NODELAY

**Uploads:**

[LIST]
[*] Ubuntu 6.06 client uploads one file to the server. System Monitor says **3.5MiBytes/sec**
[*] Ubuntu 6.10 Client uploads one file to the server. System Monitor says **7.9MiBytes/sec**
[*] each client uploads one file  to the server. System Monitor says **2.1MiBytes/sec** on Ubuntu 6.06 and **6.4MiBytes/sec** on Ubuntu 6.10
[*] each client uploads two files to the server. System Monitor says **3.1MiBytes/sec** on Ubuntu 6.06 and **6.2MiBytes/sec** on Ubuntu 6.10
[/LIST]

Downloads:

[LIST]
[*] Ubuntu 6.06 client downloads one file from the server. System Monitor says **3.5MiBytes/sec**
[*] Ubuntu 6.10 Client downloads one file from the server. System Monitor says **5.5MiBytes/sec**
[*] each client downloads one file  from the server. System Monitor says **4.7MiBytes/sec** on Ubuntu 6.06  and **3.8MiBytes/sec** on Ubuntu 6.10
[*] each client downloads two files from the server. System Monitor says **5.6MiBytes/sec** on Ubuntu 6.06  and **4.8MiBytes/sec** on Ubuntu 6.10
[/LIST][/COLOR]

[COLOR="DarkRed"]Now the whole procedure again, this time with TCP_NODELAY SO_SNDBUF=8129 and SO_RCVBUF=8192 in smb.conf.

**Uploads:**
[LIST]
[*] Ubuntu 6.06 client uploads one file to the server. System Monitor says **3.8MiBytes/sec**
[*] Ubuntu 6.10 Client uploads one file to the server. System Monitor says **8.2MiBytes/sec** and sometimes 10.2MiBytes/sec
[*] each client uploads one file  to the server. System Monitor says **2.5MiBytes/sec** on Ubuntu 6.06 and **6.8MiBytes/sec** on Ubuntu 6.10
[*] each client uploads two files to the server. System Monitor says **3.0MiBytes/sec** on Ubuntu 6.06 and **7.5MiBytes/sec** on Ubuntu 6.10
[/LIST]


**Downloads:**

[LIST]
[*] Ubuntu 6.06 client downloads one file from the server. System Monitor says **6.2MiBytes/sec**
[*] Ubuntu 6.10 Client downloads one file from the server. System Monitor says **6.2MiBytes/sec**
[*] each client downloads one file  from the server. System Monitor says **4.8MiBytes/sec** on Ubuntu 6.06  and **4.5MiBytes/sec** on Ubuntu 6.10
[*] each client downloads two files from the server. System Monitor says **5.1MiBytes/sec** on Ubuntu 6.06  and **5.1MiBytes/sec** on Ubuntu 6.10
[/LIST][/COLOR]

If I had a managed switch, i'd rely solely on port counters instead of GNOME System Monitor. I know I could try **iptraf**, but when network load increases, iptraf eats up to 30% CPU load on the server. I can't be having with that during the tests, no way! So I'll have to stick to what GNOME system monitor is telling us.

I am not quite sure what to conclude from all of this. Some things shine through, although not reported here:

[LIST]
[*] where a single transfer can't max-out the link, multiple connections can
[*] SO_SNDBUF and SO_RCVBUF make some difference
[*] CIFS (tcp/445) outperforms SMB (tcp/139)
[*] hard-mounts outperform gnome-vfs-mounts
[*] nfs ist faster still :-)
[/LIST]


best regards

Marc

---

### Post by netztier on 2007-03-13
> **dannyboy79 said:**
> If I disable netbios, then wouldn't my name resolution stop working? I like being able to use the computer name instead of ip addresses in my fstab and when I ssh into it so on and so forth. if you could clarify this I would appreciate it. thank you. 


Not necessarily. NetBIOS was using broadcasts on udp/137 and udp/138 on the local subnet to find neighboring NetBIOS servers. This was an adaption from it's ancestor, the NetBEUI protocol which was not routable at all. Still, on medium and large scale networks, these broadcasts needed help from the routers to cross router boundaries and reach the servers, which is why NetBIOS-over-IP was often sneered at by network admins. WINS - basically MS's "DNS for NetBIOS" helped quite a bit in keeping the broadcast flooding at bay.

If however your IP stack has other means to resolve names to IP addresses (such as DNS lookups, a hosts file or an lmhosts file), there's no need for broadcasting. Microsoft's ActiveDirectory added one more way to find servers and ressources: special DNS entries and LDAP queries. Actually, you can run an entire AD without (well, almost) any NetBIOS, just by using CIFS, LDAP and Kerberos. We've spent quite a bit of time with our AD guys trying to rot NetBIOS our of our network, but it wouldn't quite work till the end. MS's Clusters are such a thing that still need NetBIOS and WINS, or DOS-based setup routines that need to access some software distribution server.


> **dannyboy79 said:**
> i have never actually timed my tranfers but  I have ntoiced that they seem to take way to long but what is weird is that I can stream movies and music from my ubuntu server (running dapper) to my xbox media center and it plays great!!!

That just goes to show that "streaming" is different from "transferring": when you "stream" content, you deliver it as fast as the receiving application needs/requests it. Web radio with 128kbit/s only needs a mere 128kbit/s, videos may need a few Mbit/s, not more, even 1st generation HDTV is happy with ~15-20Mbit/s. 

On the other hand, wehn copying files or ftp'ing files the applications will just try to take all the bandwith they can get, and possibly will max-out the link. And that's when things start to appear slow with Samba not going further than say... 35Mbit/s on a 100Mbit/s full duplex ethernet.

> **dannyboy79 said:**
> what is the best way to measure the amount of time instead of actually timing it with a stop watch as I don;t want to haev to sit there and wait to see when it finishes? some cases I am transferring a 600mb file and others I am trasnferring a 4.5gb file. any help would be much appreciated.

Use Gnome System Monitor (you can add it to your panel and open it from there). In the "Ressources" tab, it shows you the input/output curves of the primary network interface. I've found it to be quite accurate.

Be careful with Files over 2Gig in size - these will never fit into the cache of your systems, and you might be measuring a mix of disk/I-O & cache subsystem/bus performance instead of samba's. I have made the same mistake and I'll have to repeat the test with smaller files (transferred multiple times sequentially) so they'll be served out of the cache, so at least I have the disks out of this.


best regards

Marc



PS: a paragraph oa blank line here & there in the text of your answer might have made it easier to find the hidden question in it!

---

### Post by dannyboy79 on 2007-03-13
> **netztier said:**
>  Not necessarily. NetBIOS was using broadcasts on udp/137 and udp/138 on the local subnet to find neighboring NetBIOS servers.  
SO how would I go about turning off netbios over tcp/ip so that I don't have these broadcasts using my bandwidth? I have all my hostnames and ip's already within my /etc/hosts file on all my ubuntu machines and I even added all ip and hostnames in my lmhosts file within windows. on the windows side would I just uncheck the netbios over tcp/ip box? how about on the (x)ubuntu side? would I then close 137 & 138 udp ports with iptables? just so you are aware, my dapper ubuntu box is my local master browser when all my machines/xbox's are on, then when that gets turned off, xubuntu dapper turns into it. I do it this way because sometimes winxp pro isn't on and I noticed that when I didn't have ubuntu or xubuntu as the local master browser, and winxp was off, samba wouldn't work, i can't say there is a direct connection with the issue but I can only atest to what did and does work.

[QUOTE=netztier;2290670]
Be careful with Files over 2Gig in size - these will never fit into the cache of your systems, and you might be measuring a mix of disk/I-O & cache subsystem/bus performance instead of samba's. I have made the same mistake and I'll have to repeat the test with smaller files (transferred multiple times sequentially) so they'll be served out of the cache, so at least I have the disks out of this.
QUOTE]
so how do you suggets transferring such large files? can I make my cache larger? disk space isn't an issue, I have over 1.2tb of storage between my xp box and my ubuntu server.

thanks in advance for your help and your suggestion of using paragraphs between answers and questions is a good idea.

---

### Post by netztier on 2007-03-13
> **dannyboy79 said:**
> SO how would I go about turning off netbios over tcp/ip so that I don't have these broadcasts using my bandwidth?

In smb.conf's man page, I found a section about the option **disable netbios = yes**. I added it to the global configuration section of my samba server, but I saw that a listener on tcp/139 was still open. So I assume it's still active. I was so busy doing file transfer tests yesterday, I didn't bother investigating further. That's for another night. Spring is here :) and I feel it through every bone :)

About broadcasts consuming bandwith: don't worry about it on a small LAN with a handful of machines. The NetBIOS broadcasts on udp/137 and udp/138 are not sent by dozens-per-second. It was only in larger networks where things got out of control. 

The nagging thing about Win9x for example was that it would broadcast it's presence simultaneously on NetBIOS-over-IP, NetBEUI and IPX/SPX, thus tripling the broadcast load. Imagine the chattiness of say... 50 to 60 Win9x machines on the same subnet. Awful! And half the time someone would switch off the station that had been master browser, so every now and then, a master browser election had to take place... yes. with broadcasts. for all three transport protocols! 

With bringing everyting to IP and using some WINS servers, things got a lot better: The NetBIOS broadcasting could be brought under control, and the network admins didn't have to forward that many NetBIOS broadcasts across router boundaries anymore. 

> **dannyboy79 said:**
> 
 I have all my hostnames and ip's already within my /etc/hosts file on all my ubuntu machines and I even added all ip and hostnames in my lmhosts file within windows. on the windows side would I just uncheck the netbios over tcp/ip box?

Exactly. AFAICR, it's somewhere in the "Advanced properties" of the TCP/IP configuration, I believe on the "WINS" tab. If you do this, accessing the Ubuntu Servers directly with \\<server-name>\<share> will definitely still be possible, since name resolution is given - make sure to add the names to the hosts file on Windows, too (%windir%\system32\drivers\etc\hosts, I believe). I am not sure if you'll be able to browse the network neighborhood the same way as before. Be sure to check!

If network browsing won't work anymore, you could re-enable NetBIOS on the  samba server an configure it to be a WINS server.  Then make sure that clients recevice a DHCP option telling them what their WINS servers are (Option "Netbios Name Servers"). While you're at reconfiguring your DHCP server, you may even consider configuring the NetBIOS node type to something else than "H-Node" (I believe that it's "P-Node", I have to look it up first), so that they always will look up in WINS and DNS and never broadcast. On XP and Win2K, you'd then have to tell it to use the "NetBIOS setting from the DHCP-Server" instead of "disable NetBIOS".

This of course is going a long way just to eliminate a few broadcasts, but it might make a great exercise in networking for the curious. :-)

> **dannyboy79 said:**
> 
how about on the (x)ubuntu side? would I then close 137 & 138 udp ports with iptables? just so you are aware, my dapper ubuntu box is my local master browser when all my machines/xbox's are on, then when that gets turned off, xubuntu dapper turns into it. I do it this way because sometimes winxp pro isn't on and I noticed that when I didn't have ubuntu or xubuntu as the local master browser, and winxp was off, samba wouldn't work, i can't say there is a direct connection with the issue but I can only atest to what did and does work.


Master Browser: you should be able to force your samba server to be a master browser,  there's a config option for that. It's already given in the sample config file, you'll just have to uncomment it to make it active. It's **domain master = auto**. Consider a "yes" here, but check the smb.conf man page before to see what implications this has. I think that "auto" is recommended.

The other parameter is **disable netbios = yes**, and I would expect that udp/137 & 138 and tcp/139 should not be open anymore on the server afterwards. So there's basically no need to firewall them - you could, of course. As described above, I have configured this option, but at first glance, it didn't seem to have the desired effect. More investigation to follow...

> **dannyboy79 said:**
> 
so how do you suggets transferring such large files? can I make my cache larger? disk space isn't an issue, I have over 1.2tb of storage between my xp box and my ubuntu server.


Hm, I fear I wasn't quite clear there. I didn't mean that you should not transfer such large files, but that you should arefully consider the implications when using such a chunk of data for performance testing. It might turn out that you're not measuring samba performance, but your system's disk I/O qualities or how good caching and swapping works on your system, and this might have unwanted influence on the results.

best regards

Marc

---

### Post by dannyboy79 on 2007-03-13
i don't use dhcp for 1, all my computer's and xbox's use static ip's so i am not sure about the settings you talked about involving the dhcp server and the p-node or whatever. also, i explained that my ubuntu IS my local master browser so I didn't need you to explain how to do this but I thank you as I am sure others may want to know this. I should explain however that there are several options that I have enabled and not ONLY domain master and everything with samba is working great.  also, just so you are aware, the default for domain master is set at auto due to the fact that when domain logons is changed from no (the default) to yes, then domain master would "auto" become yes otherwise without domain logons the "auto" is basically a no and that's why the default is auto but you can set it to yes if don't want domain logons and you're not on a domain. that's what it states in the man page.

main ubuntu samba server

os level = 40
local master = yes
domain master = yes
preferred master = yes

ensure that my ubuntu dapper machine is the local master browser so i can have winxp off and samba still works. i already stated that I am not sure if this is the specific reason why samba still works, it just does and it doesn't work if I don;thave this stuff in there and have winxp pro off.

and my xubuntu settings are:

os level = 33
local master = yes
domain master = auto (in effect this is no because domain logons default is no)
preferred master = auto

i guess my question is, if I disable netbios, I currently don't have wins server defined, I have my gateway defined as my router and only have hosts files in linux and lmhosts in windows xp pro, than how does this work? i suppose I'll give it a try and see what happens. i thought netbios uses the hosts file? i have tried playing with the name resolve order = lmhosts host wins bcast (this is the default) option in my smb.conf and had the host first but it never seemed to work so I believe it is using bcast currently or maybe host cause I know I don't have a lmhosts file on my samba server and I know I don't have wins defined so it's obviously either host or bcast.

---

### Post by muso on 2007-03-14
Hmmm... I don't want to bring this thread off-track, but I said I'd report back my findings after trying CIFS.

This didn't work:
mount -t cifs //hostname/share /mnt/temp -o username=someuser,password=somepassword

But this did:
mount -t smbfs //hostname/share /mnt/temp -o username=someuser,password=somepassword

However, using SMBFS it was going to take 3-4 hours copying a 600MB file (I gave up while testing it).

I also tried LUFS (to mount the drive using FTP) - which seemed to have bits missing, and didn't work.

---

### Post by dannyboy79 on 2007-03-14
> **muso said:**
> Hmmm... I don't want to bring this thread off-track, but I said I'd report back my findings after trying CIFS.

This didn't work:
mount -t cifs //hostname/share /mnt/temp -o username=someuser,password=somepassword

But this did:
mount -t smbfs //hostname/share /mnt/temp -o username=someuser,password=somepassword

However, using SMBFS it was going to take 3-4 hours copying a 600MB file (I gave up while testing it).

I also tried LUFS (to mount the drive using FTP) - which seemed to have bits missing, and didn't work.
well here is the guide, if you follow it step for step it will work! [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534))
also, do you have the user you are trying already added to your ubuntu computer and your smb password database? i think this is required for authentification otherwise the link does show how to use a guest option and still be able to write to the share. good luck

---

### Post by btboudreaux on 2007-03-14
I did some more testing.

After using cifs I started getting about an average of 7MBps transfer speeds going samba to samba machine. That was just doing one transfer at a time. I tried doing 2 transfers at a time and I got around 10MBps and sometimes it jumped to even more. 

So if you really want to make best of your bandwidth using samba and cifs, transfering two sets of files at once might do the trick.

---

### Post by bogolisk on 2007-03-15
with my linksys 10/100 router and wired connections:

   - 11.3 MB/s for NFS (edgy to edgy)

   - 10.MB/s for smb (windows pulls 8GB from samba on edgy)

---

### Post by dannyboy79 on 2007-03-15
so the question becomes, how do we limit the amount of bandwidth a file tranfer uses. If we are getting better speeds when we transfer 2 files than I would suspect that this is because the protocol isn't trying to use as much as it can for 1 file which ends up saturating the transfer and causing it to actually be slower, but instead using a realisitic amount of the bandwidth per file which then leaves overhead for the process or whatnot.

also, to netzier. i would like to know what the difference is between samba in 6.10 versus samba in 6.06. when you did your test, it was actually faster uploading when you used 6.10 on the client BUT slower when downloading. WHY???? 

**Uploads:**
6.06 client one file. 3.8MiBytes/sec
**6.10 Client one file.  8.2MiBytes/sec and sometimes 10.2MiBytes/sec**
simaltanious one file. 2.5MiBytes/sec on 6.06 and **6.8MiBytes/sec on 6.10**
simaltanious two files. 3.0MiBytes/sec on 6.06 and **7.5MiBytes/sec on 6.10**
*Are you viewing the system monitor on the server or on the client?????*
**Downloads:**
6.06 downloads one file. 6.2MiBytes/sec
6.10 downloads one file. 6.2MiBytes/sec
simaltanious downloads one file. 4.8MiBytes/sec on 6.06 and 4.5MiBytes/sec on 6.10
simaltanious downloads two files. 5.1MiBytes/sec on Ubuntu 6.06 and 5.1MiBytes/sec on 6.10
*Are you viewing the system monitor on the server or on the client?????*

this is very interesting. i am going to try the same thing once I get my system back. i am currently in the middle of changing motherboards and cpu's. 
from: foxconn something or other and P4 Celeron 2.66ghz 
to: ASRock 775dual-VSTA and an Intel E4300
i am probably just going to stick with dapper though and maybe compile whatever version of samba is in Edgy if it's different than what's in dapper.

---

### Post by Mr. C. on 2007-03-15
There are many variables at play here, and these benchmarks as very simplistic.  One cannot read too much into these numbers until the effects of caching, CPU vs. disk IO vs. network IO, file size, buffer size, synchronous vs. asynchronous completes, etc. are all taken into consideration and understood.

The previous poster indicated 10Mbs for two files- was that total or average?  Did each file actually transfer at 5Mbps ?   Either way, it is typical for the systems to seemingly perform better when the workload is increased.  This is due to a single process waiting on IO to complete, whereas two or more process allow a fuller saturation of system resources.  While one is waiting for an IO to complete, the other(s) may be performing CPU-intensive calculations.  Put more simply, in a test that is primarily IO-bound, the process will spend a fair amount of time sleeping and waiting.

MrC

---

### Post by dannyboy79 on 2007-03-15
i can't speak for them, but if you look at the gnome system monitor, i believe it just shows what the bandwidth usage is. so if it says 10MB of data being transferred per second plain and simple, it could be 3MBps for 1 file and 7MBps for the other file, i just believe it's the total. i can't say for sure though since I don't have my ubuntu working right now. I am however curious as to why that guys Raid array only is allowing 40.5MBytes/sec. When I run the same hdparm test against a ATA100, ATA133 or Sata 1.5gb I get 59MBytes/sec. I always thought Raid arrays were faster? Is this not true or is it simply dependent on the controller and drives is hooked to?

---

### Post by Mr. C. on 2007-03-15
RAID 5 is always slower than other RAID configurations, especially for writes.  It has to calculate checksums.

MrC

---

### Post by netztier on 2007-03-15
> **dannyboy79 said:**
> i can't speak for them, but if you look at the gnome system monitor, i believe it just shows what the bandwidth usage is. so if it says 10MB of data being transferred per second plain and simple, it could be 3MBps for 1 file and 7MBps for the other file, i just believe it's the total. 

That's what it does. And I had the Edgy Laptop and the Dapper Desktop right next to each other, so i could watch gnome system monitor on both of them. I know that this may be inaccurate as a method. But I'm not wondering if it's 7.1 or 7.2 MiBytes/sec, but if it's 4, 7 or 10MiBytes/sec. And for that purpose, I deem Gnome System Monitor "good enough".

> **dannyboy79 said:**
> I am however curious as to why that guys Raid array only is allowing 40.5MBytes/sec. When I run the same hdparm test against a ATA100, ATA133 or Sata 1.5gb I get 59MBytes/sec. I always thought Raid arrays were faster? Is this not true or is it simply dependent on the controller and drives is hooked to?

With all four drives hooked up on the same UltraWide SCSI Bus, I think 40MBytes/sec is about as fast as it will get. After all, this is last century hardware. :-) 

best regards

Marc

---

### Post by dannyboy79 on 2007-03-16
you didn't comment though, what version of Samba is in Edgy versus what version is in Dapper? Also, what other things does the Edgy kernel have compiled in that Dapper's kernel may not? I know MrC is gonna come back and say, "there is so many things to take in account.............."  but I am only curious about these 2 things for now. If you could answer this since you have both running that would be great. Thank you.

---

### Post by hairy on 2007-03-27
I appreciate that there's a lot of unanswered questions in this post, but I have found a (possible) solution to some people's wireless samba/nfs problem.

I have no idea why this affects ubuntu (i've not had a problem with windows or slackware) but with ubuntu if you do not specify a low receive buffer size, then you get slow transfers!

Something that worked for me.......

sudo mount -t smbfs //server/video /mnt/video -o rsize=1024

This enables each chunk to be placed into a ethernet frame without fragmenting it. I've seen some other stuff relating to mac's that suggests turning off delayed acks (couldn't find a similar option in ubuntu) I wonder whether the ubuntu client or something ubuntu related is collecting fragments before sending acks, which leads to samba throttling the connection.

if anybody who knows better than me can dis/prove that i'd be grateful =)

---

### Post by hairy on 2007-03-27
to make the last post make a bit more sense.... all the clients operate through a wireless connection, server being wired to the wreless router (a belkin soho jobbie)

windows xp client copying large file from slackware server = quick
slackware client copying large file from slackware server, mounted as smbfs = quick

ubuntu client copying large file from slackware server, mounted as smbfs = slow

to the point where watching a video in totem thats on a samba share on the server is of unacceptable quality (jerky, bleh as it buffers). copying a 200mb file takes about 30mins

I've got all the suggested options on the samba server, nothing special was needed doing to the windows or slacware clients to help along. I've disabled ipv6 in ubuntu (not on the slackware server though, I'm going to try that and see what happens) 

in ubuntu I have to specify a low receive buffer when mounting the share before I can get fast transfers, or videos to play properly.

I don't have any numbers to hand, but if you want them np =)

---

