---
title: "Gparted meets hard drive from hell"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by pottzie on 2010-04-24
A friend said he wanted to try Ubuntu so I ran the live cd on his older Compaq/HP (?) computer. When the partitioning section ran, it only offered to install ONLY Ubuntu. He has WinXP, but the partitioning software never gave the option of installing Ubuntu and XP. 
 I'd never seen that, as I've installed Ubuntu along side Windows several times.
 I thought that maybe it was because there was a problem with the live cd, so I tried it using a Gpareted live cd. Same thing, the hard drive showed an NTFS partition as the entire hard drive, with no fat-32 partition. Gparted didn't seem to be able to carve it up or add partitions or alter the size of the existing partition. 
 He's just changed the new hard drive, and this was a fresh install of XP, with nothing added. He doesn't even want the service packs! The hard drive looked to Gparted like it was made of cement and covered with super glue. He's got an 80 gig HD, with XP taking up 8 gigs. The rest is vacant, and we'd sure like to "put it to good use."
 Any ideas what's preventing the partitioner from working?

---

### Post by ed-koala on 2010-04-24
Boot the LiveCD, go into Synaptic and install a package called ntfsprogs.  See if that helps.  That package is designed to alter ntfs partitions.

---

### Post by pottzie on 2010-04-24
Alright I'll try that. How hard is it to use Synaptic before Ubuntu gets installed to the hard drive?

---

### Post by ed-koala on 2010-04-24
Not hard at all.  It makes no permanent changes to your system.

You may have to find the ntfs tools in the applications menu, I've never used it so I'm not sure.  Here's the link I found that had me suggest this:

[http://www.linuxquestions.org/questions/linux-software-2/gparted-ntfs-resizing-has-anyone-had-any-problems-with-it-459829/]("http://www.linuxquestions.org/questions/linux-software-2/gparted-ntfs-resizing-has-anyone-had-any-problems-with-it-459829/")

---

### Post by pottzie on 2010-04-24
Y'know...it never occurred to me until I read your link. In the rush to install Ubuntu, my friend just shut down Windows by hitting the "kill switch" on the front of the computer.
 No wonder Gparted wouldn't work! Gparted won't touch a Windows partition that wasn't shut down from the menu. 
 It may need a "Start" button to come to a halt, but it sure makes a difference!
 Bet that's what the problem is.

---

