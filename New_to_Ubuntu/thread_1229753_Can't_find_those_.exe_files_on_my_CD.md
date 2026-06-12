---
title: "Can't find those .exe files on my CD"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by StephenG on 2009-08-02
I have only Ubuntu 9.04.  No other Windows partitions or installs.  I seem to have the latest version of Wine installed adn it shows up on the applications menu.  I'm trying to install Rosetta Stone v.3, which is rated either Gold or Platinum, depending on where you're looking in the WineApp database.  After I put the RS CD into the drive, the drive shows up on my menu but there's no indication there are any files on the CD.  There are, in fact, since I just installed the program on my other Win machine.  I've tried going through the Wine process and it can't find anything.  I've tried going through terminal and changing to the CD drive.  Again, no files of any kind indicated.  I've tried every combination of "Wine setup.exe" I can imagine.  Nothing finds that setup file on the CD.  Any ideas?  Since I'm pretty new at Linux, a more step-by-step approach is appreciated.  Thanks.

---

### Post by SunnyRabbiera on 2009-08-02
Odd, can you open up a file manager and verify?
(go up to places> home in your main menu)

---

### Post by Paddy Landau on 2009-08-02
I'm not sure whether this will help.

Try installing [PlayOnLinux]("http://www.playonlinux.com/"). It's a kind of Wine manager that makes it easy to install, run and uninstall Windows packages.

Then try to install the CD using PlayOnLinux.

---

### Post by j.bell730 on 2009-08-02
This happened to me with The Sims 3, for some reason. I had to go into the CD directory, and click View > Show hidden files. Yes, the files on the CD were hidden, then, I could see all files I needed, and install successfully.

Hope this helps.

---

### Post by StephenG on 2009-08-02
Yes, the file browser shows up and there is a folder for the CD drive (showing: "RS_App") but no files show up there.  Double-click on it -- same result, no files.  I really can't figure out why nothing is showing up -- even if it wouldn't let me execute the file, which I'd understand fully since it's a Windows file.

Tried the hidden files check and the same results -- nothing shows up.  All the Wine and Rosetta Stone searches I've done all tell me to simply fire up Wine, navigate to the "setup.exe" fine on the CD and either double-click or right-click to open with Wine.  Sounds easy.  It isn't.

---

### Post by irv on 2009-08-02
> **StephenG said:**
> Yes, the file browser shows up and there is a folder for the CD drive (showing: "RS_App") but no files show up there.  Double-click on it -- same result, no files.  I really can't figure out why nothing is showing up -- even if it wouldn't let me execute the file, which I'd understand fully since it's a Windows file.

Make sure you are in the CD in your file browser an then go to the View>Show Hidden Files. See screen shot:
[ATTACH]123358[/ATTACH]

---

### Post by irv on 2009-08-02
> **Paddy Landau said:**
> I'm not sure whether this will help.

Try installing [PlayOnLinux]("http://www.playonlinux.com/"). It's a kind of Wine manager that makes it easy to install, run and uninstall Windows packages.

Then try to install the CD using PlayOnLinux.

Thanks for the tip, I like this. I just downloaded and install and it works great.
StephenG did you try this?

---

### Post by StephenG on 2009-08-02
> **irv said:**
> Make sure you are in the CD in your file browser an then go to the View>Show Hidden Files. See screen shot:
[ATTACH]123358[/ATTACH]

Yup -- that's exactly right.  Nothing.

> **irv said:**
> Thanks for the tip, I like this. I just downloaded and install and it works great.
StephenG did you try this?

Are you saying you tried it with Rosetta Stone and it worked?  The site has no mention of the RS program.  Even that begs the question, though, of why Wine is not finding the CD files.  That is, unless I'm so far off base in my abilities that I'm not capable of giving the right commands.  Entirely possible, maybe even likely.

When I do a search for "setup.exe" on the computer, I get no responses.  In terminal, when I type "cd /cdrom" the command line switches to the CD drive but an "ls" command gets nothing.  If I put an audio CD in I get music and I installed Ubuntu on this drive about 2 months ago, so it seems to be working and being recognized by the system.  I can't figure it out.  BTW, I'm using Wine 1.1.26 and RS 3.4.3A

