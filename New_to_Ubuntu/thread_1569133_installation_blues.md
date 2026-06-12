---
title: "installation blues"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by pirooz on 2010-09-06
I  have an old toshiba TA2000, intel centrino, with 1 meg of memory. It runs its original version of windows xp just fine, but one the several service packs and updates are added it slows to a crawl. 
I thus decided to go to UNIX Ubutu. the first problem I encounter is tht on the site Ubuntu.com there are several vesions for downloading and it is not clear which is the one I need. there is a 10.10 and then there is a 10.04. I downloaded both SOs. 
neither one installs. The 10-10 stalls on the initial boot-up where you see the UBUNTU name with 4 or 5 dots below it . It stays running that ad infinitum.
The othe rversion, the 10.04 boots and run subsequent s for a bit  until te speaker icon appears on the top left and then after that it stalls as well. On the first try it said something about an unknown fatal error. On tries it just stalls after that icon appears and says  nothing further.
if i try to install it as a virtual system, it tels me I only hve 244 of mem and that it needs more.
I really do not care if I have to blow away the win xp ad just install the UBUNTU, in fact that is what i would like to do. Prior to attempting to install UBUNTU, I restored the laptop to factory set (using the restore CDs). It runs clean and faxt n windows (I avoided installing any win updates. left it at factory preset).
What can I do to install UBUNTU? I never expected UBUNTU too to be so hard to deal with from step #1?

Any assitance would be appreciated.

Thanks
Pirooz

---

### Post by shreeyashattal on 2010-09-06
> **pirooz said:**
> it tels me I only hve 244 of mem and that it needs more.

the problem is your system has only 256MB of RAM, which is not good :(

try running the same CD on another laptop/pc, should work fine, your laptop stalls because it runs out of RAM midway..

---

### Post by dirghrabadia on 2010-09-06
Hi there,
Ubuntu is a Linux distro. For now, I would recommend you to download 10.04 .iso file, and burn it on a CD/DVD. Then, restart and select the CD-ROM as the first boot device (if already not the first boot device by default). The rest of the installation procedures are fairly simple to follow. Let us know if you are stuck :)

---

### Post by Elfy on 2010-09-06
> **dirghrabadia said:**
> Hi there,
Ubuntu is a Linux distro. For now, I would recommend you to download 10.04 .iso file, and burn it on a CD/DVD. Then, restart and select the CD-ROM as the first boot device (if already not the first boot device by default). The rest of the installation procedures are fairly simple to follow. Let us know if you are stuck :)

The Op did that, the OP has low memory ;)

You might be better of with lubuntu or xubuntu

[http://lubuntu.net/](http://lubuntu.net/)
[http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)

---

### Post by sikander3786 on 2010-09-06
> **forestpiskie said:**
> The Op did that, the OP has low memory ;)

You might be better of with lubuntu or xubuntu

[http://lubuntu.net/](http://lubuntu.net/)
[http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)
Yes lubuntu should work. I haven't tried xubuntu but it should also work as lubuntu works for me on an old laptop with 256MB RAM.

---

### Post by pirooz on 2010-09-06
> **dirghrabadia said:**
> Hi there,
Ubuntu is a Linux distro. For now, I would recommend you to download 10.04 .iso file, and burn it on a CD/DVD. Then, restart and select the CD-ROM as the first boot device (if already not the first boot device by default). The rest of the installation procedures are fairly simple to follow. Let us know if you are stuck :)

many thanks for your reply. :D

I have done that and tried many times . It reboots fine. It starts the process alright. But it stalls after drawing a few icons. after that it is dead. A few times it said installer encountered an unspecified FATAL error and that it would take me back to my desktop.
It is hard to beieve that as another forum participant kindly suggested, that UBUNTU will not install due to lack of memory ( 1 mega with extended mem, 224 available) whereas windows XP did?

anyway I am about to throw the towel in on UBUNTU for right now, it seems it really is not all that easy or friendly to install as painted.

---

### Post by pirooz on 2010-09-06
> **shreeyashattal said:**
> the problem is your system has only 256MB of RAM, which is not good :(

try running the same CD on another laptop/pc, should work fine, your laptop stalls because it runs out of RAM midway..

Thanks so much for your reply.;)
yes i suspect the same thing too. Which is why I would really rather get rid of windows all together so that the whole 1 meg would be available for UBUNTU. Yet how is that done, the installation disk does not seem to give the option of complete replacement of the previous OS.?

thanks again

---

### Post by pirooz on 2010-09-06
> **forestpiskie said:**
> The Op did that, the OP has low memory ;)

You might be better of with lubuntu or xubuntu

