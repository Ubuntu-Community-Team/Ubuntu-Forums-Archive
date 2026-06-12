---
title: "Trouble with DVD Drive - possible mouting issue?"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Debra.S on 2010-10-14
I am running 10.10 on a Dell Inspiron 1545 which came preloaded with 9.10.  When I upgraded to 10.04, I started having trouble with my DVD drive (Optiarc AD-7560S).  Sometimes it would not recognize DVD's or would play the video but not audio.  This problem seemed to be limited to Totem, so I switched to VLC and used it without problem.  However, with this latest upgrade, VLC is not working either.  When I insert a CD or DVD, the drive often does not recognize that it is a new one, and will show the previous media that was in the drive.  Sometimes, I can get CD's to play through VLC by chosing the "play media" option, but this does not work with DVD's.  Totem will not even open.  Going into the media folder and refreshing it does not prompt it to recognize the new disk.

In my places menu, it's currently showing both an audio CD (no name on it though) and also CD ROM.  I have only one drive and this also is a new issue.

I've been scouring the forums for a day now, but could not find any similar issues.  I am at a complete loss, and use my laptop to watch movies quite often (one of the reasons I bought it) and can only guess that it could be a mounting issue, but I don't know how to check that.

Additional information - the drive has no problem reading disks with data on them, but is still having the same issue with not recognizing new media.

Where do I start with this?  I'm just learning things in terminal, so if I'm given commands, I can reply back with what I get, but I don't know what much of it means yet.  So far I've really only used terminal for basic opperations.

Thanks.

---

### Post by lhb1142 on 2010-10-14
> **Debra.S said:**
> I am running 10.10 on a Dell Inspiron 1545 which came preloaded with 9.10.  When I upgraded to 10.04, I started having trouble with my DVD drive (Optiarc AD-7560S).  Sometimes it would not recognize DVD's or would play the video but not audio.  This problem seemed to be limited to Totem, so I switched to VLC and used it without problem.  However, with this latest upgrade, VLC is not working either.  When I insert a CD or DVD, the drive often does not recognize that it is a new one, and will show the previous media that was in the drive.  Sometimes, I can get CD's to play through VLC by chosing the "play media" option, but this does not work with DVD's.  Totem will not even open.  Going into the media folder and refreshing it does not prompt it to recognize the new disk.

In my places menu, it's currently showing both an audio CD (no name on it though) and also CD ROM.  I have only one drive and this also is a new issue.

I've been scouring the forums for a day now, but could not find any similar issues.  I am at a complete loss, and use my laptop to watch movies quite often (one of the reasons I bought it) and can only guess that it could be a mounting issue, but I don't know how to check that.

Additional information - the drive has no problem reading disks with data on them, but is still having the same issue with not recognizing new media.

Where do I start with this?  I'm just learning things in terminal, so if I'm given commands, I can reply back with what I get, but I don't know what much of it means yet.  So far I've really only used terminal for basic opperations.

Thanks.

It is possible that your internal drive is corrupted or physically damaged (that happened to one of my computers once upon a time).

Have you tried an external CD/DVD drive? That's what I now use almost exclusively. (If they go bad, they're much cheaper to replace than an internal one.) If you own, or can borrow, one, try using it.

In the VLC Media Player click on Media -> Open Disc. You will see the Disk Device reading /dev/sr0; change that to read /dev/sr1 and (I hope) that the disc will then play.

You would have to do this every time you wished to play a CD or DVD via VLC Media unless you were to change the Default CD/DVD player to VLC (see < [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) > - scroll down to Default DVD Player for instructions).

Good Luck!

Lawrence

---

### Post by John Peschken on 2010-10-14
I have experienced what may be related issues with my DVD drive, an external USB unit.
 
I have not tried a DVD with it, but I noticed that CD's with both audio and data (usually a video) confuse Ubuntu to no end.  It tries to load the two things separately, and fails on the data portion.   Are these DVD's perhaps some kind of mixed content?  Perhaps a DVD and a data file of some kind?
 
Also, I have a CD drive (also external USB) that likes data CD's okay, but can not mount audio CD's under Ubuntu.  
 
In both cases, Windows on the same computer likes this same discs just fine, so it looks like there are some issues with mountng CD's and DVD's in Ubuntu.  My upgrade to 10.10 did not solve the problems.  I started with 10.04, so I have no previous versions to compare to. 
 
None of this helps you really, but I just wanted to chime in and follow the discussion.  Maybe we'll both find a solution.

---

### Post by lhb1142 on 2010-10-14
I should have mentioned that I am running Ubuntu v.10.04 'Lucid Lynx' on my computer. I have had absolutely no problems with my external CD/DVD drive using either VLC (my own personal favorite) or Totem.

