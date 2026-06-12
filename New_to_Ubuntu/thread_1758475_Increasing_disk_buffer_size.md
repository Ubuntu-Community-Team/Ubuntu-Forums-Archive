---
title: "Increasing disk buffer size"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by msimon1960 on 2011-05-14
Coming back to Ubuntu after a bit of hiatus after Jaunty...

My disk to disk transfer speed is slow (15Mbps) and I recall that the send/receive buffers were set small by default.

I can't recall how to increase the buffer sizes -- the last time I tested this I found that 16k buffers worked best (1k was the default at the time).

Any help would be appreciated!

---

### Post by ClientAlive on 2011-05-14
What release of Ubuntu are you running?

---

### Post by msimon1960 on 2011-05-14
Fresh copy of Natty...

---

### Post by ClientAlive on 2011-05-14
> **msimon1960 said:**
> Fresh copy of Natty...

You poor poor soul.

Hang on. Let me do some looking around and see what I can find. I've personally never messed with what you are talking about but if I can find any info that may help I'll post it here. the information you gave will help others also.

Back in a bit.

Jake

:D

---

### Post by ClientAlive on 2011-05-14
> **msimon1960 said:**
> Coming back to Ubuntu after a bit of hiatus after Jaunty...

My disk to disk transfer speed is slow (15Mbps) and I recall that the send/receive buffers were set small by default.

I can't recall how to increase the buffer sizes -- the last time I tested this I found that 16k buffers worked best (1k was the default at the time).

Any help would be appreciated!

Can you be a little more descriptive about what it is you are trying to do? Does this involve TCP? When you say "disk to disk" do you mean transfering data between two internal disks on the same computer? Between an internal disk and an external (like a usb drive)? Over a network?

Thanks

---

### Post by msimon1960 on 2011-05-14
Thanks...

I may be recalling a samba config option (it's been a loooong time since Jaunty) but any suggestions on improving local disk transfer rates would be appreciated.

Matthew.

---

### Post by ClientAlive on 2011-05-14
Is this of any use?

[http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)

[dated 2008]

[http://www.crn.com/news/applications-os/18818299/linux-power-tuning.htm;jsessionid=BcHLqtbdaH6KZR+Fz3nnTA**.ecappj03](http://www.crn.com/news/applications-os/18818299/linux-power-tuning.htm;jsessionid=BcHLqtbdaH6KZR+Fz3nnTA**.ecappj03)

[dated 2000]

---

### Post by msimon1960 on 2011-05-14
Between two local disks -- sata connection to the motherboard and two identical 2TB Western Digital drives.  Both drives are installed on the one computer -- nothing to do with networking at all in this situation.  The only difference is one is NTFS and the other is Ext3.

I just would have expected the copy transfer rate between the drives to be higher -- when I run it in Win7 I get 90Mbps.

Matthew.

---

### Post by ClientAlive on 2011-05-14
> **msimon1960 said:**
> Between two local disks -- sata connection to the motherboard and two identical 2TB Western Digital drives.  Both drives are installed on the one computer -- nothing to do with networking at all in this situation.  The only difference is one is NTFS and the other is Ext3.

I just would have expected the copy transfer rate between the drives to be higher -- when I run it in Win7 I get 90Mbps.

Matthew.


Is it some kind of RAID configuration?

Brother. I want to let you know, I don't know anything about this particular thing before coming across your post. What I am doing is looking at information about it on the internet just like anyone could do. Just that we are the only two people talking on this thread right now anyhow and I figured two minds are better than one, right? So I'm new to Linux (about 6 wks in) and been studying my ars off. I've learned a lot and I would love to learn more. Sooo . . . whatever time you have to mess with it today I can learn something; and, maybe in the process, we come across what you are looking for. Just stating what is on my mind and what I'm doing here on the thread. Maybe someone else comes along and just knows exactly whats up. Then we both win (learning wise). Sound cool?

:)

---

### Post by ClientAlive on 2011-05-14
There's this:

[http://linux.die.net/man/8/hdparm](http://linux.die.net/man/8/hdparm)

I noticed that the section " -m" seems like what you are talking about. It's about 1/4 or 1/3 of the way down the page. It talks about buffer size all through that page though. Perhaps, in general, we are on the right track?

---

### Post by msimon1960 on 2011-05-14
No raid involved.  I'm just transferring a big (900Gb) library of files from my NAS (which used EXT3) to a new drive on an Asus mediaplayer which uses NTFS.

I pulled the NAS drive and connected it to my motherboard along with the new drive that will go into the ASUS unit. Trying to transfer the data between the drives using the network would have taken days.  I thought this would be much faster.

On a hunch I plugged one of the drives into another SATA port and I'm getting 35MBps now.  Much better!  I don't know why this worked?  I thought every SATA connection was independent (not master/slave like PATA)?

I'd still be interested in linux configurations to tune disk drive performance.  With such a large media library every bit helps.

Matthew.

---

### Post by msimon1960 on 2011-05-14
Finally found it!...

My memory failed me -- the buffers had to do with Samba (networking).

SO_SNDBUF and SO_RCVBUF are configuration options for tuning samba -- they are set low by default -- I found that 16k buffers worked best for my unit at the time.

I checked out the -m switch but it operates on IDE drives -- I don't know if it works only on PATA IDE drives or on SATA as well.  I may experiment with it on an old drive at a later date.

Thanks for climbing the learning curve with me -- if you find anything on tuning SATA drive performance I'd be interested.

Matthew.

---

### Post by 5149.5 on 2011-05-14
This[ link]("http://goo.gl/Pl0Tz") has some tuning information.

---

### Post by ClientAlive on 2011-05-14
That's great man! Glad to hear it. Well, you have a nice weekend. Back to my studies for me.

:D

---

