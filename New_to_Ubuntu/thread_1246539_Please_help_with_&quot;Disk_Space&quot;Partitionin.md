---
title: "Please help with &quot;Disk Space&quot;/Partitioning options in Ubuntu installation"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by hanzj on 2009-08-21
Hello,
Step 4 in Ubuntu 9.04 installation gives 4 options:

1. Install them side by side
2. Use entire disk
3. Specify partitions manually 
4. something something (advanced)

Let's say I'm going to have only ubuntu on my hard drive. It seems then that "use entire disk" is the common-sense option. But would there be any advantage in choosing option 3 or 4.


Pls help soon. Thanks.

---

### Post by mike555 on 2009-08-21
If your only going to install Ubuntu you could just pick the default "use entire disc" , some will say to make a separate /home , but you don't need to, in fact I don't recommend it ... better to back up your data to a external HD ..........

---

### Post by hanzj on 2009-08-21
thanks. I chose option 2.

---

### Post by KinKiac on 2009-08-21
Personally I like the "specify partitions manually" option.  It gives you much more control over your file system.  I dont have any external storage except my 16gig thumb drive.  I have over 150gigs of music and movies on my drives though.  If I have only one partition, and it got corrupted or wouldnt boot, got a virus etc etc whatever, I would lose everything unless I could hook the HDD up to another PC for data retrieval.  

Up until recently I was a windows user exclusively.  Problem with that is, I hate MS, lol.  When I had windows installed I had 2 drives.  1 80gig IDE with my windows on it.  OS and programs only.  Then I had a 300 gig SATA drive.  I took that drive and partitioned it into 3 100gig partitions.  This is where all my music, documents, movies etc would be saved.  I changed the default save directory for all my programs to go to the other partitions.  So, when windows crapped out on me, which is inevitable, about every 6 months or so I would just re-format my entire C: drive and do a clean install on windows.  I did the same thing when adding new hardware(wireless card, video card etc).  

Basically it just allows me to have all my files, music etc, on the equivalent of a different drive, without having to have a different drive.  If my OS gets messed up I reformat and reinstall, all without having to lose my personal files.  

Now that I have Ubuntu I have kept the same setup.  I moved all my files on to one of the 2 100gig partitions in windows before I installed Ubuntu.  Then I used the manual specify option when installing Ubuntu and deleted the blank 100gig partition.  I formatted a couple gigs for swap space, formatted 80 gig for storage of files, and used 20gig for my Ubuntu installation.  

Being a noob with Linux, and my undying urge to meddle and reconfigure, there is a good chance I may mess up my OS beyond repair, or at least beyond easy repair for me, a noob.  That being said it is much safer, and quicker than spending hours researching how to fix, for me to set my system up the way I have as no matter what happens, no matter how badly I mess up my OS, I can simply reformat, reinstall and all is good again, with no lost files.

I know I could just as easily make a system backup for my ubuntu, but what if I wanted to drop Ubuntu altogether?  Maybe try Arch? Or Mint?  Again, doing it like this allows me to simply reformat the partition that I use for my OS and lose none of my media files.  
Backing up those files is a whole other ballgame.   

Anyway, thats my 2 cents.

---

