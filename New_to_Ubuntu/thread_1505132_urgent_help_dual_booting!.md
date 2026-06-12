---
title: "urgent help dual booting!"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by abkarch on 2010-06-08
OK so my bro's computer got shut off randomly at the worst possible time (it was working very hard) and apparently all the USB and PS/2 drivers are corrupt for windows. right now i am typing from a live DVD boot of ubuntu 10.04. i cannot access windows 7 at all. i need to install this DVD on my machine alongside windows 7 until something can be worked out. i had no unallocated disc space (from what i read here [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) you need some unallocated disk space)
how do i do this asap? thx in advance. i also have no windows 7 disc, he had purchased it  and downloaded it digitally and installed it directly from vista, meaning that the only thing i MAY have is the CD key)

Thanks for your patience, i am very new to linux!

---

### Post by cbecker78 on 2010-06-08
you can shrink the size of the windows 7 partition using gparted on the live CD.  its under system -> administration on the top gnome panel of the live cd (assuming you are using Ubuntu and not Kubuntu).  If you're just planning on this being temporary, you can just allocate around 10-15 GB for the ubuntu installation.  resizing will give the unallocated space.

This site seems to have a good tutorial.  ask if any questions.

If you find you like ubuntu, you can make a bigger partition later for /home (all your stuff) and leave the main os installed in the partition you just created with plenty of room to grow.

---

### Post by abkarch on 2010-06-08
oh. crap. all i know is that that sounds bad. i cant even boot into windows, but it does get to the login screen but no input devices are working whatsoever.

---

### Post by abkarch on 2010-06-08
can neone help?

---

### Post by cbecker78 on 2010-06-08
Um... I can't actually read what it says in your attachment...  But nothing sounds bad as far as I know, other than you are locked out of your win7 until you get a restore cd.  

All you need to get the Ubuntu installed alongside windows like you said you wanted in the first post is:
1)backup data on win partition using the live cd
2)use gparted on the live cd to resize the windows partition (just decrease the size by 6-10 GB, assuming you have that much free space on the disk)
3)format the now empty space to install ubuntu
4)click on the install ubuntu icon
5)follow the prompts

Or, follow the guide you were probably looking at to begin with:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Ignore the part about having the windows recovery cd, you will get that later when you can...

Is the something else you were confused about?  Hope that information helps.

Edit:  After squinting, is that saying it can't mount the partition?

---

### Post by cbecker78 on 2010-06-08
for windows, did you try unplugging and plugging back in the keyboard?  There is probably a windows forum that can help you with Win7 specifically, but I suspect the issue is as you suggested first, and you need the recovery cd.

---

### Post by abkarch on 2010-06-08
it wont let me resize the disk because of that message. it say that the NTFS is inconsistant and that the F parimeter is very important. it says to run chkdsk /f in windows, which i cant do.

yes i did try unplugging and replugging

---

### Post by pizza-is-good on 2010-06-08
> **abkarch said:**
> oh. crap. all i know is that that sounds bad. i cant even boot into windows, but it does get to the login screen but no input devices are working whatsoever.

OK, thanks for that screenshot. Looks like your windows partition is really messed up. (If sda2, the one you were posting the screenshot of, is your windows one). You might have to fix it. testdisk might fix it for you. I have never used it, so I will not give instructions on how to, as I'm not sure if I'd do it correctly. Maybe someone else can?

---

### Post by 4Orbs on 2010-06-08
I'm not sure what you are hoping to accomplish. If you are trying to somehow recover the Windows 7 installation or files inside Windows then you need advice way beyond what I can offer. On the other hand, if you just want to replace (erase) Windows completely and install Ubuntu instead, that shouldn't be too difficult.

---

### Post by abkarch on 2010-06-08
that would be great if someone could!

---

### Post by pizza-is-good on 2010-06-08
> **abkarch said:**
> it wont let me resize the disk because of that message. it say that the NTFS is inconsistant and that the F parimeter is very important. it says to run chkdsk /f in windows, which i cant do.

yes i did try unplugging and replugging

OK. I think, as I said above, that testdisk will help you. I found the following instructions:

On a terminal in the live cd, type:
```
sudo apt-get install testdisk
```and then do:
```
sudo testdisk
```I'm not sure what happens after that. I imagine you'll have to go through the program. Nowhere did I find that you could loose data by using it, but do so at your own risk.

I've had the 'run chkdsk /f on windows' error before. I always fix it by reformatting the drive, or if that fails, delete the partition table, and then reformat. Of course, you loose all data when you do that, so don't try it if you care about what you have in there.

---

### Post by abkarch on 2010-06-08
ok man, ill try that later. i cant really afford to reformat, cause i have about 300 GB of data on there right now, so its not ideal. but thx.

---

### Post by pizza-is-good on 2010-06-08
> **abkarch said:**
> ok man, ill try that later. i cant really afford to reformat, cause i have about 300 GB of data on there right now, so its not ideal. but thx.


Good luck. Let us know how it goes.

---

