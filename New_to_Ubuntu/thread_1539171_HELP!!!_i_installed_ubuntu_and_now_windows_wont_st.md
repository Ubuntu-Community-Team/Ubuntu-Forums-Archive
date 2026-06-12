---
title: "HELP!!! i installed ubuntu and now windows wont start without it."
date: 2010-07-26
forum: New to Ubuntu
---

### Post by Vuk Matic on 2010-07-26
OK so here the story, i was having problems with this other computer so i decided to install ubuntu to an External HDD and see if that would help the other computer. What i didnt realise is that i cannot start windows without the external HDD (with ubuntu) anymore and this is terrible since HDDs are very risky (especially this one)! This is all on my main computer (the one that works). I dont know what to do now but it is REALLY annoying to have to plug in my HDD everytime i want to start Vista (64 bit)! Please help me quickly! you can email me at [EMAIL="vukmatic@msn.com"]vukmatic@msn.com[/EMAIL] !!!

---

### Post by anewguy on 2010-07-26
What happened is that the MBR (master boot record) on the hard drive was overwritten by the information needed to load the Ubuntu boot loader - grub.  Where your hard disk used to say "boot windows directly from me" it now says "load grub from the Ubuntu drive and let the person select the OS".  This is very common with people installing Ubuntu to an external drive.

The following will get you back to where you can boot Windows without the external drive, however it won't give you an option to boot Ubuntu:

Boot Windows

goto [www.downloads.com](www.downloads.com)

search for and download the tiny free program MBRFIX

after download, check the syntax in the html file that comes with the program - if you only have one drive built-in, it should be:

mbrfix /drive 0 fixmbr /yes

After you've done that just reboot and it should just boot Windows.

Now you'll need to set up so you can boot Ubuntu from the external drive but not interfere with any other OS - e.g., make the drive containing Ubuntu portable to boot on any computer without changing that computer.  I personally haven't done this, but I would venture a guess that you want to install to the drive and in the installation - I think the partitioning screen? - will be an "advanced" option where you tell it which disk to install the grub loader to.  Since I haven't done this, I would suggest that after you get Windows booting again you do the following:

- open a new post, explain that you want to install Ubuntu to an external drive so you can move the drive around and boot it on various computers but not change anything on any of the computers.  Someone should be able to help you from there.

Dave

---

### Post by Vuk Matic on 2010-07-26
> **anewguy said:**
> What happened is that the MBR (master boot record) on the hard drive was overwritten by the information needed to load the Ubuntu boot loader - grub.  Where your hard disk used to say "boot windows directly from me" it now says "load grub from the Ubuntu drive and let the person select the OS".  This is very common with people installing Ubuntu to an external drive.

The following will get you back to where you can boot Windows without the external drive, however it won't give you an option to boot Ubuntu:

Boot Windows

goto [www.downloads.com]("http://www.downloads.com")

search for and download the tiny free program MBRFIX

after download, check the syntax in the html file that comes with the program - if you only have one drive built-in, it should be:

mbrfix /drive 0 fixmbr /yes

After you've done that just reboot and it should just boot Windows.

Now you'll need to set up so you can boot Ubuntu from the external drive but not interfere with any other OS - e.g., make the drive containing Ubuntu portable to boot on any computer without changing that computer.  I personally haven't done this, but I would venture a guess that you want to install to the drive and in the installation - I think the partitioning screen? - will be an "advanced" option where you tell it which disk to install the grub loader to.  Since I haven't done this, I would suggest that after you get Windows booting again you do the following:

- open a new post, explain that you want to install Ubuntu to an external drive so you can move the drive around and boot it on various computers but not change anything on any of the computers.  Someone should be able to help you from there.

Dave


Dave you have no idea how happy you have just made me! i thought i screwed up my computer! hehe! But i really like ubuntu and i think i ll be making a special partition for it on my main hard drive because its really smooth and runs MUCH faster than vista even off of a hard disk! 
Thank you so much! If you ever need anything im here for you! (although i cant offer much knowledge on ubuntu hehe)

THANK YOU!

---

### Post by Vuk Matic on 2010-07-26
well i ve got some bad news :( the mbrfix didnt work for me :( its probably cause Vista has changed their MBR or something like that :( crap!

---

### Post by Zorgoth on 2010-07-26
Use mbrfix64, not plain mbrfix!

(because you have a 64-bit OS)

---

### Post by Vuk Matic on 2010-07-26
okay thanks i found it! gotta love google! tryin to see if it worked now! thanks!

---

### Post by anewguy on 2010-07-26
Sorry - didn't realize you were running 64-bit (I missed that little bit of important info and it was right there in your opening post).  At least you got it working.

Dave

---

### Post by Vuk Matic on 2010-07-27
it didnt work :( i opened the file (as an admin) and cmd just flashes and sometimes i can see a bit of writing! but it still doesnt work! I restarted my computer and i still cant boot withour my external!!

---

### Post by Mark Phelps on 2010-07-27
Instead, go to the appropriate link below, download and burn the Vista Repair CD, boot from that into a command line, and run "bootrec.exe /Fixmbr":

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by Vuk Matic on 2010-07-27
> **Mark Phelps said:**
> Instead, go to the appropriate link below, download and burn the Vista Repair CD, boot from that into a command line, and run "bootrec.exe /Fixmbr":

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)


thanks im downloading it now!

---

### Post by jtarin on 2010-07-27
While your at neosmart you should investigate and download their application for booting more than one OS. EasyBCD. It uses the Windows Loader to boot Grub.....leaves the MBR to Windows.

---

### Post by anewguy on 2010-07-27
And I should have pointed you to the newest version of mbrfix - it will work with Vista and Windows 7 in addition to the other OS's from before,  and 32 or 64 bit.  Vista and Windows 7 use a different format of MBR from XP, etc..

With that version, the command would be something to the effect of:

MbrFix /drive <num> fixmbr /vista /yes

Dave

---

### Post by Vuk Matic on 2010-07-27
> **Mark Phelps said:**
> Instead, go to the appropriate link below, download and burn the Vista Repair CD, boot from that into a command line, and run "bootrec.exe /Fixmbr":

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Thanks loads it worked great! Just wondering, if i partitioned my main hard disk (the one inside my computer) and installed ubuntu onto this would i still get the same problem?

---

### Post by Vuk Matic on 2010-07-27
Worked like a charm! thanks a bunch! Just one more noobie question: if i partition my hard disk (the one in my computer) and install ubuntu onto this, will i get the same boot options again? or is there a way in which i can actually still use the windows booter?

---

### Post by jtarin on 2010-07-28
> **Vuk Matic said:**
> Worked like a charm! thanks a bunch! Just one more noobie question: if i partition my hard disk (the one in my computer) and install ubuntu onto this, will i get the same boot options again? or is there a way in which i can actually still use the windows booter?
See my post above this one where I pointed to one of the cleanest ways to dual boot.EasyBCD

---

### Post by Vuk Matic on 2010-07-28
sorry didnt realise page 2 hehe :) but thanks! im downloading it and trying it out as we speak! thank you ALL for your help! im loving this forum!!!

---

### Post by jtarin on 2010-07-28
Any problems with EasyBCD....the onsite forum is a good place to get help.

---

