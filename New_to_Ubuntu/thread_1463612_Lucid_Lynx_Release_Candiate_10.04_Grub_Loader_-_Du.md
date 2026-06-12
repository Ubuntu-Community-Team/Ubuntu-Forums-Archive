---
title: "Lucid Lynx Release Candiate 10.04 Grub Loader - Dual boot bug?"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by EllyBilateralCI on 2010-04-27
Hi,

On my kids PC, there is a dual boot system of Windows XP Professional and Ubuntu. 

I upgraded Karmic with "update-manager -d" to upgrade to Lucid Lynx Release Candidate 10.04....all went ok until when I re-booted the PC, grub menu and selected Ubuntu and it came up with the purple screen with red dots flashing by and at the same time, on the bottom of the screen, that it said....

"The disk drive for /media/sda1 is not ready or not present"

Continue to wait; S to skip mount, M for manual 

I thought ah oh perhaps it didn't install properly from the upgrade method so I installed it again via disc with the Release Candidate installation again.

Now....again it is the same thing...."The disk drive for /media.....etc"

What on earth do I do to solve it?  Is it a bug?  Do I report it?  Is there a workaround?  I'm totally stuck....I've googled and googled and spent hours trying to find a solution...I'm concerned because of (a) the Release Candidate doesn't look stable and (b) that it'll have screwed up the Windows XP Professional.   Having said about the Win XP Pro that when I installed Release Candidate via disc that it could see the User Accounts details and asked me would I like to have it transferred so am hoping it is not completely lost.   But then with the grub loader I couldn't access Windows XP Pro as it came up with a blank (black) screen with the white cursor flashing at the top left hand side of the screen....

Please can somebody help me.....I'm biting my fingernails! :confused:

It is much appreciated and I await with abated breath......

---

### Post by empty_spaces on 2010-04-27
Couple of things.
1) Before things get any worse, run the livecd and copy all your important data to an external drive.

2) You said you installed it again. So did you do a clean install of lucid with a format over the failed karmic upgrade? Or did you skip the partition format?

---

### Post by EllyBilateralCI on 2010-04-27
> **empty_spaces said:**
> Couple of things.
1) Before things get any worse, run the livecd and copy all your important data to an external drive.

2) You said you installed it again. So did you do a clean install of lucid with a format over the failed karmic upgrade? Or did you skip the partition format?
Hi empty_spaces!

Thank you for helping me ....

1)  forgive me for being thick but what is a "live cd"?  I assume you mean the Release Candidate that I downloaded for the PC?

2) I had assumed the re-installation of the lucid would write over the partition of the karmic.  You see whilst I re-installed it that it came up with a graphical picture of the partitions, it had a drop down list of two different partitions,  I clicked on the first item of the partition drop down list and it has its own full partition of (40Gb) and it's Win XP Pro and the other item on the drop down list is the second partition (40Gb) for Linux (Ubuntu).  So I selected the second partition for the Linux and ticked the checkbox of it to erase the whole of the Linux.  

That is why I'm baffled about this blooming bootup!!  I'm scratching my head.   I'm pretty sure it is something simple to fix - is it related to the grub list being all screwed up  in trying to detect it OR is it the Lucid Lynx having a memory leak and therefore stops everything working properly?

Please say you have an answer.....I am praying very hard!

---

### Post by empty_spaces on 2010-04-27
> 
1)  forgive me for being thick but what is a "live cd"?  I assume you mean the Release Candidate that I downloaded for the PC? 

Yes, is is called a livecd because it lets you run and test ubuntu from the cd without having to install it on the hard drive.

> 
2) I had assumed the re-installation of the lucid would write over the partition of the karmic.  You see whilst I re-installed it that it came up with a graphical picture of the partitions, it had a drop down list of two different partitions,  I clicked on the first item of the partition drop down list and it has its own full partition of (40Gb) and it's Win XP Pro and the other item on the drop down list is the second partition (40Gb) for Linux (Ubuntu).  So I selected the second partition for the Linux and ticked the checkbox of it to erase the whole of the Linux.  

That is why I'm baffled about this blooming bootup!!  I'm scratching my head.   I'm pretty sure it is something simple to fix - is it related to the grub list being all screwed up  in trying to detect it OR is it the Lucid Lynx having a memory leak and therefore stops everything working properly?


Please remember that you are trying to install an RC which is not quite the full finished product yet. It is possible that is why you may be seeing this error. I'm seeing a few other threads in the forum about people not being able to boot into lucid.

Other possibilities are either a bad download, or a bad cd burn.

If you can, please wait a couple of days and try installing with the final release cd.

---

### Post by EllyBilateralCI on 2010-04-27
Gosh that is worrying about the lucid affecting a lot of people....do hope the final release gets to work 100% better than I've been experiencing with Release Candidate....it's been a big learning curve all these different upgrades - I've learnt now not to upgrade to the final final piece de resistant!

I'll let you know either way how it goes....I'll wait for a few days and see what happens with the final version in a couple of days time.....gulp!

---

### Post by empty_spaces on 2010-04-27
Here are some ongoing threads that might give you some clues.

[http://ubuntuforums.org/showthread.php?t=1461157](http://ubuntuforums.org/showthread.php?t=1461157)
[http://ubuntuforums.org/showthread.php?t=1463159](http://ubuntuforums.org/showthread.php?t=1463159)
[http://ubuntuforums.org/showthread.php?t=1459153](http://ubuntuforums.org/showthread.php?t=1459153)

---

### Post by EllyBilateralCI on 2010-04-27
Thanks for looking up those links - it's really helped me and 


Ok I went back and re-installed Ubuntu Beta2 32 bit version.

The grub didn't load and had "grub rescue>"  I panicked!

I investigated and went to [https://help.ubuntu.com/community/Grub2#Resolving%20an%20%22Unrecognized%20Device%20String%22%20%28Error%2011%29](https://help.ubuntu.com/community/Grub2#Resolving%20an%20%22Unrecognized%20Device%20String%22%20%28Error%2011%29) and went to the section of SIMPLEST - Copy GRUB 2 Files from the LiveCD.

With the LiveCD, I selected Try Ubuntu 10.04....and wait for it to be in "Ubuntu mode", and then from there follow the instructions of the SIMPLEST.....method.

It worked - I got my grub back and Ubuntu opened up ok as normal.:P

So I'm going to wait for the Release and see what happens.

---

### Post by empty_spaces on 2010-04-27
Good to know that it was just a grub issue and your pc is up and running again.
Although I've been testing the lucid betas, I'm going to wait until the 29th and do a fresh install with the final release.

---

