---
title: "Issues with scp download speed"
date: 2014-08-26
forum: Networking &amp; Wireless
---

### Post by cosmicsteve on 2014-08-26
Hello all-

I am having some issues with my download speed on an scp/rsync/rcp transfer I need to make from an old work computer onto a Ubuntu 14.04 home desktop I just resurrected. It is directly wired to a Cisco Linksys EA 2500  router, and I have not had any issues with the internet speed in general, until I had to run an scp routine for a very large (~ 1 TB) amount of data from my old work computer in Boston (I am now in Hunstvile AL, FYI). When I run the scp commands I am maxing out at ~ 100 k/s, which given the amount of data I need to transfer is unacceptably slow (like well over a month to transfer everything). 

This does not seem to depend on whether or not I connect the computer directly to the modem or not, and it doesn't seem to be a problem with any of my other network protocols (every speed test puts my download speed at ~ 15 M/s. I am not demanding that speed, but I am a factor of 100 lower than that at the moment and I really cannot afford to be). 

So my questions are a few in number:

1) What is it about scp that is making it so much slower than I expect?
2) How can I configure my router and modem to try and circumvent this limit?
3) Are there any other tests I can run to make sure everything is in working order?

I have loads of experience with Ubuntu in general but that does not extend to any of the networking aspects, so I am at a loss as to where I might even start to figure this out. 

Also time is a factor in getting my data transferred, so I would love to hear sooner rather than later. 

Thanks in advance!

---

### Post by weatherman2 on 2014-08-26
When you are transferring files between two computers on different local networks, connected via the slow internet, you have to consider the download speed of one side and the upload speed of the other.  Typically, upload speed is much slower than download speed unless you are on a very high speed network.  For a DSL, cable, or fiber connection, upload speed is almost always much slower, often by a factor of 10 or more.

So if you are trying to download files at home from some other computer at work, the work computer's upload connection speed is the one that is probably slowing you down.  

scp itself does use encryption (ssh) which takes more computing resources - the data is encrypted at one end and decrypted at the other end.  If you have a very slow computer at one end or the other, that could slow down the speed of transfer too.

You might try using simple ftp as a test between the same two computers, if you can (ftp is an old, encrypted protocol and not consider secure over the public internet, so you should only use it to test some files you don't care about).

If FTP is much faster than ssh/scp over the same network path, then it probably is the speed of one computer or the other doing the ssh encryption/decryption.  Look at the CPU load of the Ubuntu machine you are using, for example, as it copies.  Do you see a significant CPU load from the ssh or scp process?

---

### Post by TheFu on 2014-08-26
The upload speed of the other system is likely the main issue.  This is almost certainly a WAN connection issue 100%.  Most upload bandwidth is extremely limited - especially for DSL connections.

Please do not use FTP for any data that you don't want to share with everyone in the world.

I'd have someone there clone the data to a new HDD and fedex it.

---

### Post by cosmicsteve on 2014-08-26
Hey guys-

Thank you for the help, but I highly doubt it is a question of upload speed on the other computer: my work computer is at a research university with plenty of internet bandwidth and I know I have achieved much faster download speeds than this when I am on other networks. The limiting factor is, by some means I don't understand, bottlenecked by my home connection. The same download speeds are also achieved by rcp instead of scp, so I know it is not limited by the encryption process. I have found some other threads that talk about this router having issues ([http://ubuntuforums.org/showthread.php?t=2222484](http://ubuntuforums.org/showthread.php?t=2222484)), but no luck as to how to configure the router/ethernet to work with ubuntu.  

Hopefully I shouldn't need to use the SneakerNet protocol, but I will if need be. Also, I would like to make sure other transfers aren't limited in the future.

---

### Post by TheFu on 2014-08-26
I'd contact the network admin at the other location to see if they are throttling.
Bandwidth is not unlimited anywhere.

Home connections may be throttled too - especially if the ISP has monthly data caps.  Perhaps doing the transfers outside "prime time" would help?  Lots of netflix use every evening across the USA.

What bandwidth does each side of the connection really have?  Forget what the statement says - what is the real throughput provided? Is it stable or does it change wildly?

Also - please say you are wired - not wifi. Unless your location is far (for certain values of far) from everyone else, controlling wifi interference is next to impossible.

scp is definitely slower than rcp.  rsync will use ssh by default these days according to the manpage, so the encryption overhead will be there too.
>   For remote transfers, a modern rsync  uses  ssh for  its  communications, but it may have been configured to use a different remote shell by default, such as rsh or remsh.


Don't know anything about that router.

---

### Post by cosmicsteve on 2014-08-26
Okay, so here are some answers to your questions.

1) Of course I know bandwidth is not unlimited. But there is absolutely no reason to believe that MIT is throttling their file transfer off campus to such absurdly low levels, and given that my new work network HAS allowed me to download things from there ~ 10x faster rates suggests that they are NOT responsible for the throttle. I also checked with my ISP and they swear there aren't any data caps for me. 

2) I am supposed to have a 15 M/s connection,and I am getting those speeds in speed tests. I just tested the MIT VPN and got a 2 M/s upload speed over the VPN. scp should (presumably) be about the same. 

3) I am doing a wired connection via desktop for this big download. Although I have gotten much faster download speeds from my MIT computer using a wifi connection, so again I highly doubt that MIT is the culprit here. 

There is definitely some reason that my scp connection isn't working, and I really have no idea what it is or how to fix it. Do you have any suggestions as to how I can reconfigure my Ubuntu ethernet connection in order to diagnose what might be causing the issue? I can even quickly download from other sites through the terminal, so there is something about these remote transfers through another machine that is holding my download hostage.

---

### Post by andrew102 on 2014-08-27
As others have said it's a combination of the upload speed from the server (usually slower than download capability) and that scp is a secure protocol with far greater overheads then normal FTP or regular downloads.

Also could you please state your speeds as either MB/sec or Mb/sec (Mbps) as this makes a difference. Since you talk about WiFi connection being your regular, I'm going to assume you mean 15Mbps and 2Mbps.

2Mbps ~ 250kBps so with attenuation and contention considerations as well as encryption overheads, I would say 100kB/s is reasonable.

---

### Post by TheFu on 2014-08-27
Simplify and test.
Simplify and test.
Sometimes that means swapping hardware to determine exactly what is the slowdown.

There are a few bandwidth testing tools - don't trust the "speedtest.net" things. Use the real linux testing tools. **iperf** comes to mind.  Might be useful to test storage performance too, just to be certain something funny isn't happening there.

---