[http://lubuntu.net/](http://lubuntu.net/)
[http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)

Thank you for the reply and the insight as well as the alternatives.
Yet, I wonder if there would be enough memory to install the UBUNTU if Windows would not be installed in the first place or if the HD could be Formatted to blow away the WIN OP system before installing Ubuntu? If the answer is yes i am willing to do that I do not need WIN at all. How would a clean installation of UBUNTU (replacing WIN XP, not standing side by side) be done? I do not see that option on the system install disk??
Thanks again

---

### Post by pirooz on 2010-09-06
> **sikander3786 said:**
> Yes lubuntu should work. I haven't tried xubuntu but it should also work as lubuntu works for me on an old laptop with 256MB RAM.

Once again thanks for the followup reply.

Ok I am all clear that Xubuntu or Lubuntu would work.
yet, I am curious as to if I got rid of WIN XP all together the 1 Meg of mem installed would not allow UBUNTU to be installed? Or is it that the UBUNTU needs the WIN installation for some reason??

---

### Post by jtarin on 2010-09-06
If you do not install virtually, 1GB of memory is enough.You can blow XP away or dual boot. the choice is yours....if you have the disc space.Ubuntu does not need the Win installation...only if you install it virtually...within Windows...get it?

---

### Post by pirooz on 2010-09-06
> **jtarin said:**
> If you do not install virtually, 1GB of memory is enough.You can blow XP away or dual boot. the choice is yours....if you have the disc space. Ubuntu does not need the Win installation...only if you install it virtually...within Windows...get it?

Thanks so much for the insight and advice. Much appreciated.
Indeed I know the virtual installation inside windows in a VM type set up where the environment where the op sys of UNIX runs is a virtual bubble supported by the WIN framework. On that point I am very clear.

I was expressing my astonishment that when UBUNTU is making a clean install it can not use the 1 meg of memory that is installed (640 conventional plus extended memory totaling 1 meg)??  Of curse when trying to install as a Virtual program it fails to install because it needs 250 k of memory and there is only 224 left because windows is hogging the rest. But why does the clean install fail as many here point out due to lack of memory?? when WIN XP installs with no problem on the same machine with 1 meg of memory??

---

### Post by jtarin on 2010-09-06
We are talking in terms of physical memory for clean install....from boot with Live CD.


> Ubuntu requires at least 256 MB of virtual RAM, or swap space. As a rule of thumb, if the computer has 512 MB or less of physical RAM, Linux operates best with double that in swap space. On computers with more than 512 MB of RAM, Ubuntu runs best with an equal amount of virtual RAM.
For this example, the computer has 512 MB of RAM, so we need 1024 MB of swap. In addition to this reserve, there is more space we need to subtract. For each partition after the first one, it is best practice to plan a buffer of at least 1 MB on either side.

---

### Post by pirooz on 2010-09-06
> **jtarin said:**
> We are talking in terms of physical memory for clean install....from boot with Live CD.

Thanks again.
I am guessing what you mean to relay so here goes:

yes indeed. when I do a mem check from DOS command line, it shows a total of 1 meg installed. So I figure when I insert the UBUNTU CD in the drive and reboot, this is what is available to it . yet installation fails after it advances for a few minutes and gets as far as drawing out the little icons for sound etc on the upper left hand side of the screen.

---

### Post by jtarin on 2010-09-06
The first thing to do is insure you have downloaded and burned a good CD. Run a md5 checksum on the .iso file and match it to the reported value where you downloaded.

---

### Post by pirooz on 2010-09-06
> **jtarin said:**
> The first thing to do is insure you have downloaded and burned a good CD. Run a md5 checksum on the .iso file and match it to the reported value where you downloaded.

much obliged. I'll run the check. though I downloaded that install file twice and both CDs when used produce the same error. The MD5 check will eliminate any possibility of a systemic error or deviance.

---

### Post by Elfy on 2010-09-06
It is also worth ensuring that the actual burn is good - there is an option to verify the disc. When the disc boots - press any key when you see the pic of a keyboard and man at the bottom.

You might also find that some of the boot options help - [https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by pirooz on 2010-09-06
> **forestpiskie said:**
> It is also worth ensuring that the actual burn is good - there is an option to verify the disc. When the disc boots - press any key when you see the pic of a keyboard and man at the bottom.

You might also find that some of the boot options help - [https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Thanks once more. All of your advice is really appreciated. I must admit however that I have no idea what keyboard & man you are referring to? When I booth the CD and installation begins, there is a screen reading UBUNTU with 4 or 5 colored circles below it, after about 3 min or so of intense whirling of the CD a SOUND icon appears on the top leftmost corner of the screen as the background changes to some galactic depiction (a galaxy??). That i as far as my installation gets.
Additionaly, I am not sure what boot options, the link you provided refers to? Is this for boting into UBUNTU, assuming it was ever installed? Or are these parameters to set when trying to install the program at first boot?


as an aside I should also mention that I tried to install XUBUNTU, as suggested by some friends here, yet its eventual fate was not much better than the UBUNTU installation attempts. The effort capsized w/o so much as an error message, only a dark screen and no further CD or Disk activity after a certain point ! I am really wondering if TOSHIBA made this computer UNIX proof !! LOL

Moreover, I apologize for my utter lack of knowledge when it comes to anything UNIX and hence responses that surely sound less than intelligent to most Forum participants.

Thanks again

---

### Post by pirooz on 2010-09-06
> **sikander3786 said:**
> Yes lubuntu should work. I haven't tried xubuntu but it should also work as lubuntu works for me on an old laptop with 256MB RAM.

Hi I thought I'd relay the following update:
I tried to install XUBUNTU, as  suggested , yet its eventual fate was not much  better than the UBUNTU installation attempts. The effort capsized w/o so  much as an error message, only a dark screen and no further CD or Disk  activity after a certain point ! I will now use the initial boot screen to test the hard disk & memory using the facilities offered there by XUBUNTU install's initil screen. If no errors then I will try to install again.

 I am really wondering if TOSHIBA made  this computer UNIX proof !! LOL

---

### Post by egalvan on 2010-09-06
> **pirooz said:**
> 

Moreover, **I apologize for my utter lack of knowledge **when it comes to anything UNIX and hence responses that surely sound less than intelligent to most Forum participants.

Thanks again

Pease, no apoligies...

you are in the **ABSOLUTE BEGINNER TALK**

which means (surprise!) that we talk about absolute beginner stuff,
which means (surprise!) that most folks coming here know absolutely nothing bout *nix, or computers, or programing, or the meaning of life, or the which-ness of what..

We were ALL OF US utterly lacking in knowledge, at one point in time or another.
Your desire to learn and your good humor will take you far.

**WELCOME!**  ):P


Oops, almost forgot...

I've installed Ubuntu 8.04 Hardy (2008) on over 80 machines...
only wi-fi ever gave me troubles...

I'm up to 5 10.04 Lucid (2010) installs, 
and FOUR have failed miserably. The fifth is running OK so far.
I'm still sorting them out.
We ALL have troubles, one time or another... ;)

---

### Post by pirooz on 2010-09-06
> **egalvan said:**
> Pease, no apoligies...

you are in the **ABSOLUTE BEGINNER TALK**

which means (surprise!) that we talk about absolute beginner stuff,
which means (surprise!) that most folks coming here know absolutely nothing bout *nix, or computers, or programing, or the meaning of life, or the which-ness of what..

We were ALL OF US utterly lacking in knowledge, at one point in time or another.
Your desire to learn and your good humor will take you far.

**WELCOME!**  ):P


