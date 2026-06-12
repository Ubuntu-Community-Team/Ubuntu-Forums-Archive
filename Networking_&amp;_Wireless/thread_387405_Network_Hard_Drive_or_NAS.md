---
title: "Network Hard Drive or NAS"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by jlr4u on 2007-03-18
I am thinking about installing a Network Hard Drive or Network Access Server (NAS). Would it be better to install a wireless unit?  Some units are just an enclosure and you must install your own hard drive, while others come with the hard drive as part of the unit.  What about file format compatibility with both Linux and Windows systems?
   
Hopefully, we can learn from this post to find out what others have done and share some learning experiences in order to make smart decisions on the hardware.

---

### Post by handy on 2007-03-18
You may save money buying enclosure & drive separately, you will at least be able to buy exactly the size drive that you need for the job.

Your network is probably running on TCP/IP, if so, then any OS capable of using that networking protocol will be able to use it.  (Which means any OS that is internet capable, basically.)

It then comes down to the file system that you use on the drive?  If you use Fat32 it will be r/w for both windows & Linux (at least).  There is software available that allows you to use the NTFS r/w as well, I don't know how reliable this is from experience so you may have to research.  [***Automatix***]("http://www.getautomatix.com/") now will install such software for you.

Wireless still looks to be the biggest lottery hardware wise for non-windows systems.  You need to verify that a wireless component works for you before you buy it. Personally I would use wired, it is easy to set up, reliable, inexpensive & faster.  Wireless when functioning properly, surely is more convenient in many situations though.

I hope that little rave helps some... :)

---

### Post by rpommier on 2007-03-18
I had been contemplating the same thing for awhile now, I'll go through my thought process, maybe it will help.

- The good thing about a NAS enclosure is simplicity.  You plug it into your router and it just works, most have nice web interfaces too.  The downside is that is all they do and you are limited by the size of the drive you put in them, although I'm sure you can daisy-chain some together to increase storage.

- For those reasons I decided to utilized an old ECS K7S5A board I had laying around and use FreeNAS.  Again FreeNAS is excellent at what it does, and very easy to setup.  I have very limited LINUX experience, but I got it up and going in about 15 minutes.  Again nice web interface but limited in what you can do beyond sharing storage.

- I messed with Windows Home Server Beta, WHS, for awhile and same thing.  Very easy to setup and manage, plus it has some nice features if you only have WinXP, Vista machines in your home.  You can backup workstations to it, share files easily, plus you have a server to run applications from if you choose, and remote desktop is built-in.  Another nice feature is that when you add storage it just borgs it into one big pool with no need to mess with FSTAB's and mounting.

- Finally, I settled on Ubuntu and have been using it as a server for about a week and think it's great.  I like the flexibility of Ubuntu and the community help is great.  Plus as a bonus it's a good way to broaden your knowledge and learn linux.  I'm a MS Systems Administrator by trade and really like treading in the unfamiliar linux waters :)  Here's what I did to get my Ubuntu server up and going.

- Ubuntu 6.10 Desktop LiveCD (Install once you get it going)
- Loaded SAMBA for sharing folders with my Windows boxes
- PuTTY to shell into my server
- FreeNX to RDP into my server
- TorrentFlux to download torrents without tying up my other computers

The only thing that I find difficult in linux is added hard drives.  For some odd reason this discipline escapes me.  I finally go mine mounted but am still unsure about how to actually take advantage of it.  I am researching the board and finding valuable help.

- So far that's my setup and it's very stable and way more useful than any NAS enclosure or FreeNAS.  As I stated before though, FreeNAS is awesome if all you want is a NAS server.  I would go with FreeNAS instead of a NAS enclosure if storage is your goal.

Good Luck
Roderick

---

### Post by bloodniece on 2007-03-22
Hi,
We took an old Dell server (SC440) and installed FreeNAS on that.  We have two SCSI 36GB disks each formatted using UFS.  User authentication is done through Active Directory and both my Windows and Linux boxes can access the shares on the FreeNAS.  It took about 15 minutes to set it up.  It would be even faster for a home user since you probably don't care about AD.

You could probably use any old PC and just stuff it HDs.

[http://www.freenas.org/](http://www.freenas.org/)

---

### Post by l4tran on 2008-04-27
Freenas has been awesome for me because of its simplicity easy to use GUI.  However I'm trying to find a way to install Torrentflux on it as well to free up my other PCs.  Has anybody ever done this?

---

