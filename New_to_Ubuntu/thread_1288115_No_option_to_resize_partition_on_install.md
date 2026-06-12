---
title: "No option to resize partition on install"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by scottiec809 on 2009-10-11
I have run into a little problem while trying to install ubuntu. When I get to the disk repartitioning step, it only give me the options, Guided—Use Entire Disk and Manual, and not the third, Guided—Resize Partition. I'm almost positive that it isn't the CD because I have tried to use the one I burned the image to, and a ubuntu disk I got in Linux Format magazine. I really do not know what it could be. Please help me out if you can.
Thank you.

---

### Post by rippin on 2009-10-11
> **scottiec809 said:**
> I have run into a little problem while trying to install ubuntu. When I get to the disk repartitioning step, it only give me the options, Guided—Use Entire Disk and Manual, and not the third, Guided—Resize Partition. I'm almost positive that it isn't the CD because I have tried to use the one I burned the image to, and a ubuntu disk I got in Linux Format magazine. I really do not know what it could be. Please help me out if you can.
Thank you.

Try using the non-GUI install option.

---

### Post by RichardLinx on 2009-10-11
Did you go into the advanced options?

---

### Post by kansasnoob on 2009-10-11
I prefer this method:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

That way I control the partitioning before I ever start to install, and I know exactly how Ubuntu "sees" the partitions, that is there is no drive C or drive E, etc. Instead partitions are numbered sda1, sda2, etc, where the **a** in sd**a** means drive #1, and **1** or **2** designates partition #1 or #2, etc.

You may want to spend some time and browse Herman's whole guide:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by scottiec809 on 2009-10-11
> **RichardLinx said:**
> Did you go into the advanced options?

I did try the manual partition. It only gave me the option to create a new partition table, which wants you to format all partitions, so that was a fail.

What I'm probably going to do, what I should have done in the first place, is just partition it myself with some kind of free partition software before I run the boot CD, which I think is what kansasnoob was suggesting (sorry I didn't click on the link, I just assumed). It just seems like the only probable solution. 

I still want to know what happened with the boot CD if anyone knows, just out of curiosity and for future reference.

---

### Post by tpjk on 2009-10-11
> **scottiec809 said:**
> What I'm probably going to do, what I should have done in the first place, is just partition it myself with some kind of free partition software...

try the gparted live cd:
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

---

### Post by mcduck on 2009-10-11
> **scottiec809 said:**
> 
I still want to know what happened with the boot CD if anyone knows, just out of curiosity and for future reference.
Perhaps your windows partitions wasn't cleanly unmounted, or properly defragged, before starting the Ubuntu installers.

Those are the two reasons I've found to disable the option to resize partitions with the Ubuntu installer.

And the solution is of course simple: boot windows into safe mode and defrag the partition (safe mode becaus it allows moving any fles that would be unmovable when windows is running in normal mode), then start the Windows at least once normally to make sure the file system gets cleanly unmounted.

edit: Still, if you decide t just use some other partition tool instead, I recommend not actually creating any new partitions with it, but instead just making some empty, unpartitioned space on the drive. Ubuntu's installer will detect unpartitioned space and offer you an option to use that for Ubuntu. If you create any partitions you'll have harder time selecting the actual partitions to use, and you'll need to reformat the partitions anyway during the install so you'd just waste your time creating the partitions beforehands.. ;)

---

### Post by spiralx on 2009-10-11
Personally, I think the whole Ubuntu partitioner sucks.

I have just bought a new laptop, with Vista spread over 500GB of hard drive.

Fine, I thought:  I'll use my Ubuntu 9.04 install disk to put Unbuntu on, and use the partitioner part to divide the disk in two.    Defragged the Vista side first, and off we went.

Well!  First of all, it went and tucked itself into 2.5 GB of "free space".  Whether I went for option 2 ("instal side-by-side"), or option 3 ("use the largest free space"), it did the same.  No way of telling it to use a larger partition size.  

Much swearing and wasted Saturday morning time, before I gave up.

Went BACK to Vista, downloaded Easeus Partition Manager, partitioned the disk into two, erased the two useless Ubuntu partitions, then went back to installing Ubuntu.  F*ck me.  It STILL sees the disk as all Vista, and insists on installing into 2.5GB of "free space".