Oops, almost forgot...

I've installed Ubuntu 8.04 Hardy (2008) on over 80 machines...
only wi-fi ever gave me troubles...

I'm up to 5 10.04 Lucid (2010) installs, 
and FOUR have failed miserably. The fifth is running OK so far.
I'm still sorting them out.
We ALL have troubles, one time or another... ;)

Thanks so much for your reply and the encouragement.

Having failed to install 10.04 UBUNTU and Xubunto as well. I am no thinking maybe I should just try and install the Hardy version. Your own experience with 80 installs is a great indication of how bug free that version may be for installation.

Fingers crossed!
Much obliged.

---

### Post by jtarin on 2010-09-06
On the flip side of that I have done about 6 different installs on 6 different computers of 10.04 and have had trouble with none of them. I have been installing Linux and BSD for over 13 years and this has been one of the most trouble free out of the box experiences.

---

### Post by pirooz on 2010-09-06
> **jtarin said:**
> On the flip side of that I have done about 6 different installs on 6 different computers of 10.04 and have had trouble with none of them. I have been installing Linux and BSD for over 13 years and this has been one of the most trouble free out of the box experiences.

Thanks for the flip side. 
It is perplexing then why neither UBUNTU nor XUBUNTO will install, or even give an intelligent reason why not on my WINDOWS XP old laptop?? I mean is windows XP instals in 15 minutes on this laptop, should UBUNTU or XUBUNTO not be capable of a trouble free install???](*,)

---

### Post by jtarin on 2010-09-06
[Look at these instructions.]("https://help.ubuntu.com/community/Installation").There are alternate ways of installing. Keep us informed of your progress and/or failure. There is also a link on that page for hardware compatibility.

---

### Post by pirooz on 2010-09-06
> **jtarin said:**
> [Look at these instructions.]("https://help.ubuntu.com/community/Installation").There are alternate ways of installing. Keep us informed of your progress and/or failure. There is also a link on that page for hardware compatibility.

Thanks a million for all your interest in this problem. Your latest tip is highly appreciated as were all the others.

I had seen this sheet and tried a couple of different routs. yest I have come up dry. I will nevertheless go over them again.

Yet, to tell the truth, having blown 2 days out of the long labor day weekend doing this, I figure anything this complicated to install in comparison to the much BASHED MS windows, is probably not for me anyway. I had read with much interest how light and fast the UNIX OP systems were. I guess what I had not figured on was the monumental task it is just to  install it on a laptop that can accommodate a WIN XP OP system (which installs perfectly in 15 min tops). It is hard to imagine how such a laptop would lack the minimum qualifications for UNIX?!Strange indeed.:mad:

On top of that the install just leaves one hanging, no messages (not even anything like the often hilariously, funny & incoherent WINDOWS error messages) no explanations; nothing but a black screen and a hanged system. 

I might consider the HARDY version just for kicks. But I have very little optimism as to success . We shall see.

---

### Post by jtarin on 2010-09-06
Keep in mind your XP came installed on your computer several years ago and XP has been around for quite a spell, but hardware has gone ahead.My installs take no more than 15-20 minutes ifyou don't count the updates at the end of the install. I can rmember installing XP and spending another hour or two....or more installing and updating drivers. So there is a reality to be reckoned with here.

---

### Post by pirooz on 2010-09-07
> **jtarin said:**
> Keep in mind your XP came installed on your computer several years ago and XP has been around for quite a spell, but hardware has gone ahead.My installs take no more than 15-20 minutes ifyou don't count the updates at the end of the install. I can rmember installing XP and spending another hour or two....or more installing and updating drivers. So there is a reality to be reckoned with here.

Thank so much once more for your reply. Yes indeed you are right as you have been all along with your advice. The lap top in question is no spring chicken. That is exactly why I earmarked it for a UNIX face-lift.

Having admitted that, however, if I recall UBUNTU, or other close cousins are all touted for how they will revive older machines cause they do not make such high demands as windows op do. Even though the XP service pack 1 is from a while back (no doubt there) I would have thought it would still be pretty comparable in demands to the UBUNTU. However, now I know that is not true. I mean at the end of the day if  the 10.04 was meant for a speedy machine with lots of RAM headroom, then what would be the competitive advantage?

