---
title: "new server setup (need network+disk bandwidth)"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by moonlightcheese on 2008-01-25
first of all, here's what i'm trying to accomplish:

basic goals:
- ability to serve files at roughly 200MB/s over the network (basically read data real fast)
- multiple file servers: sftp, samba, etc...
- record tv: mythtv box (sdtv)

what's been done:
- installed 32bit Ubuntu on my A64 machine (DFI Lanparty nF4, 7900GS, 1GB DDR400)
- setup 900GB raid5
- serve php5 webpages

to do:
- setup IP teaming with two 1Gbps NICs
- setup mythtv with schedule direct (screw you, zap2it labs!  nobody even gave a **** who you were until mythtv used your services)
- setup ftp
- setup firefly remote to work with mythtv

**on network throughput** - here is my thinking: by IP teaming two nics i was expecting somewhere around 200MBps real throughput.  calculated thusly:
((1Gbps * 2nics) / 8bpB) * 0.8efficiency= ~200MB/s network throughput
*bpB=bits per Byte

**on disk throughput** - i was thinking a 4 disk 900GB raid5 using 4 300GB partitions on four seagate 7200.10's would net me more than enough throughput to completely saturate my network bandwidth, essentially serving faster than any one computer could possibly demand at a time.  in other words, i want to be able to stream music, movies and media to my xbox (modded v1.2, XBMC latest SVN loaded) while still transfering at blazing speeds to any machine that wants to copy massive amounts of data, and with bandwidth to spare in case i want to watch some recorded tv from the pc in my bedroom...  you get the idea.  bandwidth and storage space imperitive, also need spare processing power for tv recording and video transcoding of recorded tv.

**progress** - this is basically going to act as a media server.  i'll be streaming video to my modded xbox v1.2 running XBMC (got this working already with samba).  **what i'm trying to do is get the most bandwidth possible from this box**.  i figured raid5 would give me the maximum amount of space without sacrificing too much speed.  it's a software raid5 and it's already complete as a 600GB set of 3 disks.  i'm adding the fourth disk and rebuilding it shortly; probably today.  shouldn't be too difficult as i've done this before.

**mythtv** - i still haven't got mythtv working with schedule direct but i just bought an account and i need to find a guide to get the schedules working with mythtv.  anyone got a good guide?  maybe a couple guides?

**sftp** - whats the best server to use these days.  i tried the gftpd server (the only one that shows up as an official ubuntu package) and i thought it was crap.  i need a relatively easy to setup **sftp** server (yes, it has to be sftp, call it paranoia i guess...) that will use the existing logins on the system.  no gui necessary.  i prefer the shell and a few config files.  i don't mind compiling from source.

summary of questions (because most of you won't read this whole thing):
best sftp server to use?
mythtv setup guide with schedules direct info?
what kind of throughput to expect from 4 disk  raid5 (linux soft raid mdadm) (individually drives get roughly 55MB/s)
how to setup IP teaming in linux?
snapstream firefly IR USB remote control driver?

---

### Post by moonlightcheese on 2008-01-28
::bump::

come on... can someone at least point me in the right direction in regards to IP teaming?

---

### Post by Dougie187 on 2008-01-28
Not sure if this is what you are looking for, but i just found this.

[http://www.howtoforge.com/nic_bonding](http://www.howtoforge.com/nic_bonding)

---

### Post by moonlightcheese on 2008-01-28
that's what i'm looking for exactly.  that takes care of ip teaming.  anything else i'll ask in a separate thread.  questions seem to go unanswered when you try to consolidate all your issues into a single thread it seems...  so much for being efficient.

thanks for the response. :D

---

### Post by Dougie187 on 2008-01-28
No problem. I do what i can :)

---

