---
title: "I'm toast"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by Gavinthechop on 2009-08-13
Hi all
 
I just installed Ubuntu on a spare laptop that had Windows XP on it. It also had hundreds of photos of my daughters first 18 months! I was unaware that the Ubuntu installation would delete the entire hard disk. Is there any way I can recover these pics 'cause my wife will leave me (or worse) if I can't?!:(

---

### Post by Revolutionary101 on 2009-08-13
Do you know if the Windows partition is still on the hard drive? To install gparted by typing this into terminal

```
sudo apt-get install gparted
```After doing that you should open Gnome Partition editor in System>Administration>Partition Editor. Then look for the largest NTFS partition. If it isn't there then it is not recoverable. (At least that I know of)

---

### Post by QIII on 2009-08-13
Ooof.  Yeah, if you selected "Use entire disk", it used the entire disk for the Linux partition.

Don't despair just yet.  Those little magnetic particles may or may not have been disturbed, except perhaps for the 5GB or so of space where the actual OS was laid down.  Repartitioning does not necessarily mean "deleted everything."  That's why computer forensics experts can find all those files that an embezzler thought he had deleted.

I've had good luck with testdisk ([https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)).  There are several others, which will probably be recommended as others look at your post.

For now, don't do anything with the machine to avoid any further possible loss of data.  Read through the link above and any others that will follow from other posters, and carefully follow the instructions.

But you might want to go out right now and buy a dozen roses and a box of chocolates...

And from now on I recommend a basic tenet of computing:  Back important files up before you launch into the unknown.

(Edit:  There is also photorec, which is really well tuned for image files...)

---

### Post by doas777 on 2009-08-13
ok, first shut down the laptop immediately. do not boot off that hard disk again until the problem is resolved.

now you will need:
1) a live cd like this one: [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)
2) a external storage device larger than the hdd you wish to recover