That brings me to my previous point of maybe installing release 8 of the UBUNTU instead of the current memory hog 10.04. That version may be more in line with what the hardware I am trying to install it on. I mean after all 1 meg of RAM is not all that insufficient either.

 In fact now I will read all the assorted stories about how UBUNTU is the OP sys to revive and breath new life into older models and chuckle. Because that claim as it stands seems to be an exaggeration; at least from my perspective today. 

Again thanks a million.

---

### Post by Elfy on 2010-09-07
I'm still somewhat confused about how much RAM it is you actually have - if you do in fact have 1MB then I am even more confused about how you get XP to run.

If by 1 meg you mean 1Gb that is more then enough to run ubuntu, if that IS the case then I should look at other things that might be causing your issue.

---

### Post by jtarin on 2010-09-07
[Go here for some more insight into installing.]("https://help.ubuntu.com/community/Installation")

---

### Post by pirooz on 2010-09-07
> **jtarin said:**
> [Go here for some more insight into installing.]("https://help.ubuntu.com/community/Installation")

Much obliged to you.

---

### Post by Zill on 2010-09-07
> **forestpiskie said:**
> I'm still somewhat confused about how much RAM it is you actually have..."
Me too!  The OP stated "I have an old toshiba TA2000, intel centrino, with 1 meg of memory. It runs its original version of windows xp..."

[Microsoft XP]("http://www.microsoft.com/windowsxp/sysreqs/pro.mspx") specs state "128 megabytes (MB) of RAM or higher recommended (64 MB minimum supported; may limit performance and some features)" 

The minimum memory requirement for [Ubuntu 10.04 LTS]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes") is 256 MB of memory.

So, if the OP advises how much RAM is actually installed (presumably *not* 1MB) it will help us establish which is the best OS version to install.

My advice to the OP is to determine the exact amount of installed RAM, then download the appropriate ISO.  Verify the download md5sum, then burn to a CD.  Ensure the PC is set to boot from the CD drive, then reboot with the Ubuntu CD in the drive.  Rather than install I always test a CD by selecting the Live CD option to run the OS directly from the disk.  When this stage runs correctly it gives you more confidence that the hardware is suitable and the new OS can then be installed from the icon on the Live CD desktop.

Additional info to the OP... Ubuntu and all its variants, including Kubuntu, Xubuntu (not Xubunt**o**), are all GNU/Linux operating systems.  While Linux is Unix-like in some ways, Ubuntu is generally referred to as a [Linux]("http://en.wikipedia.org/wiki/Linux"), rather than Unix, OS.

---

### Post by ShakeyJake on 2010-09-07
It has to be GB, right? Surely by the time laptops were out they had more than 1MB of RAM. I tried googling 'Toshiba TA200' and found nought but this thread and an identical PCWorld one.

OP - Exactly which laptop do you have?

---

### Post by pirooz on 2010-09-07
> **Zill said:**
> Me too!  The OP stated "I have an old toshiba TA2000, intel centrino, with 1 meg of memory. It runs its original version of windows xp..."

[Microsoft XP]("http://www.microsoft.com/windowsxp/sysreqs/pro.mspx") specs state "128 megabytes (MB) of RAM or higher recommended (64 MB minimum supported; may limit performance and some features)" 

The minimum memory requirement for [Ubuntu 10.04 LTS]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes") is 256 MB of memory.

So, if the OP advises how much RAM is actually installed (presumably *not* 1MB) it will help us establish which is the best OS version to install.

My advice to the OP is to determine the exact amount of installed RAM, then download the appropriate ISO.  Verify the download md5sum, then burn to a CD.  Ensure the PC is set to boot from the CD drive, then reboot with the Ubuntu CD in the drive.  Rather than install I always test a CD by selecting the Live CD option to run the OS directly from the disk.  When this stage runs correctly it gives you more confidence that the hardware is suitable and the new OS can then be installed from the icon on the Live CD desktop.

Additional info to the OP... Ubuntu and all its variants, including Kubuntu, Xubuntu (not Xubunt**o**), are all GNU/Linux operating systems.  While Linux is Unix-like in some ways, Ubuntu is generally referred to as a [Linux]("http://en.wikipedia.org/wiki/Linux"), rather than Unix, OS.

Good day and thanks for such an elaborate reply. I stand corrected on the UNIX vs. LINUX nomenclature. Much obliged.:D

I also noted the typo in the  XUBUNTU I typed with an "o". Thanks again.;)

As for the memory, when I do a mem check from the DOS prompt I get the following:

1 meg installed (640 main+ extended) and for some reason only 224 RAM free. Now that maybe because when we measure this from the prompt windows xp OP is already loaded and sponging lots of RAM. Which is why I had wondered a few emails back if it is not wiser to just Fdisk the whole windows OP system and then install UBUNTU on a barren laptop where it could make use of the full RAM (though once the system boots from the CD I would assume no WIN OP system is loaded to soak memory anyway).

I noted your advice :
"...Rather than install I always test a CD by selecting the Live CD option to run the OS directly from the disk..."
And I assure you I tried this option as well with the same results: A black Hole; after a minute or two, the whole system seems to fall into a an abyss where the screen remains black and the CD drive stops whirling. Basically a hung system requiring a cold shutdown by force.

On the advice of another forum friend I did the MD5SUM and it all looked good. I tried installing the 10.04 iso, the 10.10 iso, the XUBUNTU iso, all to the same effect. I also ran a complete disk check and no errors were found.

I have also looked at the alternative installation page of UBUNTU (a sure fire eye glazer) and tried a few tricks from there but all things related to LINUX seem to fail when it comes to the jinxed Toshiba. My last stand this evening will be to try and install an earlier version of UBUNTU and see what happens. Thnks goodness blank CDs are dirt cheap!