---

### Post by irv on 2009-08-02
> **StephenG said:**
> Are you saying you tried it with Rosetta Stone and it worked?  The site has no mention of the RS program.  Even that begs the question, though, of why Wine is not finding the CD files.  That is, unless I'm so far off base in my abilities that I'm not capable of giving the right commands.  Entirely possible, maybe even likely.
No I didn't try in with Rosetta Stone because I don't have a CD. I just did the install of "playonlinux" and loaded some software off the Internet.
It sounds like your not reading the CD at all. Is it possible you are having a problem with the CD player or the CD itself?

---

### Post by StephenG on 2009-08-02
See my last post.  Just now, I tried the application disc from the other RS box I have -- both the same version, but one box is German and one French.  The version numbers on teh app install disc are identical. Same results -- nothing found on the disc.  Could the drive be bad?  I suppose so, though it's only about 3 or 4 months old, reads audio CDs just fine, and was the drive I used to install Ubuntu on this system when it was new -- 3 or 4 months ago.  I also tried to install the disc on a second (identical except for the brand of CD drive) Ubuntu system.  Same results.  I must have a setting for the CD authorities wrong somewhere on both machines.

---

### Post by irv on 2009-08-03
When I put a CD in my drive it takes a minute or so and the file browser window opens up an shows the content of the disc. If this doesn't happen with your, then you are not mounting the disc in the drive. You can do a manual mount, but it can be setup to do a auto mount. Maybe someone can tell you how to do this. I would look it up, but I am leaving this morning on a trip. 
Good Luck.

---

### Post by StephenG on 2009-08-03
Thank you, Irv, but the drive absolutely sems to be mounting.  If I put in the Ubuntu install disc, everything is fine.  I can browse to my heart's content.  If I put in any disc with windoze files, however, the drive mounts and the browser opens but there are no files there.  Recap:  audio files work fine (app opens and they play), Linux files are there and usable, windoze files are unfindable (with or without hidden files option checked).  I'm running out of ideas.

A week with no ideas?!?  Thanks anyway.

---

### Post by steveneddy on 2009-08-14
Remember that this is FREE SOFTWARE and you are guaranteed no help at all from anyone.

If no one has an idea for you then you have to figure it out yourself.

Try using Google for an answer.

Try help.ubuntu.com

But please don't whine in the forums that no one is helping you. You received a lot of help a week ago.

You may have burned (burnt?) the CD incorrectly (it could happen).

Try burning the info slower (4X or so) and also take that CD to a known good PC and see if the files show up on the other PC.

Maybe it is you that didn't do something correctly. Do your research and figure out what went wrong. Try other forums. But please don't whine about not getting help for your free operating system while installing third party software.

Look at some of the links in my sig to see if they can shed anymore light on your plight.

---

### Post by irv on 2009-08-14
> **StephenG said:**
> A week with no ideas?!?  Thanks anyway.

Stephen G, I have been on vacation for over a week, and just got back. I have run out of options for you because I don't have the same CD's you have. Maybe all the file are hidden and you have to go to the view and un-hide them. I don't know what the answer is? Sorry!

---

### Post by Mark Phelps on 2009-08-14
Don't have access to an RS CD and don't use Wine (have largely found it to be a waste of time) ... but as a test, I inserted an MS Windows application CD to see just what happened ... and ...

The CD icon appears on my desktop along with the CD "label".  Double-clicking the icon opens a Nautilus window showing ALL the files and directories.  Clicking show hidden files in the Nautilus window does nothing with the display -- because, apparently, there are no hidden files. The CD icon also shows up in Places, and once again, clicking that icon opens up a Nautilus window containing all the directories and files.

So, my guess at this point is that RS is distributed as a compressed archive or an MSI self-installer file, neither of which your machine is able to recognize -- or -- there's just plain something wrong with your drive that Ubuntu can't handle.