### Post by cbecker78 on 2010-06-08
maybe take a look at these guides too:

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)
[http://tolearnfree.blogspot.com/2009/02/repair-windows-partition-through-linux.html](http://tolearnfree.blogspot.com/2009/02/repair-windows-partition-through-linux.html)

Good luck!  Sorry it was worse than I first thought.  If all else fails, before you give up and reformat the whole thing, it may also be possible to clone the whole drive to recover undamaged files.  This would of course require buying another HD of equal or greater size...

---

### Post by wilee-nilee on 2010-06-09
If windows was down-loadable to begin with I would contact who it was purchased from and get a ISO link or buy the DVD. it will be needed at some point in the future, and if not it is some cheap insurance. If this was a digital river download they may, if the year long download wasn't purchased, may allow it to be now.

---

### Post by bigseb on 2010-06-09
If you have problems with Windows 7 (or anything Windows related) this is the best place to look: [www.sevenforums.com](www.sevenforums.com)

Those guys really know their stuff - not saying people on this forum don't - and have helped me out of many a pickle. Good luck!

---

### Post by wilee-nilee on 2010-06-09
> **bigseb said:**
> If you have problems with Windows 7 (or anything Windows related) this is the best place to look: [www.sevenforums.com](www.sevenforums.com)
[B]
Those guys really know their stuff[/B] - not saying people on this forum don't - and have helped me out of many a pickle. Good luck!
I would disagree with this but it doesn't hurt to try. They will consider grub as the problem at all times so beware.

---

### Post by abkarch on 2010-06-09
going to try the think mention earlier as soon asap (which might be an hour or two) and ill let yall know how that goes

---

### Post by abkarch on 2010-06-09
it says
E: Couldn't find package testdisk

when i type sudo apt-get install testdisk

---

### Post by abkarch on 2010-06-09
anyone?

---

### Post by Phillip Spencer on 2010-06-09
> **abkarch said:**
> anyone?

I am no expert on this area, in fact I am suffering fairly horrendous dual-booting problems from screwing up my Windows 7 partitions.  I have been having a lot of support and ideas through this forum, including links to useful tools and sources of information.

I do not know if it will help you but there will be no harm in scanning the thread I started:
[]("http://ubuntuforums.org/search.php?searchid=73729422")[http://ubuntuforums.org/showthread.php?t=1491232](http://ubuntuforums.org/showthread.php?t=1491232)
to see if that adds any useful input.  

I did discover a very useful Ubuntu Rescue Remix CD and Windows 7 32-bit repair kit CD in this process - links to these are in the thread.

Good luck!
Cheers
Phillip

---

### Post by oldfred on 2010-06-09
To download testdisk you have to enable the universe repositories. System, Administration, Software sources. Anything you download with liveCD of course is lost if you reboot. 

You do not want to try to resize or use NTFS untill  you have run checkdisk to fix whatever errrors it has. Doing anything else has a chance of corrupting your data.

Generally we prefer to use the windows tools to resize Vista and 7 partitions. There is a check box on gparted that will prevent problems in windows that no one checks and then has problems with windows after using gparted.
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked. The newest version of linux follows the same convention so it will be less of a problem in the future.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

Links to windows repair (only) CD:
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by Jahocolips on 2010-06-09
I would emplore you to run chkdsk before messing with it further, HOWEVER... ntfsresize has a handy flag which will do it's thing regardless of bad sectors. I believe it is...
```
ntfsresize --bad-sectors
```

If you run out of options and you want to give it a shot that should do the trick.

ntfs probably came along those bad sectors sometime or another, then if you ever defraged, or ran SeaTools it would have reallocated that bad sector, or chkdsk would have fixed it and again reallocated it. In either case ntfs doesn't erase data so it's finding more bad clusters (hence the "Cluster ... is referenced multiple times" error)

If that is the case, then ntfsresize --bad-sectors wouldn't hurt anything. But again we don't know that, so safest is to run chkdsk multiple times until no errors are reported...

Good luck.

---

### Post by abkarch on 2010-06-09
testdisk is working now, and ive been looking around in it, but i have no idea how to use it

---

### Post by abkarch on 2010-06-09
been messing around with stuff, and now i know the following:
i have 3 bad sectors
"MTF and MTF mirror are bad. Unable to repair them" -testdisk

does this mean i should start focussing on trying to retrieve my stiil good data instead of fixing the OS?

---

### Post by Jahocolips on 2010-06-09
Hmmm... Not good. Well there are some tricks that can still be tried. MBR is short for Master Boot Loader, every computer has one and it tells the computer where to boot from. You can't boot into Windows so one might conclude that the MBR is corrupt. Go into the advanced tools in TestDisk and see if the MBR is reported as intact, if not, we can try and write new code over the old MBR using TestDisk's MBRCode option, and see if you can't at least get into windows and salvage some data...

Use [this technique]("http://www.cgsecurity.org/wiki/Menu_MBRCode")

I believe you're referring to MFT fragmentation. Basically, due to extensive fragmentation of data, the MFT (Master File Table) which is a data structure that tells your NTFS (New Technology File System) Where everything is at, can no longer be interpreted and your file system can't find anything. So not likely you'll salvage big programs, like movies, or video games. Small files, like pictures and documents may still be intact for rescuing though.

Sounds like your hard drive is on it's deathbed anyhow. Might want to start thinking about grabbing a new one and getting down on a fresh install of Ubuntu... ;-)

If this doesn't work, let me know because there are still a few more tricks we can try.

---

### Post by abkarch on 2010-06-10
see the wierd thing is that i can boot into windows and i get to the logon scree, except all mouse, keyboard, joysticks, etc stop working.

so i guess its time to start searching for a new one.

i forgot to mention the reason it got shut off in the first place was because someone flicked a lightswitch that controls a wall socket (thinking it controlled a light) and the computer was plugged into that wall socket.

---

### Post by Jahocolips on 2010-06-10
What kind of mouse and keyboard are you using? Please include model number as well.

---

