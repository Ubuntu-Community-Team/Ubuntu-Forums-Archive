---
title: "Tar Backup..?"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-03-12
In creating a "tar" backup of everything on the hd, I found I accidentally left an Ubuntu image CD on the desktop...  Seems I must delete this "backup, and start the "tar" again...   "WhooH!"..

Plus.. I noticed a lot of "games" stuff in the backup...  I uninstalled Games... Is there a pile of games-junk still in the OS..?

I saw a lot of printer files copying..I use only an "HP 3 in 1"..  How do I delete all those unwanted printer-files..?  Are there all kinds of drivers to clean out..?

Is there a custom software that safely eliminates all the crap you want out of the OS..?  

Once you get rid of all the extras stuff..  just how many megs is a bare-bones Ubuntu 810 OS..?

All I want is full SeaMonkey, fully loaded Gimp, HP 3/1 printer, full Music, Pix, Conky, FW, AVS, and the various necessary peripherals to make that a system...  
Has anyone written a package that strips out all the junk..?
I'd like to test it on a spare U-810 hd...


Can I delete from a tar-backup..?

Can I add to a tar-backup..?

If I delete all mention of "games", and all printer files that I don't use, does that damage the OS in any way..?

Can I delete the tar backup..?

How do I gets it to CD..?

It's still copying...   How long does this take..?


I seems that I should have deleted the image download, the music and the pix, before I started the backup...  I can easily add the music and pix with a flash-d...

So..  will this backup make a trouble-free bootable CD..?

What else should you do before you make a backup..?

______________________


Oh Poo!..  it's still making the backup, and I touched the cursor to the update icon, and it reads there's 36-updates...  but I pulled the internet wire from the tower to go into root...  Is that a phantom 36-updates, because the Internet cable was pulled..?  Or did the thing find something while it was backupering..?

Obviously I need to delete this backup, and do some updating and cleanups, and redo the backup...

---

### Post by blueridgedog on 2009-03-12
I suggest you take a different approach.  For making a backup of the "system", I suggest remastersys.  You can install it with synaptic.

Once you make a backup using remastersys and burn it to disk, you can recreate your working system.  From there, all you need tar for is to backup your user data.  Typically that means you will only need to tar your home directory.  I also zip my tar's for space economy with:

```
tar cvfz homebackup.tgz /home
```

You can add to or delete from a tar file.  look at:

```
man tar
```

and pay attention to --delete and --apend

---

### Post by DonaldJ on 2009-03-12
Thanks blueridgedog


Does remastersys backup do a bootable image CD of the whole OS, as I've got it..?

I wants a CD that I can use to install the whole system onto new hd's...

I'm searching the commands for "How to completely delete the polluted tar-backup"..?

Then the plan is to do a major cleanup.. and then do a backup, without all the clutter...  But every time I try to do a serious major cleanup in Ubuntu I ends up destroying the install...  These are "painful" timely lessons...

OK..  So I've got all my treasures onto flash drives, safe, so I can't lose anything I value...
I'm about to delete all the music and pix files... I can load them to hd's as required...  I doubt mum would appreciate 1600 nudes in her PC...  Where's the flower-hacker guy when I needs him?..  He does so sell pretty flowers...
I will delete the tar backup as soon as I figure how...
Then do the updates, and Dash, and hope it doesn't wreck the OS...
Then I should do a cleanup with "sudo apt-get autoclean"...
I tried to get "localepurge", but it wouldn't come up in the packages box.. seems I haven't got the required repository...  Maybe I can find it in the salad lady's thread..?
Then I suppose I should install and run "deborphan"..?
I should find a way to get into the printer drivers files, and knock out the ones I don't need...  I just wonders how many other unneeded drivers, and junk, I can find to delete..?  I figure the more junk I eliminate, the faster the image CD will install...

Have I got it right..?

___________________________________________


I can't understand how to assemble commands from "man tar"...

I figure all I need to do is bring that backup up, and tell the terminal to delete it...  
But if I just delete everything tar, that would probably destroy the OS..  so, with my limited knowlege about Ubuntu, and my extreme temper, and failing patience, to cleanp the huge mess I've made it seems I must reinstall Ununtu...  
Oyie! sometimes I hate me...  I cause me so much difficulty and hardship.. the story of my life...

---

### Post by blueridgedog on 2009-03-14
> Does remastersys backup do a bootable image CD of the whole OS, as I've got it..?

I wants a CD that I can use to install the whole system onto new hd's...

Yes, the DVD that is made is bootable.

> I'm searching the commands for "How to completely delete the polluted tar-backup"..?

I recommend you

```
rm tarfile.tar
```

That is the easy way, then you can start over with what you want.

> Then the plan is to do a major cleanup.. and then do a backup, without all the clutter...  But every time I try to do a serious major cleanup in Ubuntu I ends up destroying the install...  These are "painful" timely lessons...