If you're able to open the CD in an MS Windows machine, have a look at the content and see what's there.  If it's just a bunch or ordinary-looking files and folders, then you've got a problem with your machine that we aren't able to solve for you.

---

### Post by StephenG on 2009-08-14
Thank you, Mr. Phelps and Irv.  Yes, Mr. Phelps, there is both a setup.exe and an .msi file on the CD, but neither one is visible within Ubuntu file browser.  That said, I'm not certain I have Nautilus on this machine, so perhaps I'll try installing it and see what happens.

StevenEddy, you have assumed far too much and I don't appreciate being scolded by you.  I didn't burn any of these CDs -- they came from Rosetta Stone the way they are.  And I have been searching every search engine I have access to for a month now without finding the answer - including the WineHQ and Rosetta Stone sites. And if you had been following along with the rest of the class you would know that I've already tried them on both Ubuntu and Windows machines and the results of those tests.  Nor have I been whining, but rather have been very thankful and fully explained every procedure I've tried.  Obviously something is wrong and that's what is baffling me.  Having stated at the start that I was comfortable with DOS command lines but that Linux was new to me, I'd think you would have a little more understanding rather than talking down to me like such a haughty jackass.  Having had such good luck with responses on these forums in the past, I'll consider you an anomaly and ignore your diatribe from now on.

To all others who had suggestions, thank you.  To anyone who might still have an idea why these files are not appearing, I'll keep checking back for ideas.

---

### Post by Paddy Landau on 2009-08-15
Stephen, correct me if I'm wrong: You only have this problem with Rosetta Stone?

What happens if you put in any other CDs intended for Windows? I have no problems whatsoever reading CDs intended for Windows, but I've never tried Rosetta Stone.

---

### Post by Sidewinder1 on 2009-08-15
StephenG, I've read the entire thread and didn't see any reference to it, perhaps I missed it... When I first installed ubuntu I remember having to install a driver or somesuch that would allow my linux access to view and manipulate files on an NTFS/FAT32 file system (my previous C:\ as I dual boot). Perhaps the Rosetta Stone disks are formated NTFS/FAT32 and you're missing that particular driver? Unfortunately I don't remember the name or description of it. Either a search on your part or perhaps someone more knowlegable than I remembers...Actually, I just looked it up in Synaptic: it's "NTFS-3G.
The above is just a "shot in the dark" / WAG on my part....
Hope it helps and I apologize if you've already tried it...
Side

---

### Post by irv on 2009-08-15
On early versions of Ubuntu there was a problem reading NTFS formated driver or partitions, but with 8.10 and 9.04 I have not had any problems reading them. There is no reason why the files should not show up if you can mount the drive. And it sound like the drive is being mounted when you put in the CD. There is something wrong with the CD itself IMO. Have you tried this CD in other Linux machines? If you know someone who is using something besides Windows, like Linux or OS try it there and this will tell if it is just your machine or if it is the CD itself.

---

### Post by steveneddy on 2009-08-15
[quote}StevenEddy, you have assumed far too much and I don't appreciate being scolded by you.[/quote]

Due to this statement

> **StephenG said:**
> A week with no ideas?!?  Thanks anyway.

that I felt i had to give you a friendly reminder that no one here owes you any help and the fact that you received help with this should show you that someone is looking at your posts.

YOU don't need to take the attitude of "Thanks anyway" as if you are owed a certain amount of help with your very obscure issue that you posted on Ubuntu Forums.

I am not trying to put you in your place or teach you a lesson, just to let you know that since you seem to have a limited amount of experience on this and maybe other forums and that you seem to believe that since there is a forum here that those on the forums owe you support for whatever type of software that you seem to want to install on your free operating system.

I hope that you get this resolved. Really. And when you figure it out, please post the results here so others can benefit from this issue.

Cheers

Um - some Google search results for you to peruse:

