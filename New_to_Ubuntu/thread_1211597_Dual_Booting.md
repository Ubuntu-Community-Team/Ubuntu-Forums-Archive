---
title: "Dual Booting"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by wo1fe on 2009-07-12
ok i have decided i am going to be creating a dual boot machine out of the one that i am currently running.
 
as of right now i am running vista 64 home prem
 
3.1 gthz dual core processor
 
8 gig ram
 
nvidia 9600gt
 
500gb serial ata 7200 RPM
 
there is more than enough power in this machine to be ablet o handle this. the problem that i am running into is that the fist thing i tried was to create a partition with the windows partitioner hoping that ubuntu would see that partition and be able to install to it. no such luck
 
then i delete that partition and remerged it with the windows partition remembering that jaunty had a slider bar when choosing what partition it would go on. i tried this as i would like to set 120 gb for ubuntu with the rest being for my gaming on windows. not i tried that and it started working then encountered an error where there were no root something or another on it. right now i am wondering is this still going to be possible and if so can someone tell me how i might be able to accomplish this task? vthe only reason i am keeping windows is because i tend to do alot of heavy video editing and also gaming with games such as  (crysis medium/high settings, counter strike source full settings ect ect.. please anyone who can help me it would be greatly appreciated.

---

### Post by bonzini on 2009-07-12
This is a very common configuration.  Our kids have a laptop at home on which we keep an XP partition for their iTunes and Sims.  Otherwise they all use Ubuntu.

I haven't done this in the very recent past but if memory serves, all you should need to do is put in the Ubuntu iso CD and boot from it.

The partitioner will get run during the installation process, at which point you can decide how to size things.  I believe the installer will also offer to migrate your Windows accounts over.

Once you are dual-booting, you can easily access the Windows partition from Ubuntu, which can be handy.

---

### Post by nynoah on 2009-07-12
Sometimes Vista gives problems shifting partition tables.  I ran into this when I repartitioned a friends drive.  [http://articles.techrepublic.com.com/5100-10878_11-6170510.html](http://articles.techrepublic.com.com/5100-10878_11-6170510.html)  this explains it.  You want to shrink your partition.  Ubuntu can do it too........but I have run into instances where Vista has locked partitions.  Not sure how.  But I had to use what is said in that article to accomplish a dual boot.  You will know Ubuntu is having problems because when you go to repartition it will just hang up and do nothing.  Blame VISTA...........

Also prior to doing anything at all.  Compress your vista at least 2 times to make sure the files are not all jumbled.

---

### Post by wo1fe on 2009-07-12
the answer to post #2 is.
 
i already tried this. i set the size to be used at 110000MB or 107 GB. the partitioner started working and then ran into an error, i have also tried using the windows diskmgmt.msc to make a new partition of the same size and still ran into problems when ubuntu would not see the partition already there. it only wanted to install where windows was.
 
#3 i will give it a shot and post in the morning. also any suggestions for a bootloader to use?

---

### Post by nynoah on 2009-07-12
Your numbers make no sense to me......... who are you trying to ask?

---

### Post by wo1fe on 2009-07-12
> **nynoah said:**
> Your numbers make no sense to me......... who are you trying to ask?
 
i was responding to to each post using the number of the post that the reply was to. to your i satated that i would try it again and see if it works.

---

### Post by Bucky Ball on 2009-07-12
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Excellent resource for getting it right.

---

### Post by presence1960 on 2009-07-13
the message about root is because you did not set the mountpoint to / when you chose the partition to install to. You must choose "use as" - which file system you want and mountpoint- for root choose /. You will then be able to continue with the install.

---

