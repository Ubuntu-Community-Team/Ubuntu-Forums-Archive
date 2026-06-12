---
title: "All Folders Are Locked.  What can I do?"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by agp27 on 2010-01-02
Im kinda new to ubuntu and need help

alright so i was downloading pictures from facebook and everything was fine until i went to download one and i got a message that said i did not have permission to write in this folder.  so i exited out of every thing and opened a folder and all of the folders inside of it had a lock on it so i went through some other folders and found out ever folder was locked. And i didnt have permission to them.

---

### Post by agp27 on 2010-01-02
So i restarted my computer and when it was booting i got the message /dev/sda1 contains a file system with errors, check forced. then it say other stuff. and then it says Buffer i/o error on device sda1, logical block. and the message just keeps popping up. and i cant get out of the boot.

---

### Post by Anuovis on 2010-01-03
There are some folders that you do not have writing permissions by default and there are others where you do. Where were you trying to save the pictures? 

Your *Home* folder is the best place to download them, you should be able to do that.

---

### Post by Anuovis on 2010-01-03
Now it does not boot even if you wait a bit?

---

### Post by microbious on 2010-01-03
can u guys tell me what the H is sda1 ?

---

### Post by perlluver on 2010-01-03
> **microbious said:**
> can u guys tell me what the H is sda1 ?

That would be your hard drive, partition 1.

---

### Post by agp27 on 2010-01-03
i was downloading them in my home/desktop and the picture before downloaded fine then i went to get another one and i got the message. i went to my home folder and all the icons had a lock on it including my desktop. i even tried creating a new folder on my desktop but i couldnt the message just appeared again..

---

### Post by agp27 on 2010-01-03
when i restart i get stuck in the black screen with all the text and thats where the other messdges appear.

---

### Post by Sef on 2010-01-03
1) How old is your computer?

2) Have you a live cd?  If so, then use it to back up all your files to another storage unit, e.g., external hard drive, cd, flash drive, etc.

---

### Post by agp27 on 2010-01-03
I got it iN 2006. and no. how much does it cost and how does it work?

---

### Post by Sef on 2010-01-03
> how much does it cost and how does it work?

A live cd costs nothing.  It is legal to download it.   

1) Is there another computer you can download it on?

2) How did you install it?

3) What version of Ubuntu do you have?

4) What are your system specs?

---

### Post by agp27 on 2010-01-03
ya i have another computer. it was actually my moms ex husbands and she gave it to me. and its a linux.

---

### Post by Methuselah on 2010-01-03
When you restarted the compuer did you just turn it off or did you restart by choosing restart on the desktop?
It is a really, really, really, did I say really, bad idea to simply turn it off.
Please keep that in mind.

Anyway, your hard drive does seem questionable.
If you installed Ubuntu your self, the LiveCD is likely the disk you used so you should have it.

Sef is suggesting that you insert it and select 'try ubuntu without change to your computer'.
Put in a USB stick or something then back up your data from the hard drive that you want to keep (mostly in your home folder).

