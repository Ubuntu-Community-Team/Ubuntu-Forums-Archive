---
title: "Urgent! Please help - have to install win xp for college and problems installing"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-09-03
So I have some online courses from my university; and, I thought I could slide by somehow without installing Windows. I was painfully, painfully wrong.  :cry:  They just find a way to force you to use windows.  ](*,)  One, urgent thing is that I have to install this lockdown browser in order to take the exams in one of my classes and it only works with windows or mac (of course). First, on this machine, my laptop, I looked into installing it with Wine (I have Wine) - fat chance. Then I installed windows as a vm in virtual box then installed the lockdown browser they need me to have, but it knows its in a vm and won't run (gives you a message window about it too). Wasted I don't know how many hrs finding that out. So now, my only remaining recourse, is to install it on my other machine - my desktop - the one I had OTHER plans for. Yeah, that one.

So here's my problem. I have 3 drives on that desktop two the same size and one with almost 20 GB more. I figured I could partition off the lowest common denominator across all three then partition the left over space on the one that's slightly larger and install windows to that left over space on the one disk. The partition scheme goes like this:

Sda = 76318 MiB (ext4)
sdb = 76318 MiB (ext4)
sdc1 = 76318 MiB (ext4)
sdc2 = 19076 (ntfs)

With one MiB before the larger partition on each disk and one MiB before sdc2 (or, in between sdc1 and sdc2).

I shut down the machine and removed the gparted live cd, inserted my windows xp pro oem disk and fired it back up. After a couple screens you get to the part where you select a partition to install to. Of course windows doesn't recognize the ext4 partitions, which is fine - but it sees the ntfs (ohh it likes that one). So, being where I want it to go anyhow, I select that ntfs partition (sdc2 to Linux) and press enter. Now I get a message from the windows installation that it need to install some setup files to the other partition on that drive, and it names the one its after (evil), in order to do the install. It tells me it doesn't recognize the type of partition and that I need to make one of a couple radical changes (via reformatting) to my system before it can go on.

So this is something I just can't do. I'll be darned if I'm not going to use that space for Xen. Windoze isn't getting that from me! I was really hoping someone knew of a solution to my problem. Some way I can just contain this, this . . . grrr  to that one small partition from start to finish. Do I need to split that one partition and make a little slice in there for it to use for its "setup files"? If that would work, I'm not sure how big it should be. Maybe 1 GB? I don't want to guess. Or is there a better way?

Any help would really, really be appreciated. My first exam in this, particular class, is due in less than two days. I'll miss the exam if I can't get widows installed and get that dumb lock down browser on there.

Thanks in advance for your help.

---

### Post by Wim Sturkenboom on 2011-09-03
Simplest way, if the system is 'fresh', is to partition sda; give it 20GB for windows (sda1). It will (sorry, should) install without complaining ;)

Good luck with the exam.

---

### Post by ClientAlive on 2011-09-03
Thanks for wishing me luck. The problem is that computer's purpose is not for windows to just be installed on it. I've spent a lot of time and effort and agony resurrecting that thing for a very specific purpose that has nothing to do with windows. Now, due to circumstances, I'm forced to put windows on there. I'm trying to do it in a way that still allows me to use the machine for my original intentions as well - desperately so. The only place for windows to go that would allow that is sdc2. Isn't there some way to make it install there?

---

### Post by jzjavez on 2011-09-03
i want to install a parallel operating system along with the ubuntu which i am using at present

---

### Post by Gone fishing on 2011-09-03
As you don't really wont Windows, but need it. How about installing VirtualBox then install Windows in a virtual machine? Windows will be able to use network etc but you will also have Ubuntu available at the same time you could even have windows on one virtual desktop and use Ubuntu on another.

If you want to dual boot probably the easiest way way would be to unplug the sdb, and sdc drives - backup any important stuff on the sda drive (/home?). Then reinstall Windows letting it have about 1/3 of the drive. Reinstall Ubuntu and then the system will dual boot copy over your important stuff and then replug in the other drives.

However, I'd consider the VirtualBox solution if you have a reasonably modern Box with 2 or more Gig of RAM

---

### Post by Swagman on 2011-09-03
I think you'll find that windows **HAS** to be on the first partition of the drive. ie: At the beginning.

Best thing I would do is to connect an old drive and install on that then sudo update grub or when you want to boot into windows just alter boot order in bios

---

### Post by westie457 on 2011-09-03
Bearing in mind that you are going to have to restore Grub afterwards.