Thanks a million.

---

### Post by pirooz on 2010-09-07
> **ShakeyJake said:**
> It has to be GB, right? Surely by the time laptops were out they had more than 1MB of RAM. I tried googling 'Toshiba TA200' and found nought but this thread and an identical PCWorld one.

OP - Exactly which laptop do you have?

HI and thanks for the posted reply. I am currently not at home to look at the model, but I may have mistyped the model number as TA when it should have been TE 2000. I shall confirm in a few hours.

As for the memory indeed it has a total mem of 1 meg (640 + extended).

Thanks again

---

### Post by Zill on 2010-09-07
> **pirooz said:**
> ...As for the memory, when I do a mem check from the DOS prompt I get the following:

1 meg installed (640 main+ extended) and for some reason only 224 RAM free. Now that maybe because when we measure this from the prompt windows xp OP is already loaded and sponging lots of RAM. Which is why I had wondered a few emails back if it is not wiser to just Fdisk the whole windows OP system and then install UBUNTU on a barren laptop where it could make use of the full RAM (though once the system boots from the CD I would assume no WIN OP system is loaded to soak memory anyway)...
I haven't used Windows or DOS for many years but this result seems very suspect to me. :-(
It *may* be because the original DOS memory spec was limited to 640kB, later expanded and extended to 1MB and above.  Possibly the Windows XP DOS utility emulates this early DOS behaviour, reporting your 1MB result.  However, if your laptop *is* a Toshiba TE2000 then a quick websearch shows the installed RAM as either 256MB or 512MB.

I suggest you verify the actual installed RAM using a different method such as checking the BIOS during boot and/or using the supplied Windows tools.  If you can easily open up the laptop and take a look at the RAM module(s) this might help with identification. ;-)

If the installed RAM *is* 256MB or more then it should run Ubuntu, although this is really the absolute minimum.  If you *should* have 256MB or more but all the diagnostics are reporting a lower number then it looks like one or more of your RAM modules have died.

---

### Post by pirooz on 2010-09-07
> **Zill said:**
> I haven't used Windows or DOS for many years but this result seems very suspect to me. :-(
It *may* be because the original DOS memory spec was limited to 640kB, later expanded and extended to 1MB and above.  Possibly the Windows XP DOS utility emulates this early DOS behaviour, reporting your 1MB result.  However, if your laptop *is* a Toshiba TE2000 then a quick websearch shows the installed RAM as either 256MB or 512MB.

I suggest you verify the actual installed RAM using a different method such as checking the BIOS during boot and/or using the supplied Windows tools.  If you can easily open up the laptop and take a look at the RAM module(s) this might help with identification. ;-)

If the installed RAM *is* 256MB or more then it should run Ubuntu, although this is really the absolute minimum.  If you *should* have 256MB or more but all the diagnostics are reporting a lower number then it looks like one or more of your RAM modules have died.

Hi.
thank so much for such great advice. I checked the exact model of the lap top. It is indeed from the TE2000 series, but the exact model No. is TE2300. 
A check of the memory in Dos (though you don't trust it as you point out) gives the following info:
655360 Bytes Total Conventional memory
655360 Available to MS-DOS
1048576 Bytes Total contiguous Extended memory
941056 Bytes available XMS memory
Elsewhere:
the sys property check using the facility on the control panel reads as follows:
Processor 1.4 GHz & 224 MB of memory

I am downloading an application that might give me an independent read of the system from within Windows for memory installed. I'll report that as soon as I have the application and am able to run it. For now the above stats are what I have (short of popping open the back of the laptop to get a physical read as you suggested).

thanks so much once more.

---

### Post by jtarin on 2010-09-07
4 pages and 9 hrs later......

TE2300

Standard Memory	256 MB - 1.0 GB (removable)
Maximum Memory	2.0 GB
Memory Expansion	2 sockets
Memory Comments	PC2100 DDR SDRAM SODIMMs
CPU Type	Intel Pentium M
Model Comments	400MHz FSB, Intel 855GM Chipset

So you have a minimum of 256MB installed memory

---

### Post by pirooz on 2010-09-07
> **jtarin said:**
> 4 pages and 9 hrs later......

TE2300

Standard Memory	256 MB - 1.0 GB (removable)
Maximum Memory	2.0 GB
Memory Expansion	2 sockets
Memory Comments	PC2100 DDR SDRAM SODIMMs
CPU Type	Intel Pentium M
Model Comments	400MHz FSB, Intel 855GM Chipset

So you have a minimum of 256MB installed memory

well much obliged once again. yes it seems time flies when we are busy having fun! Of course I fessed up to being an absolute beginner early on. sorry.

anyway I am sure you saw my post just about 30 min ago with the info I extracted from DOS. Details are posted there.
Now i ran a windows based program to get more reliable info and here it is (also attached as PDF in a more presentable form):

Property Value 
Memory Summary
Location System board or motherboard
Maximum Capacity 1024 MBytes
Memory Slots 3
Error Correction None
Use System memory
Location System board or motherboard
Maximum Capacity 32 MBytes
Memory Slots 1
Error Correction None
Use Video memory
Location System board or motherboard
Maximum Capacity 512 KBytes
Memory Slots 1
Error Correction None
Use Flash memory
Location System board or motherboard
Maximum Capacity 1024 KBytes
Memory Slots 1
Error Correction None
Use Cache memory
Device Locator Slot 2
Manufacturer Hyundai Electronics
Part Number HYMD232M646A6-H
Serial Number 073A2145
Capacity 256 MBytes
Memory Type SDRAM DDR
Speed PC2100 (133 MHz)
Data Width 64 bits
Voltage SSTL 2.5V
Error Correction None
Refresh Reduced (.5x)...7.8 &#956;s
Manufacturing Date N/A
EPP SPD Support No


If I am not mistaken there is a max conventional+ extended mem of 1 meg. And at least 256 installed. That should have been enough for the Ubuntu install and more than sufficient for the Xubuntu. So the mystery continues for me .....

thanks so much

---

### Post by pirooz on 2010-09-07
> **Zill said:**
> I haven't used Windows or DOS for many years but this result seems very suspect to me. :-(
It *may* be because the original DOS memory spec was limited to 640kB, later expanded and extended to 1MB and above.  Possibly the Windows XP DOS utility emulates this early DOS behaviour, reporting your 1MB result.  However, if your laptop *is* a Toshiba TE2000 then a quick websearch shows the installed RAM as either 256MB or 512MB.

I suggest you verify the actual installed RAM using a different method such as checking the BIOS during boot and/or using the supplied Windows tools.  If you can easily open up the laptop and take a look at the RAM module(s) this might help with identification. ;-)