boot from the live cd and start by running testdisk:
[http://www.howtoforge.com/data_recovery_with_testdisk]("http://ubuntuforums.org/showthread.php?t=387922")

if you can't restore your whole partition, then the next thing to try is photorec (specifically made for retreiving photos):
[http://manpages.ubuntu.com/manpages/intrepid/man1/photorec.1.htm](http://manpages.ubuntu.com/manpages/intrepid/man1/photorec.1.htm)

if you haven't done too much to the hdd except install ubuntu, then you have an alright chance of retrieving them, but no one can make any guarantees. data recovery is as much art as science.

---

### Post by LewRockwell on 2009-08-13
!
!
***_stop! Don't do anything else until you get proper instructions!***_
!
!

---

### Post by LewRockwell on 2009-08-13
> **Gavinthechop said:**
> Hi all
 
I just installed Ubuntu on a spare laptop that had Windows XP on it. It also had hundreds of photos of my daughters first 18 months! I was unaware that the Ubuntu installation would delete the entire hard disk. Is there any way I can recover these pics 'cause my wife will leave me (or worse) if I can't?!:(

go get yourself a copy of Parted Magic which has a bunch of utilities on it

[http://partedmagic.com/](http://partedmagic.com/)

read up on Testdisk and Photorec(which are on Parted Magic)

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

[http://en.wikipedia.org/wiki/Photorec](http://en.wikipedia.org/wiki/Photorec)

.

---

### Post by Maheriano on 2009-08-13
Don't you have regular backups of such important files?

---

### Post by LewRockwell on 2009-08-13
I also wanted to point out that if windows doesn't boot up but you think it should still be there since you were attempting a dual-boot install...

Then you may just have a problem with your grub configuration

Using Gparted from a LiveCD should show you what's going on partition-wise

Keep us posted on your progress!

.

---

### Post by doas777 on 2009-08-13
> **LewRockwell said:**
> !
!
***_stop! Don't do anything else until you get proper instructions!_***
!
!
good advice.

---

### Post by QIII on 2009-08-13
If it is any consolation, I usually dual boot on two separate drives.  One of the things I do is unplug the drive I am not installing the second OS (like Ubuntu) on so I don't do just what you may have done.

Then I edit my menu.lst and plug the other drive back in.

Of course, when you are working under a dark desk and don't pay attention and unplug your brand new disk you bought to put Ubuntu on and leave your wife's Vista disk plugged in...

Testdisk got it all back.

---

### Post by credobyte on 2009-08-13
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) ;)
Regarding the fact by itself, why would your wife leave you ? It's a damn computer and damn pictures .. you'll have thousands of them.

---

### Post by Gavinthechop on 2009-08-13
Thanks everyone I'll give it a go!:cry:

---

### Post by LewRockwell on 2009-08-13
> **QIII said:**
> If it is any consolation, I usually dual boot on two separate drives.  One of the things I do is unplug the drive I am not installing the second OS (like Ubuntu) on so I don't do just what you may have done.

Then I edit my menu.lst and plug the other drive back in.

Of course, when you are working under a dark desk and don't pay attention and unplug your brand new disk you bought to put Ubuntu on and leave your wife's Vista disk plugged in...

Testdisk got it all back.

you lucked out...

use a flashlight next time!

.

---

### Post by Gavinthechop on 2009-08-13
Okay, I managed to get Testdisk running and I get a huge list of files - none of them which resemble the photos I want. I would like to try PhotoRec but I don't have any idea of how to load it onto the computer. I have a good understanding of MS-DOS and Windows but absolutely none about Linux/Ubuntu and am finding it extremely difficult to grasp. Any input would be most appreciated - yup, I am an idiot for not backing up beforehand.

---

### Post by alphacrucis2 on 2009-08-13
> **Gavinthechop said:**
> Okay, I managed to get Testdisk running and I get a huge list of files - none of them which resemble the photos I want. I would like to try PhotoRec but I don't have any idea of how to load it onto the computer. I have a good understanding of MS-DOS and Windows but absolutely none about Linux/Ubuntu and am finding it extremely difficult to grasp. Any input would be most appreciated - yup, I am an idiot for not backing up beforehand.

I think photorec is part of testdisk

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step")

---

### Post by HermanAB on 2009-08-13
Hmmm, I do think that the Ubuntu developers are almost criminally negligent for making such a bad installation wizard.  All the older distributions (Mandriva, Redhat, Fedora, Suse) will by default make a dual boot system if it detects the presence of Windows.  Canonical could have copied any of those, but no, they had to go and try to re-invent the wheel and of course came up with a square one.  The result is that many new users have made the same mistake and lost all their old data in the process.

However, that being said, you may enjoy the second marriage...

---

### Post by steveneddy on 2009-08-13
My opinion:

Stop now!

You were not aware that installing an operating system and selecting "Use Entire Disk" would erase information or the other operating system.

You don't need to fix it.

Take the machine down to a professional data recovery specialist and let them retrieve the data properly.

Educate yourself a little before doing something on a machine with important data on it.

Now go slap your b*lls with a long heavy object continuously until you remember this lesson for next time.

**
I am aware that it is possible for him to recover his data with other software, but I believe that his lack of understanding of computers in general would cause further damage to the data and his marriage. I only make this judgement on the basis of the first post on the thread.

If children's pics are involved and the integrity of the marriage is dependant on proper data recovery, I would wholeheartedly recommend professional assistance in this particular circumstance.

**

---

### Post by bodhi.zazen on 2009-08-13
First as has already been suggested, stop using the hard disk.

Next decide if you want to attempt to fix this yourself or take it to a professional.

If you want to fix it yourself, first check the partitions. Is windows still there, if so repair and boot windows.

If not, image the hard drive and work from the image. Try photorec, but be warned, it will recover the files but not the file names (the names of the files will all be gibberish).

Some files may be intact, others not. You will then need to manually, one by one, look at and rename or fix the files.

---

### Post by steveneddy on 2009-08-13
> **bodhi.zazen said:**
> First as has already been suggested, stop using the hard disk.

Next decide if you want to attempt to fix this yourself or take it to a professional.

If you want to fix it yourself, first check the partitions. Is windows still there, if so repair and boot windows.

If not, image the hard drive and work from the image. Try photorec, but be warned, it will recover the files but not the file names (the names of the files will all be gibberish).

Some files may be intact, others not. You will then need to manually, one by one, look at and rename or fix the files.

Master

[IMG]http://www.precisionmartialarts.net/images/Dana,%20Na%27ala%20Bow.JPG[/IMG]

---

### Post by Gavinthechop on 2009-08-14
Okay!! I have managed to get somewhere, I think! I now have a screen on photorec that says "351 file saved to /home/ubuntu/recup_dir". What the heck do I do now? :confused:

---

### Post by Gavinthechop on 2009-08-14
:):) Thanks all, I appreciate the humour right now, helps me relax. It ain't all bad, after all, I'm 6'4" against her 5'2" ..... hell I'm still scared!  I've left the damn computer on the screen of promise until someone can tell me where/home/ubuntu/recup_dir is. PS she won't really divorce me but she is mostly at the same height as .........:shock:

---

### Post by XKCD64 on 2009-08-14
Just stop what ever you are doing.  Even me, who knows alot about this kind of stuff would take it to a professional. 

They can do this for you.  It will cost money, but it's worth it.  Don't take the chance of losing them forever, take it to a specialist.

---

### Post by tomasrey88 on 2009-08-14
Repartitioning a drive does not mean it was erased. It just means that the data is not recoverable with normal means. You need to take this hard drive to a forensic computing expert (look in your local yellow pages under "data recovery"). 

They will install the hard drive as a secondary hard drive on another computer system. Then, they will use that to recover the data. If that does not work, because you've reformatted completely, then they can read the magnetic bleeding between the hard drive's tracks with specialized hard disc readers. 

I've watched people do this and it is amazing to watch a "deleted" hard drive's data being recovered.

Or you can try this;

Go into bios and tell the computer to boot from the CD RW instead of the hard drive. Put a Puppy Linux Live CD into the computer. Puppy is designed to run without a HD, with just the CD ROM. The entire operating system and aps are designed to fit into just 100 MB of RAM. The whole thing runs in RAM. If it is a DVD RW, then use a DVD. It doesn't have to be a RW disc. It can be a regular DVD. Just be sure to burn the Puppy Live DVD without "ending" or "finalizing" it so that you could append additional data onto the DVD. Then, treat the primary hard drive like a secondary hard drive and try to read data from it to recover it. I don't know if this would work, but it's worth a try before you dump megabucks on a data recovery expert. Besides, this method is nondestructive while some of the other posters are asking you to install stuff on your computer that could overwrite your existing data. Even just turning on your computer under any operating system other than Puppy could delete valuable data because of the use of swap memory. Since Puppy works in RAM totally, you will not damage your hard drive's data. 

Let me know how this goes.

P.S. burn your Puppy Linux disc and download it with a different computer because further use of your damaged computer would damage it even more.

---

### Post by Gavinthechop on 2009-08-14
Thanks  but that sounds way complicated. The sad thing is that after using photorec, it says that 351 jpeg files have been saved to /home/ubuntu/recup_dir. I just have so little understanding of Linux that I can't find this path. I have tried from the desktop and from terminal but nothing. WTH? I should've bought a how to book before even thinking about this - obviously besides doing the intellegent thing and backing up. Anyway, it's been a learning experience and I have noted how much quicker my setup is and I'm looking forward to when this initial setback is over and I can settle into learning it slowly!

---

### Post by SuaSwe on 2009-08-14
If all you want to do is access the folder, it's simple. :)

In Terminal, type:

> cd /home/ubuntu/recup_dir

... and press Enter. You will now be in that folder. 

To see what files are there (including hidden ones), type:

> ls -la

... and again press Enter.

I agree with some of the other posters though, that anything you do here could damage the files further. (These particular "commands" shouldn't as it's just browsing, but Ubuntu can be a daunting and tricksy place if you're not well-versed!)

---

### Post by tomasrey88 on 2009-08-14
Relax. You might be surprised to find that what I described to you is easy. I only started using Linux 2 weeks ago and I only started using Puppy 2 days ago. They are really user friendly Linux distributions (that's why I use them). I am NOT an IT professional, either. Just do it.

In Puppy, click on the little data disc shape on the lower left corner of your screen, then click on /home, then click on /ubuntu, then click on /recup_dir . Then, copy and paste all your files into a CD or DVD or USB flash memory (preferred). Voila! You're done. 

:-)

P.S. This Ubuntu thing only works if you "pay it forward" by checking in periodically and answering other people's questions. I suggest that you answer a question for every question you ask. If everyone only ask questions, nobody will ever have anything answered, right? Have fun!

:-)

P.P.S. Please answer my questions;

How to use kdc2tiff?
[http://ubuntuforums.org/showthread.php?t=1239893](http://ubuntuforums.org/showthread.php?t=1239893)

Any shockwave flash editors for Ubuntu Linux?
[http://ubuntuforums.org/showthread.php?t=1239991](http://ubuntuforums.org/showthread.php?t=1239991)

---

### Post by scottuss on 2009-08-14
Shut it down and take it to someone who knows what they're doing. Sure you could do it yourself, but you got yourself into this mess, it's time to pay someone to get you out of it!

Seriously though, the more you mess about with the machine the higher the chance you lose stuff.

I wouldn't risk it if the pictures are really that important to you...

---

### Post by Grenage on 2009-08-14
If I wasn't competent with linux, I'd probably plug it into a computer with XP, and run a program called "get data back for ntfs". It's one of the best recovery programs going for windows, and it's very easy to use; It's also quite cheap.

As already iterated here, don't bother proceeding unless you're confident that you have enough knowledge to not make it worse.  Not if the data is that important.  'Most' of your files may well be retrievable.

That said; for the love of God, make backups in future!

---

### Post by LewRockwell on 2009-08-14
It should be pointed out that the OP initiating this trouble-call might not have the available resources to compensate a professional for this task.

Five years ago a friend had his laptop hard drive platter motor fry and the "professionals" billed him over $300.00 for putting the platters in their recovery equipment and harvesting the data.

That being said, if the OP was close enough geographically, I would be happy to recover any data that survived.

.

---

### Post by Gavinthechop on 2009-08-14
Yup, tried that but there is apparently no such folder!? I really don't understand how it says it copied files to a folder that isn't there - weird!

---

### Post by LewRockwell on 2009-08-14
> **Gavinthechop said:**
> Thanks  but that sounds way complicated. The sad thing is that after using photorec, it says that 351 jpeg files have been saved to /home/ubuntu/recup_dir. I just have so little understanding of Linux that I can't find this path. I have tried from the desktop and from terminal but nothing. WTH? I should've bought a how to book before even thinking about this - obviously besides doing the intellegent thing and backing up. Anyway, it's been a learning experience and I have noted how much quicker my setup is and I'm looking forward to when this initial setback is over and I can settle into learning it slowly!

please describe, in detail, how you've proceeded with your recovery

.

---

### Post by 4Orbs on 2009-08-14
You might be looking in the wrong place. The /home folder is not the same as your personal home folder. Go to Places->Computer->Filesystem->home and you should find it.

---

### Post by Gavinthechop on 2009-08-14
4Orbs - thanks for the input, seems that is one thing i got right - not there!
 
LewRockwell - thanks again for your help. I started by eventually getting photorec going and followed the procedures laid out on their site. Only searched for jpeg files. At the end of the search "351 files saved to /home/ubuntu/recup_dir" appeared. I cannot see this folder in Ubuntu, Puppy or through trying to change to it via terminal. There is only one directory off /home/ and it is not ubuntu. WTH?! Good thing is that my wife now knows and it seems my precedent of screwing up has stood me in good stead - seems she half expected it!:)

---

### Post by QIII on 2009-08-14
Might try Search under Places for "recup", but it seems odd you can't find it by looking at your file system.  It's not a "dot" folder, so it shouldn't be hidden.

---

### Post by QIII on 2009-08-14
> **LewRockwell said:**
> you lucked out...

use a flashlight next time!

.

Oh, it's really worse...

I should have noticed the black on white labels I put on my drives for just that reason.

And I should have paid attention at the partitioning portion of the install.

I blame it all on the bifocals and the carelessness of familiarity.

---

### Post by LewRockwell on 2009-08-14
> **Gavinthechop said:**
> LewRockwell - thanks again for your help. I started by eventually getting photorec going and followed the procedures laid out on their site. Only searched for jpeg files. At the end of the search "351 files saved to /home/ubuntu/recup_dir" appeared. I cannot see this folder in Ubuntu, Puppy or through trying to change to it via terminal. There is only one directory off /home/ and it is not ubuntu. WTH?! Good thing is that my wife now knows and it seems my precedent of screwing up has stood me in good stead - seems she half expected it!:)

How are you running photorec?

Since we've already requested that the drive not be mounted to prevent further damage, we will assume that you're using a LiveCD of some sort and hopefully it isn't mounting the swap partition that ubuntu created during installation

You report that photorec "saved" some files but my guess is that their usage of the word "saved" might have meant "rescued" or "discovered" and not actually "saved" as in "written to some form of media"(if that makes sense)

So...say if you've downloaded the latest Parted Magic LiveCD and you're using that for photorec then you'll need to advise that...

Or...if you're using the Ubuntu Rescue Remix ([http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)) then you'd advise as such...

Hope that makes more sense and that these files can be located and securely transfered to appropriate media for safe storage

keep us posted!

.

---

### Post by mc4man on 2009-08-14
@Gavinthechop
I don't know if you've succedded, given up or want to try again.

Anyway...
A few things from your last post seem confusing

> At the end of the search "351 files saved to /home/ubuntu/recup_dir" appeared. I cannot see this folder in [COLOR="Blue"]Ubuntu, Puppy [/COLOR]or through trying to change to it via terminal. [/COLOR].


If photorec was defaulting to save in /home/ubuntu then that suggests you were booted to a ubuntu live cd.
When you boot to a ubuntu live cd there is a login box, if you ignore and just press enter then you're logged in as ubuntu@ubuntu with a home folder named ubuntu.
Your terminal prompt would look like this
> ubuntu@ubuntu:~$ 

Is this what you did?

Where does puppy linux fit in, if you booted to puppy linux where did photorec default to saving to?

> There is only ]one directory off /home/ and it is not ubuntu