Have you tried giving Windows 2 partitions. SDC2 as the Windows boot partition (100MB) and SDC3 for the install. Try them as unformatted and allow Windows installer to format them.

---

### Post by Gone fishing on 2011-09-03
Windows does need to be on the first primary partition such as sda1

---

### Post by lmarmisa on 2011-09-03
> **Gone fishing said:**
> As you don't really wont Windows, but need it. How about installing VirtualBox then install Windows in a virtual machine? Windows will be able to use network etc but you will also have Ubuntu available at the same time you could even have windows on one virtual desktop and use Ubuntu on another.

If you want to dual boot probably the easiest way way would be to unplug the sdb, and sdc drives - backup any important stuff on the sda drive (/home?). Then reinstall Windows letting it have about 1/3 of the drive. Reinstall Ubuntu and then the system will dual boot copy over your important stuff and then replug in the other drives.

However, I'd consider the VirtualBox solution if you have a reasonably modern Box with 2 or more Gig of RAM

+1 for VirtualBox.

---

### Post by overdrank on 2011-09-03
> **ClientAlive said:**
>  Then I installed windows as a vm in virtual box then installed the lockdown browser they need me to have, but it knows its **in a vm and won't run** (gives you a message window about it too). Wasted I don't know how many hrs finding that out. So now, my only remaining recourse, is to install it on my other machine - my desktop - the one I had OTHER plans for. Yeah, that one.


> **Gone fishing said:**
> 

However, I'd consider the VirtualBox solution if you have a reasonably modern Box with 2 or more Gig of RAM

> **lmarmisa said:**
> +1 for VirtualBox.
As the op has pointed out it does not work with Virtual Box :)

---

### Post by westie457 on 2011-09-03
Sudden brainwave..... Convert the current EXT4 primary partition into an extended partition. Then Windows will install to the only primary partition.

Take a look at this [old thread]("http://ubuntuforums.org/showthread.php?t=1032234").

It might just work.

---

### Post by scruffyeagle on 2011-09-03
I agree with the people who've told you that Windows is going to demand the root partition. I'd even extend that, to saying I'd expect for it to demand the root partition on the 1st drive. Linux is much more forgiving, but Windows has always been limited in its setup options. If you're using Linux w/ grup, why not yield that root boot slot? I have a box w/ XP HE SP3 & .NET on it, and after many years of collecting & installing freeware, the system partition still weighs in at less than 26 MB total data. I don't have experience w/ XP Pro, but I'd be quite surprised if 30 MB wouldn't be sufficient forever for the system & programs (only).

I understand that you had plans for that box - but, you also had plans to succeed in college, right? You're going to need to weigh your options, and decide what's most important. Your plans for that old box can probably be revised, as long as you haven't irretrievably lost data during setup conversions. You've written that you're short on time, and there's a big test hanging in the balance. I'd advise you to yield that root partition, get Windows installed & its setup finished, and then reformulate your side project after it's done.

---

### Post by waynefoutz on 2011-09-03
I would install Windows as the only and primary OS, let it take the whole drive, which is what it wants to do, then install the other OS(s) afterwards. Anything else is going to be a wrestling match.

---

### Post by restorator on 2011-09-03
Can you grab another cheap hard drive and throw it in the computer alongside the existing one, unplug the existing one, then install windows to the new one, take your exams and then just unplug the windows one and plug the other back in, swapping the plugs as necessary? A last resort yes, but a clean and easy solution.

---

### Post by Gone fishing on 2011-09-04
Sorry I missed the VirtualBox comment - but I'm wondering why? Did you use NAT or Bridged networking? I wonder if the locked down browser is detecting you are using the wrong IP range i.e using the NAT or used ports are inaccessible through the NAT and this wont be an issue with bridged networking.

---

### Post by ClientAlive on 2011-09-04
Hi guys,

Sorry for going mia or a while there. I've been just swamped with schoolwork and all the other stuff.


> **Gone fishing said:**
> 
If you want to dual boot probably the easiest way way would be to unplug the sdb, and sdc drives - backup any important stuff on the sda drive (/home?). Then reinstall Windows letting it have about 1/3 of the drive. Reinstall Ubuntu and then the system will dual boot copy over your important stuff and then replug in the other drives.

However, I'd consider the VirtualBox solution if you have a reasonably modern Box with 2 or more Gig of RAM