If the installed RAM *is* 256MB or more then it should run Ubuntu, although this is really the absolute minimum.  If you *should* have 256MB or more but all the diagnostics are reporting a lower number then it looks like one or more of your RAM modules have died.

back again with the info you suggested I obtain from within windows. I posted it in a reply to another friend here. But i will repeat it in this reply as well just in case.
Here goes:
Property Value 
Memory Summary
Location System board or motherboard
Maximum Capacity 1024 MBytes
Memory Slots 3
Error Correction None
Use System memory
Location System board or motherboard
Maximum Capacity 32 MBytes
Memory Slots 1
Error Correction None
Use Video memory
Location System board or motherboard
Maximum Capacity 512 KBytes
Memory Slots 1
Error Correction None
Use Flash memory
Location System board or motherboard
Maximum Capacity 1024 KBytes
Memory Slots 1
Error Correction None
Use Cache memory
Device Locator Slot 2
Manufacturer Hyundai Electronics
Part Number HYMD232M646A6-H
Serial Number 073A2145
Capacity 256 MBytes
Memory Type SDRAM DDR
Speed PC2100 (133 MHz)
Data Width 64 bits
Voltage SSTL 2.5V
Error Correction None
Refresh Reduced (.5x)...7.8 &#956;s
Manufacturing Date N/A
EPP SPD Support No


I annexed a PDF version to my other reply a few minutes ago, I assume there is no need to re send the PDF file. If you wish you can check it out in a reply sent out a few minutes ago in this same thread.
Thanks again for everything you have brought to my attention. As I look at these figures it seems there is enough RAM to install UBUNTU and more than enough surely for Xubuntu.

---

### Post by Zill on 2010-09-08
> **pirooz said:**
> back again with the info you suggested I obtain from within windows. I posted it in a reply to another friend here. But i will repeat it in this reply as well just in case...
Thanks for the info.  There is no need to repeat info as *all* postings are visible to *all* users on these forums. ;-)
So, you have 256MB RAM installed.  Forget about the "conventional/expanded/extended" terminology - that used to be relevant to DOS systems but has no relevance with modern OS's.

You *should* be able to run Ubuntu 10.04 with 256MB.  As I suggested earlier, I always recommend trying to run Ubuntu first as a Live CD - ie. no installation.  My logic is that if this does work then it stands a good chance of installing OK.  Click [here]("https://help.ubuntu.com/community/LiveCD") for more info on the Live CD.

If the OS will not run from a Live CD then all is not lost - it may be that other factors (borderline memory size being one!) are preventing this.  In such cases you may be able to install using the Alternate CD - which will allow installation without needing the GUI.

I suggest you try running your Ubuntu 10.04 Live CD on *another* PC to verify the CD is OK.  This will not change anything on the PC but will prove you have a good disk.  Once this has been verified, try the same thing with your Toshiba laptop.  Then please advise exactly what happens.

---

### Post by pirooz on 2010-09-08
> **Zill said:**
> Thanks for the info.  There is no need to repeat info as *all* postings are visible to *all* users on these forums. ;-)
So, you have 256MB RAM installed.  Forget about the "conventional/expanded/extended" terminology - that used to be relevant to DOS systems but has no relevance with modern OS's.

You *should* be able to run Ubuntu 10.04 with 256MB.  As I suggested earlier, I always recommend trying to run Ubuntu first as a Live CD - ie. no installation.  My logic is that if this does work then it stands a good chance of installing OK.  Click [here]("https://help.ubuntu.com/community/LiveCD") for more info on the Live CD.

If the OS will not run from a Live CD then all is not lost - it may be that other factors (borderline memory size being one!) are preventing this.  In such cases you may be able to install using the Alternate CD - which will allow installation without needing the GUI.

I suggest you try running your Ubuntu 10.04 Live CD on *another* PC to verify the CD is OK.  This will not change anything on the PC but will prove you have a good disk.  Once this has been verified, try the same thing with your Toshiba laptop.  Then please advise exactly what happens.

Thank you for such immensely valuable observations and having taken the time to make those points to guide me. I will try the live CD on an alternative laptop later this evening and report back. I had tried the live run on the Toshiba TE2300 and it slid right into the same black hole as the rest of the installation efforts with UBUNTU and XUBUNTU.
I will try live CD and report back.
Thanks a million.