Went back to Vista (again), re-partitioned the disk into two (again), wiped out the silly little Ubuntu partitions (again), THIS TIME set up the second partition as "unformatted", then went back to reinstall Ubuntu for the third (or fourth, I'm losing count at this stage) time...

Hooray:  it sees the partitions as they are - finally.  So, install "side-by-side", assuming it will use the unformatted space.  And whaddya know.  It STILL goes for 2.5 GB , and leaves the entire unformatted area alone. 

Go BACK into Vista, call up Easeus, but guess what - it won't offer me the option of resizing "other".

So - I go into Ubuntu and apt-get "Gparted" - but once installed, it doesn't show up anywhere ("Applications" would be my logical choice, but not there, not anywhere).

So right now I'm wondering whether I haven't wasted my entire Weekend with this rubbish that is Ubuntu -  because no-one 'normal' would, given this farrago.  

And if I wipe out these partitions, I'm left with GRUB which then won;t work, so I can't get into Vista.  

(Oh, and by the way, Brasero is also useless in burning ISO images.  It ends by "creating a checksum", which just counts up and up and up, apparently at random).   You finally lose patience and close it, but the disk is un-useable.  Guess wot - I went into Vista and burnt it there.

I guess Windows is the way forward for me, from now on.

---

### Post by tpjk on 2009-10-11
> **spiralx said:**
> Well!  First of all, it went and tucked itself into 2.5 GB of "free space".  Whether I went for option 2 ("instal side-by-side"), or option 3 ("use the largest free space"), it did the same.  No way of telling it to use a larger partition size.

what about the 'manual' option? that's usually the one you want to go for if you need total control over what happens to your ubuntu install...

> So - I go into Ubuntu and apt-get "Gparted" - but once installed, it doesn't show up anywhere ("Applications" would be my logical choice, but not there, not anywhere).

you can start every installed application pressing alt f2, typing the name of the application in the window that appears and hitting enter.

---

### Post by mcduck on 2009-10-11
> **tpjk said:**
> what about the 'manual' option? that's usually the one you want to go for if you need total control over what happens to your ubuntu install...



you can start every installed application pressing alt f2, typing the name of the application in the window that appears and hitting enter.

+1 for both of these.

The 2,5GiB problem is a known issue on some setups when using the automatic partitioning option in 9.04's installer. However the manual partitioning works just fine.

gParted is actually included by default on Ubuntu's CDs. It's in System/Administration/Partition Manager (whic is also where it will end on installed Ubuntu systems, since partition management definitely counts as administrative task).

---

### Post by spiralx on 2009-10-11
That's interesting.  For what it tells you about Ubuntu, as much as anything else!

Yes: been and looked at "manual".  God knows what all those options mean.  I did attempt them, but it wouldn't 'go' (told me I needed a "root" option as well, but why?).

And really:  I shouldn't have to know.  The 'pretty picture' partitioner should do the thing properly.  Now, I'm not totally computer-deficient:  I've played around with Windows since 3.1, and Linux since 2002.  

But - every time - I end up getting frustrated with things that don't work in Linux, that do in Windows.  And every time, I end up going back to Windows to sort something out.  The fonts that don't exist (so your web-pages look rubbish) - unless you somehow 'know' to apt-get "proprietary" stuff;  the DVDs that don't play (ditto);  the Flash that doesn't work;  the audio that is silent - and in the case of my laptop, the built-in webcam that doesn't work, and the toggable touchpad that switches off but won't switch back on (and no, the work-around I Googled for in Ubuntu doesn't work either).

Rant over!  It's now 1pm, I've wasted all morning (like yesterday) re-installing Ubuntu over and over again, trying to get it to see the partitions properly, and I've had enough.

What Linux-geeks may see as an interesting learning curve is for me (and, I suspect, most computer users) a waste of time and effort. 

I may try 9.10 when it is released.  But right now, I'm waiting for my copy of Windows 7 so that I can get rid of that GRUB nonsense once and for all.

(And who thinks that GRUB could do with a make-over besides me?  It's DOS-ugly, throws up a list of options that are pretty meaningless to most people, I imagine;  and to try and rearrange the boot list is a small nightmare in itself.  Mandriva sorted that years ago - why couldn't Ubuntu follow suit?).

---

### Post by spiralx on 2009-10-11
I'm just a sucker for punishment, I guess.

I should know when I'm beat, shouldn't I.

But no;  ever the optimist, I went and installed Ubuntu (yet again) to see about this Gparted thing.

Gparted is not installed by default in 9.04.  You have to know to apt-get it.  Then you have to know that it mysteriously appears in Systems - Administration as "Partition Editor".

(Is it too much to ask that the install have a notice for this?).

And to my absolute horror - the install had not only parked Ubuntu in the (by now) familiar 2.5Gb "free space", IT HAD ALSO REVERTED MY PREVIOUS PARTITIONING - so that Vista once more filled 455GB disk space!

Gparted, by the way, doesn't work.  Almost every option is greyed out. In Vista, I can resize my Vista partition using my downloaded Easeus Partiton Manager, if not "other".  

In Gparted, NOTHING is resizeable.  Reading through the "Help", it seems I have to (somehow, I don't know how) use a LiveCD to get to the hard drive sections.  ??

It just goes on.  And on.  

I give up.  I'm going back to civilian life, with Windows.

---

### Post by mcduck on 2009-10-11
> **spiralx said:**
> I'm just a sucker for punishment, I guess.

I should know when I'm beat, shouldn't I.

But no;  ever the optimist, I went and installed Ubuntu (yet again) to see about this Gparted thing.

Gparted is not installed by default in 9.04.  You have to know to apt-get it.  Then you have to know that it mysteriously appears in Systems - Administration as "Partition Editor".

(Is it too much to ask that the install have a notice for this?).

And to my absolute horror - the install had not only parked Ubuntu in the (by now) familiar 2.5Gb "free space", IT HAD ALSO REVERTED MY PREVIOUS PARTITIONING - so that Vista once more filled 455GB disk space!

Gparted, by the way, doesn't work.  Almost every option is greyed out. In Vista, I can resize my Vista partition using my downloaded Easeus Partiton Manager, if not "other".  

In Gparted, NOTHING is resizeable.  Reading through the "Help", it seems I have to (somehow, I don't know how) use a LiveCD to get to the hard drive sections.  ??

It just goes on.  And on.  

I give up.  I'm going back to civilian life, with Windows.

Farewell, then.

Had you actually asked for instructions or help with the partitioning, or used one of the numerous tutorials available with a simple Google search, you'd probably have a functioning Ubuntu system by now.

Simply ranting for problems doesn't really help, even less when done in somebody else's thread. :)

---

### Post by spiralx on 2009-10-12
See, now, that's the kind of attitude that gets the forums a bad name.
 
And I didn't hijack this thread, I added to it.  Though this morning, I see that's it's a "known bug" that will problably only be 'fixed' with 9.10.
 
Really, guys.  Surely it's obvious that if the installer doesnt work, it stops there, for most people??

---

### Post by mcduck on 2009-10-12
What? Helping those who *want* help gives these forums bad name?

Besides, most of the people on these forums are actually *running* Ubuntu, so obviously they have also managed to install it. :)

---

### Post by theozzlives on 2009-10-12
> **spiralx said:**
> See, now, that's the kind of attitude that gets the forums a bad name.
 
And I didn't hijack this thread, I added to it.  Though this morning, I see that's it's a "known bug" that will problably only be 'fixed' with 9.10.
 
Really, guys.  Surely it's obvious that if the installer doesnt work, it stops there, for most people??

Sounds like user error to me. "Ubuntu sucks, the forums suck", is all you've posted in someone else's thread who is asking for help. NOT to hear someones opinion of Ubuntu. Windows 7 is a good service pack for Vista and should've been treated as such. Apparently you lack the common sense to create a thread and ask for help. Go back to "virus world" you deserve Windows. I've read so much ranting that I forgot what the original problem was, now I got to go back and look.

---

### Post by theozzlives on 2009-10-12
> **scottiec809 said:**
> I have run into a little problem while trying to install ubuntu. When I get to the disk repartitioning step, it only give me the options, Guided—Use Entire Disk and Manual, and not the third, Guided—Resize Partition. I'm almost positive that it isn't the CD because I have tried to use the one I burned the image to, and a ubuntu disk I got in Linux Format magazine. I really do not know what it could be. Please help me out if you can.
Thank you.

If you're using XP, you should be able to defrag the drive several times, exit Windows properly, use gparted on the Live CD and resize your NTFS partion.

If you're using Vista, you need to use the resize tool that comes with Vista. NOT a third party app.

---

### Post by Bartender on 2009-10-12
scottie, how many partitions you got, and what kind?  Sometimes the problem is that the Ubuntu installer sees 4 primary partitions, or 3 primary and an extended, and it doesn't know what to do.

---