That's another confusing part, unless you were on the puppy livecd, or where looking at your ubuntu install where it would be /home/<the user name you choose when you installed it>

In any event I wouldn't save to the live cd (ram) and certainly if you didn't have enough free space. (ram, ie, memory)

If you connect an external drive or or usb drive **before** starting photorec then it will detect it and allow you to save there.
(( using the arrow keys. it's not intuitive, but you'll get the idea - 2 clicks on left arrow take you to /. then down to media. right arrow to your drive (screen3

Doing as you **seemed** to do is shown in screens 1, 2, though I had enough space
(( booted to live jaunty cd, pressed enter, (no login name), dl and extracted photorec to desktop.
ran this in terminal, ect.
> [COLOR="Blue"]ubuntu@ubuntu:~$[/COLOR] sudo ~/Desktop/testdisk-6.11.3/linux/photorec_static

So if you try again I'd do as above but save to an external device

---

### Post by LewRockwell on 2009-08-14
> **QIII said:**
> Oh, it's really worse...

I should have noticed the black on white labels I put on my drives for just that reason.

And I should have paid attention at the partitioning portion of the install.

I blame it all on the bifocals and the carelessness of familiarity.

[http://www.gizmosforgeeks.com/2009/02/11/led-lighted-reading-glasses/4054](http://www.gizmosforgeeks.com/2009/02/11/led-lighted-reading-glasses/4054)

---

### Post by Gavinthechop on 2009-08-15
Hi everyone. Thanks for not losing interest, I certainly haven't as I really do not want to lose these photos - we really delight in showing them to our children and remembering. I have planned to go through to a professional tomorrow - to find the files that is! :)
 
LewRockwell: I used the Ubuntu Rescue Remix cd. Off the boot I ran photorec. After the "351 files saved to /home/ubuntu/recup_dir" displayed, I quit photorec and got the terminal prompt [EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$ [/EMAIL]. I rebooted from there and attempted to locate the /home/ubuntu/recup_dir from PLACES from the Ubuntu desktop - no luck. I assumed that I was missing something and took someone's advice to try through Puppy - same outcome. I had a USB drive in the whole time, but I could not see any option to save anything to it.
 
Gavin

---

### Post by mc4man on 2009-08-15
> have planned to go through to a professional tomorrow That sounds like your best bet at this point

So you know where you were going wrong...

When you boot to a live cd everything is stored in your ram memory vs the harddrive, as soon as you restart it's gone.

So the first time, from the ubuntu Rescue Remix cd, you would have found the files in places -> home on the live cd install itself, not on your hdd

---

### Post by arjuntank on 2009-08-15
thats right. u had all those 351 images on RAM. you restarted after photo-rec told you that 351 recovered. you could have copied the files to usb from there. you could have used usb-drive and booted puppy through it. that way it would have stored on the drive.

there are still chances of getting it again, but its better off you give it to some professionals.

---

### Post by Gavinthechop on 2009-08-15
Ok, that makes sense. I have done run photorec since and it still finds the 351 files. Once it has done so, how would I copy them to the USB drive?

---

### Post by occams_beard on 2009-08-15
If you are going to take it to a pro, you **really** should stop messing with the computer.  Just turn it off, don't touch it.

---

### Post by Arand on 2009-08-15
If you are going to do this recovery by yourself: ONLY BOOT THE SYSTEM WITH LIVECDs, anything else is very likely destructive to your lost data.

So, if, and only if you intend to do it yourself: After you've run photorec you should REAMAIN in the livecd environment, and use either the file manager (nautilus) or the terminal to go to the directory specified, then insert a usb or other form of storage in the system, and just copy the files over.

Whatever way you choose to solve this I hope you get it back ok.
- Arand

---

### Post by Gavinthechop on 2009-08-15
I am going to take it to someone who knows what he is doing but I would really like to understand what is going on. Seems that my problem with using photorec is how to select where to save the files to. I didn't see any drives listed. Any input?

---

### Post by jrothwell97 on 2009-08-15
> **Gavinthechop said:**
> I am going to take it to someone who knows what he is doing but I would really like to understand what is going on. Seems that my problem with using photorec is how to select where to save the files to. I didn't see any drives listed. Any input?

> **occams_beard said:**
> If you are going to take it to a pro, you **really** should stop messing with the computer.  Just turn it off, don't touch it.

'nuff said.

---

### Post by Gavinthechop on 2009-08-15
Thanks mate, you're a gem!:sad:

---

### Post by LewRockwell on 2009-08-15
> **Gavinthechop said:**
> I am going to take it to someone who knows what he is doing but I would really like to understand what is going on. Seems that my problem with using photorec is how to select where to save the files to. I didn't see any drives listed. Any input?

well...

if you've still got it powered up and you still know where the photos are...

you might as well save hundreds of dollars and just put them on some sort of media(CD, DVD, flash drive, hard drive, memory card, etc)

all in all, regardless of the outcome...a very good learning experience for everyone

.

---

### Post by mc4man on 2009-08-15
I somewhat described on my post before how select an external drive using the arrow keys.
Note the external/usb drive  has to be  mounted **before starting** photorec

If it saved to /home/ubuntu then just click on Places -> Home Folder while still on/using the live cd. (( or open the home folder first, you'll see the folder(s) being created by photorec.

A proper, full step by with pictures

[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by Gavinthechop on 2009-08-16
Thanks mc4man that link solved my issues!:P I now have all the photos back - it's a pity that the videos didn't get restored though. Only the thumbnails of the videos show!? 
 
Anyway, thanks everyone for the help. I was running Ubuntu Rescue Remix for the first couple of tries and I was not getting the option under /media to save the files to a USB/External HDD. Once I followed the advice given by the link mc4man shared and ran photorec through terminal from Ubuntu Live, the options were there. Happy days!
 
Now it is just sorting through all the crap! I can't believe the amount of residual info stored on a formatted drive. Every avatar from every forum I've ever visited and every picture from every catalog is still there! Crazy stuff! The bloke that wrote photorec is a genius! 
 
Cheers

---

### Post by misterspiffy on 2009-08-16
> **SuaSwe said:**
> If all you want to do is access the folder, it's simple. :)

In Terminal, type:



... and press Enter. You will now be in that folder. 

To see what files are there (including hidden ones), type:



... and again press Enter.

I agree with some of the other posters though, that anything you do here could damage the files further. (These particular "commands" shouldn't as it's just browsing, but Ubuntu can be a daunting and tricksy place if you're not well-versed!)

Newb here...what is the terminal?  Is it available right in Ubuntu when it's loaded up?  Thanks.

---

### Post by jrothwell97 on 2009-08-16
Applications/Accessories/Terminal.

---

### Post by Shig on 2009-08-16
Photorec should be able to grab videos too:
[http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

---

### Post by Gavinthechop on 2009-08-16
Yeah, I am sure it can - I must just try some more. Like I said, it is astounding at how much junk is still on the hd after a format. At the moment, all I can see are the thumbnails (?) but if I select them nothiing plays.
 
Sorry, my lost post may not have been clear. I couldn't find the USB/External HD when running photorec from Ubuntu Rescue Remix LIVE.

---

### Post by Old_Grey_Wolf on 2009-08-16
> **Gavinthechop said:**
> Like I said, it is astounding at how much junk is still on the hd after a format. 

:)

I thought I was security aware when I was using Microsoft Windows exclusively. I had firewall, anti-virus, anti-malware, etc., software installed. I also kept up with patches and updates for the OS and anti-whatever. I had separate admin and user accounts with strong passwords. I believed I was protected. Then, I booted my first Live CD, and discovered I was not secure at all. I could read everything. I was shocked. It was not only "astounding" but scary to learn what I didn't know about computer security.

**Anyway, I hope you continue to have success with your data recovery.**

---

### Post by bodhi.zazen on 2009-08-17
> **Old_Gray_Wolf said:**
> :)

I thought I was security aware when I was using Microsoft Windows exclusively. I had firewall, anti-virus, anti-malware, etc., software installed. I also kept up with patches and updates for the OS and anti-whatever. I had separate admin and user accounts with strong passwords. I believed I was protected. Then, I booted my first Live CD, and discovered I was not secure at all. I could read everything. I was shocked. It was not only "astounding" but scary to learn what I didn't know about computer security.

**Anyway, I hope you continue to have success with your data recovery.**

I think everybody is shocked when they realize how vulnerable they are if a cracker has physical access.

---