---

### Post by pirooz on 2010-09-08
> **Zill said:**
> Thanks for the info.  There is no need to repeat info as *all* postings are visible to *all* users on these forums. ;-)
So, you have 256MB RAM installed.  Forget about the "conventional/expanded/extended" terminology - that used to be relevant to DOS systems but has no relevance with modern OS's.

You *should* be able to run Ubuntu 10.04 with 256MB.  As I suggested earlier, I always recommend trying to run Ubuntu first as a Live CD - ie. no installation.  My logic is that if this does work then it stands a good chance of installing OK.  Click [here]("https://help.ubuntu.com/community/LiveCD") for more info on the Live CD.

If the OS will not run from a Live CD then all is not lost - it may be that other factors (borderline memory size being one!) are preventing this.  In such cases you may be able to install using the Alternate CD - which will allow installation without needing the GUI.

I suggest you try running your Ubuntu 10.04 Live CD on *another* PC to verify the CD is OK.  This will not change anything on the PC but will prove you have a good disk.  Once this has been verified, try the same thing with your Toshiba laptop.  Then please advise exactly what happens.

HI
On a different laptop it loads perfectly fine. In 1 min it was up and running from the CD. Strange That! So we now know the UBUNTU 10.04 ISO CD is perfect and has no errors. Of course the same procedure does not work on the Toshiba. No live CD based usage or install is permitted. It just sinks into oblivion.

Elsewhere, besides being baffled by why it does not work either live or installed on the TOSHIBA TE2300, I was also a bit bugged because when I tried the system on an alternative laptop , I could not make it detect the wireless  (80211.b) WIFI I have. I read the procedure and it implies that I could just go to network connections (the wireless ICON on the top right hand side) click it and see what wireless networks are running and then connect. However no wireless networks were being detected at all and there are maybe 5 of them that I usually see from my APT (neighbors presumably). In fact the WIFI detection light on the laptop was off and no way to turn it on as long as UBUNTU was loaded. Onceback to windows it was just fine. Is this because the UBUNTU was not installed but loaded from a CD or is there a special procedure for detecting networks?

of course this is besides the point unless I can get the OP installed on the Toshiba to begn with ; LOL !:D

Thanks for listening.

---

### Post by jtarin on 2010-09-08
Can you find the model number of your CD player? Maybe it only recognizes certain types of discs?

---

### Post by pirooz on 2010-09-08
> **jtarin said:**
> Can you find the model number of your CD player? Maybe it only recognizes certain types of discs?


Hi Again and thanks for your reply.
Oh no it is not the CD player (drive) . It reads and recognizes the CD just fine, as it does any CD. It runs the CD perfectly and shows the initial menus effortlessly. As stated it even gets as far as the psychedelic background that UBUNTU uses and adds a few of the icons, before the whole installation goes off a cliff. So I really doubt it is the CD unit.

Thanks so much once again.

---

### Post by Elfy on 2010-09-09
If you have low memory it is entirely possible that is not gioing to be much fun with ubuntu.

In fact if - as it seems - you in fact have less than the minimum requirement dues to video taking some of the RAM then it will be worse than not much fun.

You could try using the Install rather than the Try option from the CD boot menu - however you'll not be able to determine what hardware issues you have.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

I once again suggest you try lubuntu or one of the other low spec distros out there.

---

### Post by Zill on 2010-09-09
pirooz:  Firstly, I suggest you ignore the wifi problem for now and connect to your router with an ethernet cable.  Wifi *can* work "out of the box" but sometimes needs a bit of persuasion. ;-)  It is easier to resolve wifi problems *after* you have installed the OS and, preferably, with an ethernet connection initally.

As you have proved the CD is good it seems that your Toshiba laptop specs are inadequate.  Remaining options are:

1)  Upgrade the RAM to the maximum you can afford (at least 512MB)!  The laptop should then run the Ubuntu Live CD, allowing easy installation *and* increasing performance.

2)  Try to install Ubuntu using the [Alternate]("www.ubuntu.com/desktop/get-ubuntu/alternative-download") install disk.  This may be less "user-friendly" as I believe installation is text-based and doesn't use a GUI.

3)  Try to install [Lubuntu]("https://wiki.ubuntu.com/Lubuntu"), which *should* run with lower RAM requirements than Ubuntu.

Caveats:  I have never used options 2 or 3 so cannot really comment on them!

ps.  Xubuntu is a good OS but, I believe, is generally considered to have similar RAM requirements to Ubuntu.

---

### Post by pirooz on 2010-09-09
> **forestpiskie said:**
> If you have low memory it is entirely possible that is not gioing to be much fun with ubuntu.

In fact if - as it seems - you in fact have less than the minimum requirement dues to video taking some of the RAM then it will be worse than not much fun.

You could try using the Install rather than the Try option from the CD boot menu - however you'll not be able to determine what hardware issues you have.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

I once again suggest you try lubuntu or one of the other low spec distros out there.

Hi and Thanks again for the assistance.
Indeed I tried to install XUBUNTU (one of your recommendations) , alas, much to the same effect as UBUNTU ! So if it is a question of low RAM headroom with the UBUNTU install it certainly can't be the issue with the XUBUNTU install gone awry. And I have tried a complete install of UBUNTU (as well as XUBUNTU) several times. I only tried the LIVE CD based test run upon advice from memebrs yet as you point out if anything that would confront even lower available RAM.
Thanks again.

---

