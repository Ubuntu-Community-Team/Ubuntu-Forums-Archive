---
title: "Samba perfomance"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by wootz on 2006-10-04
I am troubled by the low xfer speeds of the samba based file server I'm setting up.  Ive tried reading and writing from both winxp and another Ubuntu 6.06 box but I am only getting transfer rates ranging from 300KB/s to 2-3MB/s. I also set up proftpd on on my server and I am getting transfer rates around 10-11MB/s from it.  Why is samba so slow compared to FTP?

This is also set up on a gigabit network and both client and server have integrated Gigabit controllers and SATA 3.0Gbps HDDs so even the 10MB/s from FTP seems like it's too slow. Am I wrong about that?  What kinds of speeds should I be seeing?

I've tried the following mod to my smb.conf file:
socket options = TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192

It helped a little but not much. Is there anything else to try?

---

### Post by bd_dali on 2006-10-05
I have the same problem, Ubuntu LTS 6.06 fully updated, I get < 10 Mbit/sec over a GBit LAN, transferring files from Windows Server 2003 to Samba shares. I've done some tests and this is what it looks like:

W2k3 Explorer -> Ubuntu Samba (write) = < 10 Mbit/sec.
Ubuntu Samba (read) -> W2k3 Explorer = ~ 200 Mbit/sec.
Win2k3 FileZilla FTP -> Ubuntu glftpd (write) = ~ 350 Mbit/sec.
Ubuntu glftpd (read) -> Win2k3 FileZilla FTP = ~ 350 Mbit/sec.

As far as I can tell, Samba write performance is the bottleneck. I've set performance options (TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192 IPTOS_LOWDELAY) but without any noticeable difference.

Any ideas?

---

### Post by bd_dali on 2006-10-05
Now this is just plain weird ... I found a web page ([http://www.dd.iij4u.or.jp/~okuyamak/Documents/tuning.english.html](http://www.dd.iij4u.or.jp/~okuyamak/Documents/tuning.english.html)) with some performace tips and started tcpdump to record all traffic ... and while tcpdump is running, performance is 200 Mbit/sec! If I end tcpdump, perfomance slows down to a crawl again. This is 100% repeatable. Can anyone explain this?

---

### Post by wieman01 on 2006-10-05
Found 2 interesting links. Perhaps it's worth taking a look at those:

[http://www.oreilly.com/catalog/samba/chapter/book/appb_01.html]("http://www.oreilly.com/catalog/samba/chapter/book/appb_01.html")
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html")

---

### Post by bd_dali on 2006-10-06
Thanks for your reply, I tried tuning Samba but it didn't help my problem. There is basically no difference, until I start tcpdump ... it's like pushing the nitro button, performance jumps from < 10 Mbit/s to over 200 Mbit/s, even during a transfer.

---

### Post by wieman01 on 2006-10-06
> **bd_dali said:**
> Thanks for your reply, I tried tuning Samba but it didn't help my problem. There is basically no difference, until I start tcpdump ... it's like pushing the nitro button, performance jumps from < 10 Mbit/s to over 200 Mbit/s, even during a transfer.
Yeah... It did not help in my case either. So I have decided to drop SAMBA and use NFS instead, but I don't have Windows so I don't really need SAMBA anyway.

---

### Post by scottpreston on 2006-10-26
any updates here?

i had a post that i could get the performance to increase for xp to samba share writes, by just having VNC running in the background. as soon as i minimized VNC performance went SLOW.

Cheers,
Scott

---

### Post by wieman01 on 2006-10-26
> **scottpreston said:**
> any updates here?

i had a post that i could get the performance to increase for xp to samba share writes, by just having VNC running in the background. as soon as i minimized VNC performance went SLOW.

Cheers,
Scott
I don't think so. Could not get the transfer rates much higher than 1 MB per second. Pretty lousy but I guess I have to live with it...

---

### Post by bd_dali on 2006-10-27
No improvement for me either. Joined the Samba mailing list, where my questions were completely ignored ... that's freeware for you, as long as everything works it seems like it's as good as payware, but as soon as you hit a bump in the road you really understand why it is free. 

Tried (dist-)upgrading to Edgy Eft yesterday and performance was actually worse after that. Even FTP performance went down, has never been a problem before. :-?

<RANT MODE:ON>
I've been off and on the Linux bandwagon for several years and this is the typical response from the community when you discover a problem that isn't easily fixed:

- Your hardware is flawed. Who cares if it's working perfectly under Windows 95/98/NT/XP.
- Hey, this is freeware, but you can get paid support. Or I could use Windows XP and not need paid support, because it just works.
- Dude, don't complain about this, learn C programming and fix it yourself, you do have the source code. Or I could use Windows XP and spend those hours using my working computer.
- Linux isn't for n00bs. Never mind that I've been a full time systems administrator (both Unix and Windows) for over 10 years and know a hell of a lot more about computers than Joe Average, who should be using Linux instead of Windows according to the same people.
<RANT MODE:OFF>

I really liked Ubuntu, too bad it's not quite finished yet.

---

### Post by bd_dali on 2006-11-29
My issue has been resolved: [http://www.ubuntuforums.org/showthread.php?t=272314](http://www.ubuntuforums.org/showthread.php?t=272314)

---

### Post by Devilotx on 2007-10-16
> **bd_dali said:**
> Now this is just plain weird ... I found a web page ([http://www.dd.iij4u.or.jp/~okuyamak/Documents/tuning.english.html](http://www.dd.iij4u.or.jp/~okuyamak/Documents/tuning.english.html)) with some performace tips and started tcpdump to record all traffic ... and while tcpdump is running, performance is 200 Mbit/sec! If I end tcpdump, perfomance slows down to a crawl again. This is 100% repeatable. Can anyone explain this?

Christ almighty! this is true!

I'm running a file server, running Dapper, and I'm getting horrible...horrible upload speeds

Moving a 3 800 meg files from the server to my windows computer takes like, 5 minutes over gigabit.

Moving those same 3 files back, was set to take 90 minutes

Fire up TCP dump and the damn thing flies!
very odd...

Might have to keep that running in the background...

---

### Post by bd_dali on 2007-10-17
It is strange and I have no explanation for it. I do however know how to solve the slow Samba performance, at least if you have a RealTek based network card. See earlier post in this thread.

---