You should "cleanup" via synaptic but be careful.  Don't be so concerned with space that you cripple your install.

> Have I got it right..?

Yes, basically, tidy up your home directory, backup your files then experiment with remastersys.


> I can't understand how to assemble commands from "man tar"...

Bring up a terminal, cd to the directory where the tar is and type rm nameoftarfile.tar.

---

### Post by DonaldJ on 2009-03-14
I changed hd's, to a fresh Ubuntu install one.. and added most of the fun softwares I like.. but I need to do a couple more searches to find if there are others I should have in a me-system...

I'm thinking I should add all the necessary items to build a good Conky, as soon as I find what's required...

And I really do so want a "conga and specialty drums" software..  but haven't found anything yet...  Is there one out there free or even for-sale..?  I have hydrogen and freebirth...

How do I delete all the printer drivers I won't be needing..?
Has anyone built a personal cleaner-package that strips-out all the extras junk safely..?  Like you know how you would rip through Windows, deleting all the sounds, and pix, and pox, and notes, and spies, and links, and junk...  I may not be necessary with Ubuntu, but I wants to determine that for myself... I'm still a little "shell-shocked" and scarred from the many years in the microsoft windows hell and meatgrinder...

Once I get this hd like I wants it, I'll do the bootable CD backup.. then test "the attack of the cleaners"..  and if the OS is still OK, I'll make a second backup CD...

I've got ten hd's Ubuntu loaded now... And I hears 904 comes out in less than a couple months...  I'm supposing 904 will be an upgrade, as well as an image CD..?

---

### Post by blueridgedog on 2009-03-15
```
How do I delete all the printer drivers I won't be needing..?
```

I would not bother, as they are not that big and not worth worrying about...your remastersys ouput will be a DVD anyway as you have added software.  So getting it down from 1.6 gig to 1.5 is sort of moot.  I have a full system with many many things installed and my boot dvd is 1.6 gig.
```

Has anyone built a personal cleaner-package that strips-out all the extras junk safely..?  Like you know how you would rip through Windows, deleting all the sounds, and pix, and pox, and notes, and spies, and links, and junk...  I may not be necessary with Ubuntu, but I wants to determine that for myself... I'm still a little "shell-shocked" and scarred from the many years in the microsoft windows hell and meatgrinder...

```

I recommend you spend time with the OS, then make your own mind up as to what is required and what is not.  It is pretty minimal to start with

---

### Post by DonaldJ on 2009-03-15
OK.. I'll take your words as "boss-prime"...  I've got 4-gigs in the OS already, and the Conky stuff will probably take up a bit more..  And it's running fast and snappy, like it should...  I suppose I can leave all its "lizard-eggs" in the nest...

Someone evil as h sure wants desperately to get into this hd to make a mess...  I'm getting a couple ultra high-tech weird-emails daily from extreme hackhead zombies...  It sure is a solid secure OS, but if there are vulnerables, I'm sure they'll find them... I'm probably their number one target... They're hungry...  It'll be a good test for Ubuntu's strengths...  
The demons will find the holes, if there are any, and I'll detail the attack MO's, and wise Ubuntu development people will patch them up secure.. but so far the demon-vampires haven't crashed this OS even once...

Are there bad things that can slam Ubuntu should I open a yuk email..?

---

### Post by blueridgedog on 2009-03-15
> Are there bad things that can slam Ubuntu should I open a yuk email..?

Generally no.  Emails typically come with windows code as executables, and at worse you may corrupt you install of wine (if you even have it).  That is a trivial mater of deleting and re-installing wine.  However, a recent test of most viruses showed that they still failed to function under wine.

I don't worry about it.

---

### Post by DonaldJ on 2009-03-15
I have no need for the Wine program..  I don't use it..  
Windows stuff doesn't work as good as the Linux stuff...  
I suppose for some it's like a necessary "soother-comforter" for when they're being weaned...
I'm distancing myself as far away from the Windows-demon as I can, after what it ran me through...

_______________

I tried synaptic and add/remove to get "remastersys"..  and it doesn't get it..?
I'm supposing I need to know the line to key into the "the repository"..?
I added: deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/ ...

Fixed...

---

### Post by DonaldJ on 2009-03-15
That PC is making its remastersys backup...  


I sees: "file fragments are present in file system"
"skipping data recovery file?"

Is that bad?..

____________________________________


It says, the backup  "/home/remastersys/remastersys", is ready to make a DVD, but I've looked everywhere for it, and just can't find the dern thing..?   I feels like I'm "chasing my tail"...  woof woof!..

---

### Post by blueridgedog on 2009-03-16
I don't think so...

The command I used was:

```
sudo remastersys dist
```

It will make an ISO image in /home/remastersys that you can burn and boot from.

---