### Post by pirooz on 2010-09-09
> **Zill said:**
> pirooz:  Firstly, I suggest you ignore the wifi problem for now and connect to your router with an ethernet cable.  Wifi *can* work "out of the box" but sometimes needs a bit of persuasion. ;-)  It is easier to resolve wifi problems *after* you have installed the OS and, preferably, with an ethernet connection initally.

As you have proved the CD is good it seems that your Toshiba laptop specs are inadequate.  Remaining options are:

1)  Upgrade the RAM to the maximum you can afford (at least 512MB)!  The laptop should then run the Ubuntu Live CD, allowing easy installation *and* increasing performance.

2)  Try to install Ubuntu using the [Alternate]("www.ubuntu.com/desktop/get-ubuntu/alternative-download") install disk.  This may be less "user-friendly" as I believe installation is text-based and doesn't use a GUI.

3)  Try to install [Lubuntu]("https://wiki.ubuntu.com/Lubuntu"), which *should* run with lower RAM requirements than Ubuntu.

Caveats:  I have never used options 2 or 3 so cannot really comment on them!

ps.  Xubuntu is a good OS but, I believe, is generally considered to have similar RAM requirements to Ubuntu.

Thank you very much once again for your response. I appreciate the clear concise, articulated language. It is all pretty clear and the path runs through additional RAM installation if for some reason I should want to install UBUNTU and ditch the WIN XP OS which runs great on the same machine. I'll be weighing that option; though I had always gotten the impression that Windows was the RAM hog !
As for XUBUNTU, at least the description I read and advice I got elsewhere pointed to a less needy OP. I might give LUBUNTU a try, though even their web page looks unattractive enough to discourage anyone from really looking forward to the OP, LOL.

I really thank you for all the time and assistance.

---

### Post by Zill on 2010-09-09
> **pirooz said:**
> ...It is all pretty clear and the path runs through additional RAM installation if for some reason I should want to install UBUNTU and ditch the WIN XP OS which runs great on the same machine. I'll be weighing that option; though I had always gotten the impression that Windows was the RAM hog !
You must compare "like with like".  Ubuntu 10.04 is considerably newer and more advanced than Windows XP and has, inevitably, got higher system requirements.

[Windows 7]("http://windows.microsoft.com/systemrequirements") (the approximate Microsoft equivalent) specifies "1 gigabyte (GB) RAM (32-bit) or 2 GB RAM (64-bit)".  I believe you would get better performance with Ubuntu 10.04 on your laptop (with a RAM upgrade) than you would with Windows 7!

---

### Post by Zill on 2010-09-09
> **pirooz said:**
> ...It runs its original version of windows xp just fine, but one the several service packs and updates are added it slows to a crawl.
> **pirooz said:**
> ...WIN XP OS which runs great on the same machine.
ps.  Now I'm really confused about how well Windows XP runs. ;-)

I really miss not having Windows on *my* PCs. :P

---

### Post by Elfy on 2010-09-09
To the OP - you have been given the same information over and over by different people.

The answer is not going to change - you don't have enough RAM for ubuntu, xubuntu might work, lubuntu is likely to ;)

System requirements for Ubuntu - RAM - The minimum memory requirement for Ubuntu 10.04 LTS is 256 MB of memory.

System requirements for Xubuntu - RAM - You need 192 MB RAM to run the Live CD or 192 MB RAM to install. 

System requirements for Lubuntu - RAM - Minimum requirements for lubuntu are ... 128 Mb RAM configuration

---

### Post by jtarin on 2010-09-09
D-----it! Someone's lying about the ram.](*,)](*,)](*,)](*,):lolflag:

---

### Post by pirooz on 2010-09-09
> **Zill said:**
> You must compare "like with like".  Ubuntu 10.04 is considerably newer and more advanced than Windows XP and has, inevitably, got higher system requirements.

[Windows 7]("http://windows.microsoft.com/systemrequirements") (the approximate Microsoft equivalent) specifies "1 gigabyte (GB) RAM (32-bit) or 2 GB RAM (64-bit)".  I believe you would get better performance with Ubuntu 10.04 on your laptop (with a RAM upgrade) than you would with Windows 7!

Thank you for the follow-up. No doubt a RAM upgrade would aid UBUNTU install & run smoothly. However, do I want to spend money on an old laptop? The only reason I even considered Linux was because of all the hype surrounding its miserly system resource requirements and how it resurrects old PC giving them a new lease on life. I guess progress means bloat, in all OP systems. That is why I was thinking of installing as a last resort UBUNTU release 8. That might be less of a burden. I guess I will find out.

As for the WIn XP, I have it running as service pack 1, and it is lightning fast. So if nothing else works I guess I will have to live with it or donate the equipment!

As always, I am extremely grateful for your great advice & insights. :p

---

### Post by Elfy on 2010-09-09
I don't think that this is going to go anywhere now - you have more than enough information to deal with the situation.

Good luck with whatever you decide to do - if once you have a *buntu installed we will be pleased to help you with any issues you might have.

Thread closed.

---

### Post by pirooz on 2010-09-09
> **Zill said:**
> ps.  Now I'm really confused about how well Windows XP runs. ;-)

I really miss not having Windows on *my* PCs. :P

LOL thanks again.
I am so sorry if I have confused you. let me try again:

WIN XP SRRVICE PACK 1 Runs on the Toshiba AE2300 lightning fast. Only when service pack 2 is installed does it slow down to an unacceptable crawl. I hope it is now more clear! 
again sorry & Thanks.:p

---