Won't work w/ VB I tried. The breaking point that makes me have to have WindoZ is that I have to install something called Lockdown browser to take my online course tests with. It's designed not to allow you to run it in a virtual machine or sandbox. I had to learn that the hard way.

I had initially thought, in consideration of the RAID 5 I'd like to run across those disks for my primary project, that having the drives set up:

sda = 75 GB (partitioned at 75 GB w/ 1 Mb at the beginning)
sdb = 75 GB (partitioned at 75 GB w/ 1 Mb at the beginning)
sdc = 100 GB (partitioned as sdc1 = 75 GB w/ 1 Mb at the beginning + sdc2 = 25 GB w/ 1 Mb at the beginning)

was the only logical way to go. I suppose though, that:

sda = 100 GB (partitioned as sda1 = 75 GB w/ 1 Mb at the beginning + sda2 = 25 GB w/ 1 Mb at the beginning)
sdb = 75 GB (partitioned at 75 GB w/ 1 Mb at the beginning)
sdc = 75 GB (partitioned at 75 GB w/ 1 Mb at the beginning)

Would probably work better and wouldn't be a problem for my other project.


> **restorator said:**
> Can you grab another cheap hard drive and throw it in the computer alongside the existing one, unplug the existing one, then install windows to the new one, take your exams and then just unplug the windows one and plug the other back in, swapping the plugs as necessary? A last resort yes, but a clean and easy solution.


