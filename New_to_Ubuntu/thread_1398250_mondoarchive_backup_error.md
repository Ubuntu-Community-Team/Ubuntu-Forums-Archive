---
title: "mondoarchive backup error"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by mistypotato on 2010-02-04
Can't seem to get Mondo Archive to work.

findfs|blkid|vol_id is installed yet mindi seems to think it's not.
Anyone found a resolution to this or should I just move on to another backup program?

**Here is the error message.......**

FATAL ERROR. Your system uses a UUID partition ,
but you lack the tool to support it.
Please replace labels with their correct devices in /etc/fstab or
install findfs|blkid|vol_id or
relabel the partition with the correct UUID if it's a swap partition.
Please e-mail a copy of /var/log/mindi.log to the mailing list.
See [http://www.mondorescue.org](http://www.mondorescue.org) for more information.
WE CANNOT HELP unless you enclose that file.

---

### Post by mistypotato on 2010-02-04
After searching for an answer for this for some time, I can only gather that at this time, Mondo does not seem to be a viable backup solution.

There was a time I was able to successfully use MondoArchive but no longer.
When it worked, it was to me, the best solution...allthough I have never been able to get it to do DVD backups.

If you have installed mondoarchive on a ubuntu 8.10 Intrepid system and it is working, please advise.

Otherwise, while Mondo is a great concept and used to work, you may find time better spent looking at alternatives as time is money.  Commercial applications is where I believe I'm headed as I want a backup system that will create Bootable backup disks of my entire drive, not just a partition or two or utilizing a complex process.  And the $50-$70 I spend once may prove to be a good investment.



Final errors from Mindi/Mondo.

Mindi --makemountlist /tmp/mondo.tmp.KZlGzC/mountlist.txt.test failed for some r
Please run that command by hand and examine /var/log/mindi.log
for more information. Perhaps your /etc/fstab file is insane.
Perhaps Mindi's MakeMountlist() subroutine has a bug. We'll see.
Failed.
Fatal error... Pre-param initialization phase failed. Please review the error messages above, make the specified changes, then try again. Exiting...
---FATALERROR--- Pre-param initialization phase failed. Please review the error messages above, make the specified changes, then try again. Exiting...

---

### Post by jamesr on 2010-02-06
Hi 

I do not use 8.10 system but 8.04 LTS systems. I find that it works well to an external USB hard drive. It does not seem to work to CDRWs on my systems, so I load to the USB HD in iso's of the correct size to burn to CDRW at my leisure. The problem seems related to the burning of CDRW's and seems to be related to Xubuntu some how. One of my systems worked until the system was updated by the update manager. Other systems (SCSI based) have never worked reliably and that includes xfburn, brasero and gnomebaker. The latter is more reliable but the compare routines fail, eventhough the burn software says OK. Even just recovering the files using afio fails whereas the I can always recover data from the USB HD using afio.

You mention > And the $50-$70 I spend once may prove to be a good investment. I do not see where the cost comes from as mondoarchive is free.

Also where did you get the mondo and mindi from, the Ubuntu repositries or from the Mondorescue.org site. I ask because the ones in the Ubuntu repositries are out of date and the naming structures is such that the update manager tries to update to the Ubuntu versions. The FAQs have a fix for this problem.

The errors in your first posting are related to the swap file UUID, again answers are available on the Mondorescue site.

I had to fix the same problem on a couple of systems whereas others are OK. It seems to be related to the Debian (Ubuntu) base install. If you cannot find the answers, I should be able to post here once I find the information.

What did you change to get the 2nd set of errors.

---

### Post by mistypotato on 2010-02-07
Hi,

Thx for the reply.

Since that post, I found that another computer I have at home with the same version of Ubuntu 8.10 and has a nearly identical fstab file works fine with MondoArchive, so even though Mindi logs indicate it's a problem with the UUID, it works like a charm on the other computer and the fstab file is, like I said, extremely close to being the same.

**The swap file line is 100% exactly identical on both machines (other than the UUID of course)**.

One difference is that the computer Mondo is working flawlessly on is the SERVER edition of 8.10 whereas the one it will not work on is a workstation (regular 8.10 version install).

I find it extremely odd that this is occurring. (SwapFile error, but identical on both machines)

In the past, I have had success with MondoArchive and when it works, it is simply fantastic at what it does.

The cost I was referring to was if I went ahead and purchased a commercial product.

Concerning the difference in the Fatal Error Message....
That was because of where I copied it from.  I think I copied the first one from the MONDO log and the second from the actual MINDI log

BTW...the "working" MondoArchive installation was installed clean directly from the Ubuntu repositories.  I could not get that or the one direct from Mondo.org to work on the workstation.

M

---

### Post by mistypotato on 2010-02-08
Update to the Update..... (for anyone later with similar concerns)

On the NON-working mondo machine, I was able to get mondo to work by Changing the swap file line so that the swap file is identified by it's old style (/dev/sda1) label.

SO, it seems Mondo is now working for me again and I couldn't be happier.

---

### Post by jamesr on 2010-02-13
Sorry I was slow in replying but that was one of the options and the other, was to do a manual uuid and reset the swap file. I tried both and both worked but I have stayed with the changed UUID route because I did it last and it also worked. My biggest problem with Mondo has been the CD burning and that is not directly a Mondo problem but is more apparent in Mondo because I always do a verify. Also my server uses Xubuntu not Ubuntu so my test bed not quite equivalent.
 
If you wish to download the latest from the Mondorescue.org site you can install with the debi installer on Ubuntu and equally on my server 
sudo apt-get install xxxxx.deb 
in a terminal window.
On the wiki on the mondorescue.org site FAQ11 should updated shortly because the old FAQ11 no longer seems to work. This is related to the problem of updates from the Unbuntu overriding the latest mondo updates.

---