I once DID have a problem with that external drive - it was with v.9.04. With that version, I could not mount ANY external CD/DVD drive (I have a couple of them). I wrote on the forums about this problem and I even filed a 'bug' report. But it was never fixed in 9.04. (The internal one worked fine.)

Came version 9.10 and the problem went away and the drives have worked perfectly since (as they did before 9.04).

I shall be upgrading to 10.10 in a week or so (I always wait a bit to make sure that any unforeseen 'bugs' are corrected and also because, when a new version is released, "everyone" is trying to get it at the same time and the servers are overloaded).

I hope that there are no such 'bugs' in 10.10 when I upgrade to it.

But I digress - I have a feeling that it is your internal CD/DVD drive that has gone bad; when mine did a couple of years ago (on a different, now discarded, Windows computer) the internal drive would still read data files and it would play CDs though it would not burn them. It would not play or burn DVDs at all; it refused to recognize that a DVD, either prerecorded or blank, was in the drive. My external drives worked fine.

Lawrence

---

### Post by Debra.S on 2010-10-14
> **lhb1142 said:**
> It is possible that your internal drive is corrupted or physically damaged (that happened to one of my computers once upon a time).


In the VLC Media Player click on Media -> Open Disc. You will see the Disk Device reading /dev/sr0; change that to read /dev/sr1 and (I hope) that the disc will then play.


Lawrence

Yes, the first is a possibility.  I'm trying to absolutely make sure it's not an issue with the os before I repair it though.  My husband suggested just getting an external, but a lot of the reason I got a laptop instead of a desktop is for the convience of easily being in any room with it.  Having to haul around extra equipment takes away some of that convience.

Changing it to read /dev/sr1 caused it to tell me that no such directory existed.  So that's out as an option.  I should add that sometimes, I can get it to start a dvd, but within a few seconds it gets choppy and the audio starts looping back on itself.

At the advice of a friend, I'm downloading 10.04 and going to try running it from a USB and see if my issues are solved then.  If they are, I'll probably have my husband wipe my hard drive and reinstall 10.04 and just stick with that.  If not, I guess I have to assume it's a hardware issue and replace the drive.  Which Dell does not sell replacements for, except for a refurbished toshiba that is supposed to be compatible.  But that's another issue for a another sub-forum.

Thanks.

---

### Post by Debra.S on 2010-10-14
The boot menu did not offer an option for booting from the USB, and after talking to my husband, I went with a fresh install from factory settings.

My optical drive is working fine now.  It's going to be a pain to get everything upgraded and configured correctly again, but at least I don't have to mess with trying to find all the drivers like I would with a completely fresh install.

I haven't seen anyone else having this issue with 10.10, nor 10.04, which is when the problem started, so I don't know what to think.  For now, I'm going to stick with 10.04 and see if I start to run into the issue again.

Thanks.

---

### Post by lhb1142 on 2010-10-15
> **Debra.S said:**
> The boot menu did not offer an option for booting from the USB, and after talking to my husband, I went with a fresh install from factory settings.

My optical drive is working fine now.  It's going to be a pain to get everything upgraded and configured correctly again, but at least I don't have to mess with trying to find all the drivers like I would with a completely fresh install.

I haven't seen anyone else having this issue with 10.10, nor 10.04, which is when the problem started, so I don't know what to think.  For now, I'm going to stick with 10.04 and see if I start to run into the issue again.

Thanks.

I have always found that, when encountering some 'insoluble' problem, the easiest and quickest thing to do is to effect a complete reinstall of Ubuntu. As long as you have backed up all your documents, music, pictures, and videos to an external hard drive, and you can either remember or can write down what you had installed (so you can reconfigure the computer the way you like it), reinstalling Ubuntu is straightforward and takes only a couple of easy hours.

I may make a suggestion to you (and to anyone else reading this who has had a problem with CD/DVD drives):

Go into Places -> [Your Home Folder]* -> Edit -> Preferences -> File Management Preferences - > Media. Change EVERY OPTION (both under "Media Handling" as well as the various options under "Other Media") to "Do Nothing" except for "Software" in the Media Handling section; leave that set to "Open Autorun Prompt." Uncheck "Never prompt or start programs on media insertion" but do check "Browse media when inserted."

Setting up the computer in that fashion prevents it from trying to do two things at one time (if you have also tried to open a program, such as playing a CD or DVD). In other words, the computer will Do Nothing on its own; it will obey only YOUR particular command.

*Actually you can make these changes from within any folder.

I hope the above information is of some use to you.

Lawrence

---