Absolutely, that is exactly what I ended up having to do, but I do consider it a 'temporary' solution. (I'll explain in a min here). So I had an extra 20 GB drive sitting there and I just plugged it into the mobo in place of what was sda, installed windoZ to it and the other program I needed and I'm golden. Got my test taken care of and everything. Thanks.


> **Gone fishing said:**
> Sorry I missed the VirtualBox comment - but I'm wondering why? Did you use NAT or Bridged networking? I wonder if the locked down browser is detecting you are using the wrong IP range i.e using the NAT or used ports are inaccessible through the NAT and this wont be an issue with bridged networking.

Way, way, over my head. Don't know what you're talking about. One day, if I keep going the way I'm headed, I'm sure I will but as for now it's not something I'm capable of. (If there's any point at which I actually sound like I know what I'm doing I probably learned about it, like, yesterday  :)  (this Linux user = about 6 mos at this point).
------------------------------

> **scruffyeagle said:**
> 
Your plans for that old box can probably be revised, as long as you haven't irretrievably lost data during setup conversions. You've written that you're short on time, and there's a big test hanging in the balance. I'd advise you to yield that root partition, get Windows installed & its setup finished, and then reformulate your side project after it's done.


Firstly, thank you for the wise advice. I am a bit of a hot head (very passionate) and can be a little arrogant at times - I need to be reminded of these things sometimes. What you suggest is a line of thought I started to take with this whole thing (it'll make more sense a little further down, near the end, where I'll explain). There wasn't anything on it by the way, just a bare piece of equipment.

> **scruffyeagle said:**
> . . . I understand that you had plans for that box - but, you also had plans to succeed in college, right? You're going to need to weigh your options, and decide what's most important. Your plans for that old box can probably be revised, as long as you haven't irretrievably lost data during setup conversions. You've written that you're short on time, and there's a big test hanging in the balance. I'd advise you to yield that root partition, get Windows installed & its setup finished, and then reformulate your side project after it's done.

I think this a good opportunity to share a bit about myself and about the situation. I consider you guys my brothers, my family. I share with you like I would with them. If the Linux community doesn't stick together and stand for what's right then who will?

Succeeding in college is not an end in and of itself, it is a means to have continued success in life. In like manner, the particular plans I had for that computer are also a means to those same goals. While I agree there are times a man has to make sacrifices this is not a situation in which a complete sacrifice is permissible (for a lot of reasons I won't go into here now).

I think I should briefly explain more of what's going on here:

That machine was built so I can use it to experiment on and not worry about borking up my daily driver. One of my interests (and with specific, future business plans in that area) is cloud computing and virtualization. Consequently, I had intended to compile Xen on that machine and continue to work from there to create my product (as I learn and grow into it).

I'm a comp sci major and have plans not only to take classes related to those life goals but also to tailor class projects directly to my project whenever possible. (The thing is bigger than Xen really. Xen is just a starting point).

There are many things involved in compiling a system that will ultimately function as a server, one of them is preparing your drives. I'm using old equipment because it's all I could get right now. The drives are old ide drives and there are 3 of them.

The way in which I wish to use those drives (for the Xen system) is to run RAID 5 across them. Two drives are 75 GB (roughly) and the other is 100 GB (roughly). RAID takes the smallest disk and uses it as the common denominator across all of them. That means I would either end up with 25 GB of wasted space on one drive or I need to find something useful and feasible to use that extra space for. Having a windoZ installation on that space just makes sense (though I loath how microsoft conducts business and loath the entire system that has been built up around it, it does make sense, and for a number of reasons).

The one thing that doesn't make sense is to have two of the three drives in a RAID array at partition 1 and a third at partition 2. MDADM might go for it but I'm still going to have to administer that system and I'd like to have things set up in a way that makes sense. Perhaps some combination of bringing that 100 GB drive up into the primary position as sda and what westie457 points out could work. I can try it. Makes more sense for both systems that they be on the primary drive, compile directly to it (for the Xen system) and build my RAID array off sda1 and on down the line.

More than all those things though. Far, far above all that - I am very passionate about individuals having the freedom to use the equipment they work so hard to have in whatever way they wish. In my particular case it has been a real struggle to get that old machine running and up to the point it's at now (resource wise - both the computer's and mine). I'll be damned if I'm going to allow some tyrant, or the tyrany of that group, dictate to me that I 'have-to' use windoZ (all-the-time), and that, to the exclusion of the other projects that are so important to me. Much more than just myself though, I find it very disturbing to think of how many others are being imprisoned daily, or who have been for years, at the mercy of that god awful racquet they've got going on. It's almost surreal!
--------------------------------

> **westie457 said:**
> Sudden brainwave..... Convert the current EXT4 primary partition into an extended partition. Then Windows will install to the only primary partition.

Take a look at this [old thread]("http://ubuntuforums.org/showthread.php?t=1032234").

It might just work.


Now that would be spectacular! Thanks for sharing.

> **scruffyeagle said:**
> I agree with the people who've told you that Windows is going to demand the root partition. I'd even extend that, to saying I'd expect for it to demand the root partition on the 1st drive. Linux is much more forgiving, but Windows has always been limited in its setup options. If you're using Linux w/ grup, why not yield that root boot slot? I have a box w/ XP HE SP3 & .NET on it, and after many years of collecting & installing freeware, the system partition still weighs in at less than 26 MB total data. I don't have experience w/ XP Pro, but I'd be quite surprised if 30 MB wouldn't be sufficient forever for the system & programs (only).



I'm hoping that some combination of the two is going to do the trick for me - I really am. I don't see why it wouldn't, but if not I'm sure I'll find some way to make it work.

Wonder if I can chain boot with grub and force winblows to where I want it?

> **westie457 said:**
> Bearing in mind that you are going to have to restore Grub afterwards.

Have you tried giving Windows 2 partitions. SDC2 as the Windows boot partition (100MB) and SDC3 for the install. Try them as unformatted and allow Windows installer to format them.

I'm not sure what I did is exactly what you're talking about but I did try something like that. At one point (before installing it to that completely other hard drive - my temporary soln) I reformatted that drive thus:

sdc1 = 75 GB (ext4)
sdc2 - 1 GB (ntfs)
sdc3 = 24 GB (ntfs)

I was thinking windoZ might just go after the next higher partition (in that case sdc2). Fat chance! It still went after my sweetheart (sda). I hadn't seen the posts here about windoZ needing to be the king of the mountain. I don't think what I did was exactly as you describe though. Perhaps there is a difference if I leave that partition unformatted.

I do recall seeing some post, I think it may have been here on Ubuntu forums somewhere, where the person was talking about this same problem and the soln that was given was editing some file in windows and make all the numbers one digit higher (so 0 becomes 1 and 1 becomes 2, etc). I don't know where to find it again though and I don't recall enough details to know if it might work for me. I think that whatever file they were talking about editing was the windoZ equivalent to grub (would that be the mbr?). Sure wish I could find that post again. Not ever certain it was here or on some other forum.

---

### Post by ClientAlive on 2011-09-04
@ overdrank: Nice to see you around again. Long time no see.

---

### Post by ClientAlive on 2011-09-06
@ westie457

Thanks for the tip. Worked like a charm. It did take a little tweaking after it was installed though. Apparently, when you use that little trick it sets the partition to

```

. . . partition(1) . . .

```

But I didn't know that until down the road. When I rebooted to check out my new installation and see that it worked right I got the following error message:

```

Windows could non start because the following file is missing or corrupt.

<Windows root>\system32\boot.ini

Please re-install a copy of the above file.

```

I did some googling around and found the following post:

> 
From: Bill on 05/21/2011
 Here is what I found but haven't tried yet - mine crashed after removing the Dell Utility 31MB FAT16 partition (via Linux):

Extracting hal.dll isn't going to fix it anyway and you don't fix it
from the Recovery Console. I'm sure you've seen this, but here is
information from the late MVP Alex Nichol:

That message is rather misleading. It happens because the boot.ini file that tells the boot where to look for 'Windows' is damaged, so it is looking for files in the wrong place - hal.dll just happens to be the first one it looks for. Set the BIOS to boot CD before Hard Disk. Boot the XP CD and, instead of Setup, take the immediate R for Repair. Assume any password requested is blank, and TAB over.

Use
Attrib -H -R -S C:\boot.ini
DEL C:\boot.ini
to delete the bad one
BootCfg /Rebuild

to search for Windows installations and make a new one.

As for not having the correct XP disk, you only need to have one that
matches the installed version - Home/Pro, retail/OEM.


I'm not sure the guys instructions were really that great though because when I tried to run that first line: "Attrib -H -R -S C:\boot.ini" WindoZ complained about a bad parameter and wouldn't take it. So I ran:

```

Attrib -HRS C:\boot.ini

```

and it seemed to like that better because it gave me a new line. Then I ran the three other lines following it from the guy's instructions.

Turns out there are two lines for input that the guy didn't mention that come up at the end of the process before it creates the new boot.ini file for you. Well, long story short I ended up running through that process twice. I didn't know it at the time but each time I ran through that process it was adding another entry to the boot.ini file. In the end I had 3 operating system entries in my boot.ini.

I went in and edited boot.ini by right clicking "My Computer" Click properties > advanced tab > settings

That gives you a window called "startup and recovery" where I clicked the "edit" button and removed the offending entries and changed the partition number to 2 instead of one in the entry I left in there. Rebooted and the thing works like a champ (well, for windoZ anyway).

I have to confess, I didn't really read the post at the link you gave. I just thought about what you said in your post here and it made sense so I went for it. Making the first partition (sda1) an extended partition did trick windoZ into installing to the second partition but it didn't know it was the second partition so it still put partition(1) in boot.ini, I was able to go back and change that extended partition back to primary and ext4 after the install, but ultimately had to do the aformentioned editing.

**In hindsight, I now realize that the problem all along (and the reason I got that error message from windoZ about the missing file) was that the partition number needed to be changed in boot.ini, that's all. All that stuff the guy in that post instructed could have been left out and just go straight for editing boot.ini and I would have been golden even sooner. Doh! This stuff is a learning process though, what can you say.**

Thanks again brother. Thanks everybody. I sure appreciate it.  :popcorn:

---

### Post by scruffyeagle on 2011-09-07
> **ClientAlive said:**
> <snipped>

Thanks again brother. Thanks everybody. I sure appreciate it.  :popcorn:

I'm glad you got it solved, and fairly impressed at the elegance of your solution. Before reading your most recent post, I was ready to write something else:

Basically, that you're still young. Years stretch ahead of you, not counting what's beyond college. A concession now doesn't knock out the chance for success later. "Baby steps" applies. You could find another old machine later, install Windows onto it as per the college's requirements, and then use the current machine for its originally intended project. And, until then, refine your design for the project; flowcharting, calculating, programming, etc.

There's an old saying about success being "1% inspiration and 99% perspiration". I believe the truth is, in design of complex systems, it's the other way around. If you don't think it through, it simply can't succeed. And, once it's properly thought through, the actual work just falls into place.

Congratulations, and good luck!

---

### Post by westie457 on 2011-09-07
Glad you got it working and I hope you did well with the online exams.

Now to explain (or try to) the thinking behind those suggestions.

The one about giving Windows two partitions came about through seeing various screenies and bootinfo scripts showing a small boot/system reserved partition and one big one for the OS. In a lot of those the small one is a primary and the big one is a logical one. In my early days of discovering Ubuntu (8.04) I was always breaking the system - Windows and Ubuntu - equally. In those days I never bothered with the Forum and just got on with experimenting with the partitions and reinstalling. I used to use a SGD Disc to boot the Windows partition and never thought about editing the boot.ini file.

The idea of forcing a rewrite of the partition table was exactly that - a sudden brainwave. A small amount of Googling trying to phrase the question right brought up the link I posted here. I chose that purely because it had that magic word in it -SOLVED. One day I will try it on a spare drive.

---

### Post by ClientAlive on 2011-09-09
> **westie457 said:**
> Glad you got it working and I hope you did well with the online exams.

Now to explain (or try to) the thinking behind those suggestions.

The one about giving Windows two partitions came about through seeing various screenies and bootinfo scripts showing a small boot/system reserved partition and one big one for the OS. In a lot of those the small one is a primary and the big one is a logical one. In my early days of discovering Ubuntu (8.04) I was always breaking the system - Windows and Ubuntu - equally. In those days I never bothered with the Forum and just got on with experimenting with the partitions and reinstalling. I used to use a SGD Disc to boot the Windows partition and never thought about editing the boot.ini file.

The idea of forcing a rewrite of the partition table was exactly that - a sudden brainwave. A small amount of Googling trying to phrase the question right brought up the link I posted here. I chose that purely because it had that magic word in it -SOLVED. One day I will try it on a spare drive.

Worked like a charm. Brilliant!


> **scruffyeagle said:**
> 
There's an old saying about success being "1% inspiration and 99% perspiration". I believe the truth is, in design of complex systems, it's the other way around. If you don't think it through, it simply can't succeed. And, once it's properly thought through, the actual work just falls into place.

Congratulations, and good luck!


Sooo sooo glad to hear someone say that. I was on the Gentoo forums a while back (probably a month ago now) asking some questions about compiling a Gentoo. At the time I didn't even have my hardware functioning (ie: the machine wouldn't even fire up at all), and I wanted to get more memory in it for what I'm trying to do. Based on some of the responses I got, I felt like people were trying to rush me. I knew there were several pretty big issues I would have to face that I didn't know anything about at the time (issues other than just compiling something - like volume management and partioning and the Xen file system and basics of how Xen works).

