---
title: "Linux-formatted drive attached to Asus RT-N56U"
date: 2014-11-30
forum: Networking &amp; Wireless
---

### Post by paul_reid2 on 2014-11-30
I have a 3TB Seagate drive attached to my home router and I had Samba shares on there (and UPnP sharing) and a weird thing happened.  The folders are all still there but now there are no files in any folder.  This happened both when attached to the router and also when I attached it to my server running a Ubuntu Live CD.

1. Has anyone seen this before?  Are the files recoverable?  (My backups are about 3 months behind.  Yeah, yeah I know.)  If so, what's the best (safest) tool to find those files and recover them?

2. What's the best way to share a drive between multiple computers 24/7 given the following requirements?
a. 30W power consumption or less.
b. Must present Windows shares to the network.
c. Prefer NTFS formatting for easier backups (the Asus claimed to work with NTFS, but it hated it) and file recovery (at least I know what tools to use to recover Windows drives).
d. 24/7 operation
e. UPnP shares for media files on there (the majority of what is there are pictures and videos we have taken).

While the Asus did a-e, I never loved this solution.  
It was clunky.  
UPnP failed for no reason occasionally.
Backing up was somewhere between massive chore and impossible since if you moved a large amount of data across the router quickly, it would crash.  
Having the drive be Linux format meant that it was very difficult to backup to a Windows computer easily.

I don't mind spending $100-$200 to get a really good solution to this, so any advice would be greatly appreciated.

Thanks for any help you can give me.

Paul

---

### Post by newbie-user on 2014-12-01
I wouldn't trust those home routers with any sort of service that you need 24/7. Build a small server based on an Atom processor, that way you can meet your 30W requirement. Install ubuntu with a samba server so that windows clients can easily access the shares.

---

### Post by paul_reid2 on 2014-12-01
That's a really good idea!  I actually have an Asus eeePC 900HA sitting around with the hard drive replaced by an SSD that I really never use anymore.  I could just put in on my Windows domain and make shares and then all my users (aka family members) could just automatically have the correct rights.  I can just hang the 3TB drive off a USB port and I could even run TVersity or something for UPnP support.  I can spin down the 3TB drive whenever it's not in use to save power.

I read that it only uses about 10-15 watts doing something like this, so for future use, this is probably the best bet.

So, now I guess I only need to know what is a good tool to rescue files from an ext3 partition.

---

### Post by paul_reid2 on 2014-12-01
Actually, I just saw that my favorite tool (Recuva) just added ext2/3 support for Windows WITHOUT a driver installed.  I guess I'll try that first.

---