Then maybe you can try re-installing after checkinh HDD health.
Here is some info on how to check hard drive health from a Live CD.
[http://www.techerator.com/2009/05/howto-check-your-drive-health-with-a-linux-livecd/](http://www.techerator.com/2009/05/howto-check-your-drive-health-with-a-linux-livecd/)

---

### Post by agp27 on 2010-01-03
I got it already installed.. and i dont know how to back the stuff up. i cant get out of booting after the check, buffer i/o error on device sda1 pops up with some other stuff and it pops up about 10 times. then the screen goes black and when i hit a key a a bunch mose stuff comes up like do fcsk mannually and then ht say login incorrect push control-d to reboot. but it doesnt do anything... and i turned it off then on...

---

### Post by nikhilbhardwaj on 2010-01-03
hi,
the indications are that your hard disk is failing
but it may not necessarily be the case
i've a pc that i got in 2003 and my old hard disk behaved similarly

i tried various different partition schemes and here's one that worked for me
/dev/sdb is the  disk(40 gb)
/dev/sdb1 1.5 GB SWAP
/dev/sdb2  10 GB / Partition
/dev/sdb5  remaining space /home

so in my case the initial sectors were going bad
i've assigned them to swap
my pc never uses swap
so now its working perfectly

this may not work for you exactly
you may need to tweak it depending on your own settings

best of luck

---

### Post by nikhilbhardwaj on 2010-01-03
> **agp27 said:**
> I got it already installed.. and i dont know how to back the stuff up. i cant get out of booting after the check, buffer i/o error on device sda1 pops up with some other stuff and it pops up about 10 times. then the screen goes black and when i hit a key a a bunch mose stuff comes up like do fcsk mannually and then ht say login incorrect push control-d to reboot. but it doesnt do anything... and i turned it off then on...

start your computer with the live cd
you'll probably have to reinstall your os

---

### Post by Methuselah on 2010-01-03
> **agp27 said:**
> I got it already installed.. and i dont know how to back the stuff up. i cant get out of booting after the check, buffer i/o error on device sda1 pops up with some other stuff and it pops up about 10 times. then the screen goes black and when i hit a key a a bunch mose stuff comes up like do fcsk mannually and then ht say login incorrect push control-d to reboot. but it doesnt do anything... and i turned it off then on...

Apparently the hard drive is not going to boot.
You can use the liveCD to boot instead of your hard drive.
Once in the Live environment you may be able to perform diagnostics on the hard drive as well as rescue your data.

---

### Post by agp27 on 2010-01-03
after i download it on my windows computer what do i do with it. and where can i download it?

---

### Post by Anuovis on 2010-01-03
The live CD people are speaking here about is simply your Ubuntu Install CD. That is, if you are using 9.10. Some time ago you had to use 2 CDs, one for installation, another one for booting into live session. Now they are together.
Just insert your installation CD and pick "Try Ubuntu without any changes to the system", it will load the OS from the CD. 

If you do not have this live-installation CD, you can download it from [www.ubuntu.com]("http://www.ubuntu.com") and burn it legally.

If you have any valuable data on your hard disk, you can back it up via this live session. Since your cd-rom drive will be occupied by the Ubuntu CD, you should use some external memory device that connects, for example, via USB. A simple USB memory stick should do the job if you do not have very much to save.

---

### Post by agp27 on 2010-01-03
i didnt install it so i dont have the cd. and what kind of cd do i burn it to?

---

### Post by dmaxel on 2010-01-03
> **nikhilbhardwaj said:**
> hi,
the indications are that your hard disk is failing
but it may not necessarily be the case
i've a pc that i got in 2003 and my old hard disk behaved similarly

i tried various different partition schemes and here's one that worked for me
/dev/sdb is the  disk(40 gb)
/dev/sdb1 1.5 GB SWAP
/dev/sdb2  10 GB / Partition
/dev/sdb5  remaining space /home

so in my case the initial sectors were going bad
i've assigned them to swap
my pc never uses swap
so now its working perfectly

this may not work for you exactly
you may need to tweak it depending on your own settings

best of luck
Sorry, I know this is slightly off topic, but I'm having similar problems with my server, it having I/O buffer errors. How were you able to determine which sectors were going bad?
> **agp27 said:**
> i didnt install it so i dont have the cd. and what kind of cd do i burn it to?
Any regular CD-R would work just fine. Just make sure that you download the right LiveCD and burn it using an ISO burning application.

---

### Post by Anuovis on 2010-01-03
> **dmaxel said:**
> Any regular CD-R would work just fine. Just make sure that you download the right LiveCD and burn it using an ISO burning application.

Yes, any CD-R and maybe even CD-RW will do. Better stick with the former, just in case... 

You also have to make sure you do not burn the .iso file itself in the CD like in regular copy-paste procedure. The .iso file will have all the contents you need, so you have to open it inside the burner, find something like "burn ISO image", etc. 

Back in the Windows times (not so long ago) I really liked this software:
[http://www.cdburnerxp.se/](http://www.cdburnerxp.se/)

This is how you burn .iso:
[http://cdburnerxp.se/help/Data/burn-iso](http://cdburnerxp.se/help/Data/burn-iso)

Btw, do you have anything of value inside that hard disk?

---

### Post by agp27 on 2010-01-03
ya theres probably about 200 Gb that i would like to  keep.. is there a way that i can take the hardive out and put it in my windows computer?

---

### Post by dmaxel on 2010-01-03
> **agp27 said:**
> ya theres probably about 200 Gb that i would like to  keep.. is there a way that i can take the hardive out and put it in my windows computer?Considering that Ubuntu uses ext3/ext4, and that Windows doesn't support Linux filesystems out of the box, it probably wouldn't work. There are programs/drivers out there for Windows that supposedly offer excellent read-only access to ext2/ext3 filesystems, but I've never tried any of them myself.

---

### Post by agp27 on 2010-01-03
well, would it be able to read the folders and mp3's on it...

---

### Post by dmaxel on 2010-01-03
Well, with Windows itself, no. With that certain program/driver, probably. (Like I said, I've never tried it myself)

---

### Post by agp27 on 2010-01-03
alright.

---

### Post by Anuovis on 2010-01-03
> **dmaxel said:**
>  There are programs/drivers out there for Windows that supposedly offer excellent read-only access to ext2/ext3 filesystems, but I've never tried any of them myself.

There are drivers for ext2 and ext3 that provide you with a slow but good read/write access. I have been using these for some time on Windows XP. Now, I have no idea if these would work with ext4.

If you have so much data to save, your best bet would probably be a live session with an external hard disk drive. Hopefully, you have such a thing or a good friend that could lend you one. At least until you copy the documents to some safer place.

---

### Post by agp27 on 2010-01-03
Whats an external hard drive? and will a memorex music cd-r work to put the live cd on?

---

### Post by Anuovis on 2010-01-03
> **agp27 said:**
> Whats an external hard drive? and will a memorex music cd-r work to put the live cd on?

Any CD-R will do.

External HDD is what I would use in your case, because they have good storage and can be connected via USB without any hassle. Other devices with a lot of memory might be used as well.
_**[Google it...]("http://www.google.com/search?hl=en&source=hp&q=external+hard+disk+drive&btnG=Google+Search")**_

Maybe there are other ways to save your data, like connecting your PC to another machine and copying everything over there. In any case, you need to find those 200 GB somewhere.

If that data is not that important, you might just proceed by fixing your hard drive. Maybe you have backed it up somewhere, no?

[U][B][URL="http://www.google.com/search?hl=en&source=hp&q=external+hard+disk+drive&btnG=Google+Search"]
[/URL][/B][/U]

---

### Post by agp27 on 2010-01-03
no. i dont have anything backed up..

---

### Post by agp27 on 2010-01-03
im downloading ubuntu-9.10-desktop-i386.iso is that right?

---

### Post by teward on 2010-01-03
> **dmaxel said:**
> Sorry, I know this is slightly off topic, but I'm having similar problems with my server, it having I/O buffer errors. How were you able to determine which sectors were going bad?

Any regular CD-R would work just fine. Just make sure that you download the right LiveCD and burn it using an ISO burning application.

If you're getting I/O buffer errors, it means one of the drives on your computer/server is dying.  this may have been resolved already, but I've had this issue with several computer devices, so its a good indication your devices are screwed over.

---

### Post by agp27 on 2010-01-03
I got it on a cd.. now what do i do?

---

### Post by Anuovis on 2010-01-03
> **agp27 said:**
> I got it on a cd.. now what do i do?

Read the posts. If you want to do the backup, find yourself a storage with 200 GB (or how much you need). Boot the system from the cd and copy all the data. 

BTW, if you are really not that knowledgeable about the computers, you might be better of finding someone who could help you directly. These forums are very helpful and you could probably solve anything you want by just reading them. But if you feel it is too difficult to follow the advice people are giving here, at least do not do anything you can not understand. Because you might end up in the worst situation than you are now.

For the future, always have a backup of important things. Especially when you are doing something critical with your computer, like moving to the new OS.

---

### Post by agp27 on 2010-01-03
i think i can do it. but how do i boot. im at the page where it says try ubuntu without change, install ubuntu and other stuff

---

### Post by agp27 on 2010-01-03
i found it but its not letting me do anything cus i dont have permission to the folder. will it work if i open it in root nautilus?

---

### Post by Anuovis on 2010-01-03
> **agp27 said:**
> i found it but its not letting me do anything cus i dont have permission to the folder. will it work if i open it in root nautilus?

Which folder? Is it your *Home*?
Trying Nautilus as root would do no harm, just make sure you are not deleting something important.

---

### Post by agp27 on 2010-01-03
i did.. im getting it all transsferred... when im done transferring everything, what would happen if i installed the ubuntu 9.10?

---

### Post by Anuovis on 2010-01-03
> **agp27 said:**
> i did.. im getting it all transsferred... when im done transferring everything, what would happen if i installed the ubuntu 9.10?

Glad you at least saved your data. 
I can not help you with the hard disk problem. If it is a hardware issue, a fresh installation would not help. It would be wise to check your disk anyway. But I do not know how to do this. Search web and these forums, maybe you will find the answer.

And don't give up on Ubuntu yet :)
Good luck.

---

### Post by agp27 on 2010-01-04
Ill try to keep using it.. i like the speed of it and how it looks. so ill keep using it until i get 1,000 dollars for a Mac...

---