Some of the folks there wanted me to just jump into it but I didn't (and don't) want to have to re-do the thing half a dozen times before I get the kind of system I'm really after. I know I'll probably make mistakes and will probably have to recompile or do some other thing over before I get it right but I don't want to go into something like this with an empty head. I'm glad I was patient and gathered the information I needed to do it properly. I still have a ways to go but I'm already learning a lot of really huge things because of that decision. Among many other things this project is a guideline and motivation to learn about some pretty major topics. I love it!

Thanks man!

Gonna write my first program in C in the next few days by the way. It's our next assignment for that class. We have to make a program that calculates miles per gallon. I think all the instructor wants is something with fixed values that just does the one calculation on that and gives one answer. I'm tempted to step it up a notch though and try to make something where the user inputs the values and gets the answer spit out based on their input. We'll see what happens!

;)

Peace

---

### Post by scruffyeagle on 2011-09-10
> **ClientAlive said:**
> <snipped>
Gonna write my first program in C in the next few days by the way. It's our next assignment for that class. We have to make a program that calculates miles per gallon. I think all the instructor wants is something with fixed values that just does the one calculation on that and gives one answer. I'm tempted to step it up a notch though and try to make something where the user inputs the values and gets the answer spit out based on their input. We'll see what happens!

;)

Peace