### Post by DonaldJ on 2009-03-16
I set that command..  and it's doing same as what it did with remastersys.. making another copy...  Seems it erased the previous copy..?  It said something about "cleaning up a previous something"...

Did yours start to record to DVD right after it created the copy..?

My problem is that I gets the copy built, four times now.. then it doesn't start copying to CD..?  So I search(d) all over the hd for that copy, to place it into the CD burning software's window to tell it what to burn an image of...

I've searched in: Home, all files, file system, desktop, various CD burners, Remastersys controls, "under the tower"...  
The blank DVD is in the slot...  The DVD RW is working...

Is there another special command that gets the backup started copying to the DVD..?  or should it follow through, and start copying to DVD with that command, after it's built the backup..?

____________________________


I've tried many times in the past five years to make bootable image CD's of various OS's, and haven't been able to make a one... All I ever do is waste CD's...  This is so frustratin', like going camping in July, in the mountains, and waking up to a foot of snow...

---

### Post by blueridgedog on 2009-03-16
> Did yours start to record to DVD right after it created the copy..?

No, it places an ISO image in /home/remastersys

---

### Post by DonaldJ on 2009-03-16
What's the process to get it from the point that it is a file in Home called "/home/remastersys"...   It says that file is ready to burn to CD, but I can't find any other mention of it anywhere in the computer...  The plan is to drag the file to the burn window, and have it make the CD, but I can't finds it to makes it..?  How did you get yours to make the CD from a file that can't be found..?

---

### Post by blueridgedog on 2009-03-17
Perhaps remastersys is failing...is there any output after you run the command that would imply an error?

---

### Post by blueridgedog on 2009-03-17
When I run remastersys, here is the final output:

```
Creating md5sum.txt for the livecd/dvd
Creating customdist.iso in /home/remastersys/remastersys
Creating customdist.iso.md5 in /home/remastersys/remastersys
/home/remastersys/remastersys/customdist.iso is ready to be burned or tested in a virtual machine.
 
Check the size and if it is larger than 700MB you will need to burn it to a dvd
 
1.8G /home/remastersys/remastersys/customdist.iso
 
It is recommended to run 'sudo remastersys clean' once you have burned and tested the customdist.iso
```

Note that the dvd image is then /home/remastersys/remastersys/customdist.iso.

I can burn this by double clicking on it.

To run remastersys I first unmounted any non-system drives (otherwise it attempts to include them) then ran:

```
sudo remastersys clean
sudo remastersys dist
```

---

### Post by DonaldJ on 2009-03-18
Thanks for sticking it out with me in this little nightmare...

Pesky glitch from your end..  Nightmare on my end...
_____________________


Yesterday I removed that hd, and replaced it with a little 3.7 gig spare hd..  and managed to get Ubuntu-810 on it with no troubles, along with the required updates, and 300 custom peripheral updates, and 70-megs of pix..  with a gig to spare yet...  
It's probably best I run my music from flash or CD...

_____________________


Back to this silly backup to CD prob...

I'll put that troublesome hd back in, and bring up remastersys, and give your double-clicking suggestion a few tries...

The CD unit is a new RW LG DVD cheapy, but it does read and record CD's and DVD's...

I'm wondering if there's a tiny bit of a problem with drivers in Ubuntu for the LG..?  Are there tests I can do to determine the compatibility of the LG CD ROM to the Ubuntu system?..  I'm wondering if there's a common denominator with the few folks who are experiencing this same little prob..?   besides the "slight wetness behind the ears"..?  I'm wondering if we're all running the same cheapo LG DVD ROM..?

Is there a card that makes DVD ROM's work better..?

I'm gonna keep-on banging-away at this problem till I gets it...

Can I run something to find if the proper CD drivers are properly installed..?

Is there something else that must be installed with Remastersys..?

I'll do some more trying, and get back...

---

### Post by Royce2u on 2011-06-18
> **blueridgedog said:**
> I suggest you take a different approach.  For making a backup of the "system", I suggest remastersys.  You can install it with synaptic.

Once you make a backup using remastersys and burn it to disk, you can recreate your working system.  From there, all you need tar for is to backup your user data.  Typically that means you will only need to tar your home directory.  I also zip my tar's for space economy with:

```
tar cvfz homebackup.tgz /home
```You can add to or delete from a tar file.  look at:

```
man tar
```and pay attention to --delete and --apend
   	 	 	 	 	 	  

I'm trying to backup my files onto a DVD with Remastersys. As far as I can tell, everything is ready to go, which is to say that Remastersys reports that my files are correctly copied—my md5 files. So I assume I just need to transfer the resulting folder onto a DVD. But when I tried to do that I get an error message saying that vmlinuz could not be opened. Consequently, nothing was copied onto the DVD.
 

 So how have I messed things up?
 

 Thanks in advance!

---

### Post by blueridgedog on 2011-06-21
What command did you use to make the image?

---