[http://www.google.com/search?hl=en&q=rosetta+stone+software+ubuntu&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&q=rosetta+stone+software+ubuntu&aq=f&oq=&aqi=)

[http://ubuntuforums.org/showthread.php?p=7741626](http://ubuntuforums.org/showthread.php?p=7741626)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10043](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10043)

[http://www.nabble.com/Rosetta-Stone-td24944735.html](http://www.nabble.com/Rosetta-Stone-td24944735.html)

[http://www.linuxforums.org/forum/wine/127941-rosetta-stone-wine.html](http://www.linuxforums.org/forum/wine/127941-rosetta-stone-wine.html)

All of these seemed to be the most relevant to what you are trying to accomplish.

I hope that these links help.

Have you tried running Windows in a Virtual Machine and installing Rosetta Stone that way?

I use VirtualBox 3.0 and have XP and Vista installed and I run then through the VM.

It's easier than dual booting and you can use both OS's (Linux and Windows) simultaneously.

---

### Post by irv on 2009-08-16
> **steveneddy said:**
> Have you tried running Windows in a Virtual Machine and installing Rosetta Stone that way?

I use VirtualBox 3.0 and have XP and Vista installed and I run then through the VM.

It's easier than dual booting and you can use both OS's (Linux and Windows) simultaneously.

This is a great idea! I do the same thing and it works great.
On some of your other posts, you came down somewhat hard on this guy. Maybe you should cut him a little slack. I can understand where he is coming from. When you have a problem and can't find the answer, you sometimes say things you shouldn't. Let's just let it slide and focus on his problem. Again this was a great idea.
And yes, if you find the answer elsewhere, don't forget to post the solution here.

---

### Post by jagibbs on 2009-12-28
StevenG, were you ever able to work this problem out using Wine or some other method?  I now have the exact same problem as you did.

I know it's been a few months since this thread ended, but I KNOW there are still going to be people out there running into this same problem with RS

I just bought Rosetta Stone v3 this past week and I'm also trying to get my linux box (xubuntu 9.10) to show me the files on the CD/DVD.  Disk is mounting fine, but I get no listing of files either in Linux itself or within Wine.  I know my drive is working fine, and so is the CD.  I just installed Rosetta Stone on a Windows machine minutes before trying to read the disk on my Linux box.  I thought maybe the disk was burned using a version of UDF that Xubuntu was not supporting out of the box, but it seems I'm up to date through UDF 2.6 the best I can tell.  Perhaps the disk is burned using some proprietary Microsoft version of UDF which is hindering the file reading process?

If anyone has gotten around this please help me out if you can.  I've been Googling for days and my eyes are starting to hurt!  I really don't want to go back to dual boot just for this!

---

### Post by irv on 2009-12-28
Have you tried running VirtualBox 3.0?
[ATTACH]141542[/ATTACH]   [ATTACH]141543[/ATTACH]   [ATTACH]141544[/ATTACH]

---

### Post by sandyd on 2009-12-28
what does
```

sudo fdisk -l
```
while the cd is in the drive give?

---

### Post by jagibbs on 2009-12-28
> **carlee said:**
> what does
```

sudo fdisk -l
```while the cd is in the drive give?

sudo fdisk -l gives me:

jagibbs@LappieSac:/etc$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37437   300712671   83  Linux
/dev/sda2           37438       38913    11855970    5  Extended
/dev/sda5           37438       38913    11855938+  82  Linux swap / Solaris


Hmm.  I thought the disk was being mounted and unmounted since I feel the disk spinning up when mounting and I wasn't getting any errors when mounting or unmounting... perhaps it's not actually being mounted?

I've tried  both of the following lines below in my fstab with similar results:


/dev/scd0       /media/cdrom0   auto ro,users,noauto    0       0

and

/dev/scd0       /media/cdrom0   udf,iso9660 ro,users,noauto    0       0


In addition, doing a sudo fdisk -l /dev/scd0  gives me:

jagibbs@LappieSac:~/Desktop$ sudo fdisk -l /dev/scd0
Note: sector size is 2048 (not 512)

Disk /dev/scd0: 428 MB, 428615680 bytes
255 heads, 63 sectors/track, 13 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x00000000

Disk /dev/scd0 doesn't contain a valid partition table


EDIT....Although after mounting if I enter "mount" on the command line it shows that I have the drive mounted at the bottom of the list, although I don't know why it's calling the device /dev/sr0 instead of /dev/scd0:

jagibbs@LappieSac:/etc$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev)

EDIT EVEN MORE:

I'll add that issuing "mount | grep sr0" returns:

jagibbs@LappieSac:/media/cdrom0$ mount | grep sr0
/dev/sr0 on /media/cdrom0 type iso9660 (ro)

and "mount | grep scd0" does not return anything.

---

### Post by jagibbs on 2009-12-28
> **irv said:**
> Have you tried running VirtualBox 3.0?
[ATTACH]141542[/ATTACH]   [ATTACH]141543[/ATTACH]   [ATTACH]141544[/ATTACH]

I have not tried this approach yet, but other people's sucess with Rosetta Stone under Wine had me hopeful.  I'm not sure what running a virtual box might entail as I have not done this or researched it before, but if that's what it will take.

For the moment, my problem may just be as simple as getting the CD to mount properly (see my previous recent post).  I thought it was mounting, but may not have been.  If it's not mounting I don't know why.  I've been using linux for a good while and have not had mounting issues like this before.  Is there a different mount option if the CD was burned using some strange and twisted Microsoft UDF version?  Looks like the disk is being mounted as iso9660 when I specify "auto" for the fs type in the fstab line..

thanks for the help guys!  I didn't expect responses so quickly!

---

### Post by StephenG on 2009-12-29
Sorry that I dropped the ball on this thread.  After about an hour on the phone with Rosetta Stone CS on more than one occasion and with more than one rep, I am no closer than I ever was to resolving the issue.  They repeated, ad nauseam, that they didn't support Linux.  I repeated nearly as often that I knew that and that I was trying to get it working in a Windows environment, that simply happened to be on a Linux machine.  Explained all about WINE, etc., and no help.  I believe they have some proprietary cloaking something-or-other to prevent piracy.

Yes, the CD drive is absolutely mounting.  Yes, I've tried the discs on other Ubuntu machines, though I have no access to other distributions of Linux than Ubuntu.  Tired other Win CDs on all the Ubuntu machines.  Everything seems to be working properly, except this one program.  I do not have any dual-boot machines -- only one Windows machine, one Mac, and three Ubuntus (all with 9.10).  I haven't tried all the third-party software suggested so far, because frankly I'm still gun-shy about somehow corrupting the OS and I need the machines working -- can't afford much downtime to reinstall everything, etc., if things go "south" on me.  At this point, I have a Win machine that I can use the Rosetta Stone on and am making do with that.

My "Thanks anyway" comment was heartfelt.  It appeared at that time that no one had the answer I needed and I was thanking all for what suggestions had been already made.  I don't engage in sarcasm, so it was  not posted sarcastically.  Again, thanks to all and Happy Holidays.

---

### Post by fromthehill on 2009-12-29
> **StephenG said:**
> Sorry that I dropped the ball on this thread.  After about an hour on the phone with Rosetta Stone CS on more than one occasion and with more than one rep, I am no closer than I ever was to resolving the issue.  They repeated, ad nauseam, that they didn't support Linux.  I repeated nearly as often that I knew that and that I was trying to get it working in a Windows environment, that simply happened to be on a Linux machine.  Explained all about WINE, etc., and no help.  I believe they have some proprietary cloaking something-or-other to prevent piracy.

wine is far from a windows environment
windows programs in wine more often don't work then do and those problems are not are not windows related bugs.
RS is programmed for windows, It's not their fault or responsibility if it doesn't work in wine

---

### Post by irv on 2009-12-30
If you are just trying to read the CD you might try this:
On the windows machine, where you can read the files, just copy them over to a memory stick or a blank CD. do not do a CD copy, just copy the files. Then move them over to the Linux machine and see if you can read them. I have never try this, because I have a machine running both Ubuntu and Vista. I have one partition I use to swap file on both OS's and this works great for things like this. Just for the record, I am not running the software you are having problem with so I don't know if this will work but it is worth a try.

---