A word of advice: Before you do that, sound out the instructor about it. Some professors appreciate initiative and extra, but some professors are like some drill sargeants. When they tell you to clean the sidewalk, they'll get pissed if you also do the lawn. They expect exactly what was assigned - no more, and no less. So, to avoid unpleasant surprises, find out how your professor feels about this before you actually do it. It might be that you should create 2 versions. One for handing in, that's exactly what was requested, and a second one w/ extra for your enjoyment.

---

### Post by ClientAlive on 2011-09-11
> **scruffyeagle said:**
> A word of advice: Before you do that, sound out the instructor about it. Some professors appreciate initiative and extra, but some professors are like some drill sargeants. When they tell you to clean the sidewalk, they'll get pissed if you also do the lawn. They expect exactly what was assigned - no more, and no less. So, to avoid unpleasant surprises, find out how your professor feels about this before you actually do it. It might be that you should create 2 versions. One for handing in, that's exactly what was requested, and a second one w/ extra for your enjoyment.


Sounds like good advice. Thanks scruffyeagle.

---

### Post by PayPaul on 2011-09-20
To paraphrase what others have said here; you've got time on your hands and yet you don't. I prefer simple. Clean out that hard drive, reformat it, do a clean install of Windoze and use it for your exams. Then you can reformat again and use the machine for all your future plans. 

It seems like sudden death at first look but better than the slow death of time.

---

