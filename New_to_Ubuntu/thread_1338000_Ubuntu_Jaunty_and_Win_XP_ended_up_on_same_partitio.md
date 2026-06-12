---
title: "Ubuntu Jaunty and Win XP ended up on same partition??"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by sruckman on 2009-11-26
I am an absolute newbie to Ubuntu, and don't know much about computers in general, so bear with me!  
 
I partitioned my 10 yo son's hard drive to dual boot Ubuntu and Windows XP so he could continue to play his old Windows based games.  I then installed XP first, as I read to do, then ran the defrag program.  I could never get the GParted to download and burn correctly, so I took a chance and skipped it.  I rebooted from the Ubuntu live disk and installed.  I couldn't find an answer on any forum as to how I should go from there, so with the urgent prompting of my son I chose to install side by side.  Now it seems that both Windows and Ubuntu are both residing on 'drive G', and 'drive C' is empty.  Jaunty seems to run fine, I haven't done much in Windows yet, but it looks okay.  Can I fix this without wiping the entire thing again?  That was an ordeal in itself, and I'm not sure I can remember how to do it without spending another entire day in front of 2 PC's searching for answers!
 
Please help with very specific details, if possible!
 
Thanks,
Suzanne

---

### Post by jrrader on 2009-11-26
Gparted is in the live cd.  Go to system, administration, partition editor.  Reinstalling Ubuntu on the other partition shouldn't be too difficult.  Just use the advanced option in install, choose the partition you want, format it and set it to "/"  Then simply delete the other one from the windows partition.

Edit: also, if it works, no need to mess with it.  You could do a little reading and then change the extra partition to act as his home folder.  Separate home partition is a nice thing to have.

---

### Post by mikewhatever on 2009-11-26
Hi and welcome to the forums,

it looks like you installed Ubuntu inside Windows, which is one of the ways to do it. It's also a preferable way if you don't know much about partitions and partitioning in general. The partitioning stage is often sited as the most difficult ones in the whole of the installation process.
Anyway, there is a very easy work around for partitioning, namely, 'prepare unallocated space'. In other words, delete the partition you want Ubuntu to be installed to, then, begin installing Ubuntu, and you should see a new option at the partitioning stage, that reads 'Use the largest continuous free space'. Pick that option, and you'll be dual booting in no time. I'll post a screenshot, to, hopefully, facilitate the explanation even further.

---

### Post by louieb on 2009-11-26
Really can't tell from your post what type of install you did (WUBI or side by side).  You may be fine the way your set up.

Would like a closer detailed look. Please follow the  [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")  and put the results.txt file in your next post.

---

### Post by Bartender on 2009-11-26
Suzanne -
I can understand your reluctance to install again.  However, installing a few times is the best way to get over the confusion and disorientation.  Especially if it's a computer that you can afford to just wipe and start over!
I guarantee you, by the third time you'll be going, "Oh, yeah, I recognize this step, no big deal" vs. that first time where every click of the mouse was a nail-biter.

When you say you couldn't download gparted, do you mean the stand-alone GParted LiveCD?  I have a link under my sig that'll get you pointed in the right direction.  Download the latest stable 32-bit .iso, and make a bootable CD from that just like you did the Ubuntu CD.

That gives you a partitioner on a CD that I think is less confusing than trying to partition from inside the Ubuntu LiveCD.

Using the GParted LiveCD, wipe the HDD clean, create a primary NTFS partition for XP out of part of the drive, and Apply the changes.  Leave the rest of the drive unallocated.  Close out of the GParted Live CD, and pop in the XP disc.  INstall XP to just that NTFS partition.  Don't let it format the entire drive.

You'll now have XP on half the drive, without having to mess with defragging and shrinking.  Run XP for a day, make sure it works, get updates if you're on broadband (seems like everyone is these days - except me) and just make sure it's working right.

Then toss the Ubuntu CD in and don't choose the "side by side" install.  Probably the simplest choice would be "Guided" and tell Ubuntu to install to the unallocated space.  I haven't used "Guided" in a while so not absolutely sure about that.  I like using "Manual", not because I'm a Linux guru and manual is really geeky.  It's not.  Manual is really easy once you've done it right one time.  I just like the added control.

If you've got broadband, you might want to search YouTube for "Ubuntu install".

EDIT:  BTW, if you've wiped a drive, reinstalled Windows, and managed to install Ubuntu you have established a certain level of geek cred.  A willingness to try, and not blame Ubuntu if something goes sideways, will get you far here at the friendly, supportive Ubuntu Forums!

---

### Post by sruckman on 2009-11-27
:KS Thanks Bartender!  (wow, I haven't said that in a really long time!)  It is done, and all seems to working;  I just can't get Windows online for some reason, but I couldn't last time I installed it, either.  It is wired into my DSL via my router.  Ubuntu connects just fine.  I'm starting to dislike Windows more and more each day!  If I didn't have so much stuff on my own pc, I would take the leap myself!  
 
:P Suzanne

---

