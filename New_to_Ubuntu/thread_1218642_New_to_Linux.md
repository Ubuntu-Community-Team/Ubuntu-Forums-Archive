---
title: "New to Linux"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by .Zero. on 2009-07-20
I'm now to linux and am currently using Windows XP. Planning on Migrating to Elive. I have two old versions of Ubuntu, ver 7.04 and 7.10. Live runs very well for me, and 7.04 seems ko work better for me as it automatically recognizes my ADSL connection, so will i have this problem with new versions or other distos? I have a few question though.

1. How to install application on Linux?
2. Does installing mean it will format my other partitioned half of HD as well?
3. Need to use Visual Basic, can i use it with WINE, or an alternative?
4. Do heavy programs work with windows emulation tools?
5. will i have multimedia trouble like playing DVDs, playing MP3, MP4. 
6. Anyway, i can migrate my windows programs to Linux?

---

### Post by utnubuuser on 2009-07-20
If Windows programs are important to you, keep Windows.  You can find all the answers to your questions through Google as they've been answered many times over.

Dual booting means having Ubuntu and Windows/Mac or whatever on the same computers. - Dual-booting is easy to accomplish. (Novice level).
> [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by Garrovick on 2009-07-20
My theory is that if one wants to do Ubuntu, forget Windows. Put all thoughts of running Windows programs with Ubuntu out of the realm of possibility.

Use one or the other...

---

### Post by jeppewinther on 2009-07-20
There are a great many windows programs that can run under linux using wine. But I would suggest you look into finding alternative native linux programs, and see if you can cover what you need.

While WINE isnt and emulator, and as such doesnt incur a performance penalty, it can still be a slight hassle and lead to some less than optimal behaviour. Not to worry, very much nearly everything can be done using Linux programs these days, so unless youre dead set on not changing you ways, I am sure you can work it out.

As to your questions:

1) Most programs are installed using the Add/Remove programs menu, which is a very simple Search, point and click install interface. There is stuff that will require more advanced methods, but you can most likely get on fine without bothering with that whatsoever.

2) Depends what you mean. If by your other HDs you mean the ones you keep your Data on, IE. not a bootable drive, then you dont have to at all. Linux supports all Filesystems Windows does, and quite well at that.
If by your other HDs with Windows installed on it, then you dont have to worry about that either. GRUB will let you pick and choose what to boot when you start up the computer.

3) I am not familiar with Visual Basic, so I dont know. A quick google revealed:
[http://ubuntuforums.org/showthread.php?t=112218](http://ubuntuforums.org/showthread.php?t=112218)
[http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html)
[http://appdb.winehq.org/appview.php?appId=94](http://appdb.winehq.org/appview.php?appId=94)

4) Maybe. But most have equivalents that run Natively. Check

5) No. Less so than with Windows, probably.

6) Maybe. But you will be happier if you give up on wanting all your old Windows goodies and try the treats Linux has to offer instead. It can be different, but if it isnt better then it certainly isnt worse.

---

### Post by credobyte on 2009-07-20
1. How to install application on Linux?
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

2. Does installing mean it will format my other partitioned half of HD as well?
[COLOR=Blue]Partition layout can be modified .. choice is up to you.[/COLOR]

3. Need to use Visual Basic, can i use it with WINE, or an alternative?
[COLOR=Blue]Don't know .. easier would be to use VB ( VirtualBox ).[/COLOR]

4. Do heavy programs work with windows emulation tools?
[COLOR=Blue]Depends on your PC specs ( RAM ).[/COLOR]

5. will i have multimedia trouble like playing DVDs, playing MP3, MP4. 
[COLOR=Blue]*[COLOR=Navy]ubuntu-restricted-extras[/COLOR]* and *all* your multimedia problems will be solved.[/COLOR]

6. Anyway, i can migrate my windows programs to Linux?
[COLOR=Blue]You can't migrate them to Linux .. you can only replace them with other alternatives or emulate them via Wine ( or as previously said, use VirtualBox ).[/COLOR]

---

### Post by SunnyRabbiera on 2009-07-20
> **.Zero. said:**
> I'm now to linux and am currently using Windows XP. Planning on Migrating to Elive. I have two old versions of Ubuntu, ver 7.04 and 7.10. Live runs very well for me, and 7.04 seems ko work better for me as it automatically recognizes my ADSL connection, so will i have this problem with new versions or other distos?

7.04 and 7.10 are no longer supported, try Hardy 8.04 to begin with.

> 1. How to install application on Linux?
On Ubuntu look no farther then here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

> 2. Does installing mean it will format my other partitioned half of HD as well?
Ubuntu will detect any partitions you have and adjust itself to take up any unsused space.
Just make sure to compact your filespace on windows and defrag first.

> 3. Need to use Visual Basic, can i use it with WINE, or an alternative?

Mono might help with this one, or Gambas.
For most though linux is not ideal for VB, blame that on microsoft and their anti competitive nature.

> 4. Do heavy programs work with windows emulation tools?
Possibly, Wine can be a little flaky though.

> 5. will i have multimedia trouble like playing DVDs, playing MP3, MP4. 

Not really but you will have to install codecs for MP3/MP4 playback and libdvdcss and stuff.
Legally Ubuntu cannot provide these codecs on a fresh install but the codecs are easy enough to install.

> 6. Anyway, i can migrate my windows programs to Linux?
Depends on what you need, but for practically every windows software there is a linux alternative, most of them as good or better then their windows counterparts.

---

### Post by cptr13 on 2009-07-20
*sigh* you're going to get the whole range of opinions now.  Pure linux, dual boot, or no linux are all viable options depending on your circumstances.


1. How to install application on Linux?
You can install apps through the distros package manager.  Most distros have a GUI package manager but you can always install through terminal as well.  Package managers vary distro to distro, your distro's documentation should have good documentation on using the package manager

2. Does installing mean it will format my other partitioned half of HD as well?  
You can install however you want, whether it's on a partition or the entire hard drive.  Just make sure you are careful during the install process so as not to install over your windows partition.  I strongly reccomend the WUBI installer for completely new users, though if you've used Ubuntu previously...probably isn't necessary for you.

3. Need to use Visual Basic, can i use it with WINE, or an alternative?
Don't know..sorry.  There's an app database for wine though that lists programs and how well they work under wine.  [http://appdb.winehq.org/](http://appdb.winehq.org/)

4. Do heavy programs work with windows emulation tools?
Don't know...sorry.

5. will i have multimedia trouble like playing DVDs, playing MP3, MP4.
As far as I know, you can get these working under any distro with the right knowhow.  However, not every distro provides out of the box support for restricted formats such as these.  Linux mint has it as well as PCLinuxOS.  The major distros do not (Ubuntu, SUSE, Fedora, Debian) but you can find a howto fairly easily via the forums or google.  It's not that tough, generally installing a handful of packages for the codec support.

6. Anyway, i can migrate my windows programs to Linux? 
If you dual boot, you can access your windows partitions from within linux.  I'm not sure about "migrating" beyond that.  I know Ubuntu will import your wallpaper and email (I think) during a fresh install.  

Out of curiousity...why Elive?  That has the enlightenment window manager...not something I'd recommend for a linux newbie. Why not stick with Ubuntu if you've already used it?  It is definately the most newbie friendly distro (in my opinion)

---

### Post by .Zero. on 2009-07-20
Thanks guys, so if i install Ubuntu 9.04 then i will have no problems with my internet connection and it will automatically get detected like in 7.04, right?

And the about the partition, i plan to removing my Windows completely. My HD is partitioned in C and D. C is where my Windows resides and D is where i have all my documents. So my main concern is, C and D being one Physical Drive, that my D will get formatted as well. I have no problems with my C drive getting formatted but i can not afford to lose my documents on D.

---

### Post by raymondh on 2009-07-20
> **.Zero. said:**
> I'm now to linux and am currently using Windows XP. Planning on Migrating to Elive. I have two old versions of Ubuntu, ver 7.04 and 7.10. Live runs very well for me, and 7.04 seems ko work better for me as it automatically recognizes my ADSL connection, so will i have this problem with new versions or other distos? I have a few question though.

1. How to install application on Linux?
2. Does installing mean it will format my other partitioned half of HD as well?
3. Need to use Visual Basic, can i use it with WINE, or an alternative?
4. Do heavy programs work with windows emulation tools?
5. will i have multimedia trouble like playing DVDs, playing MP3, MP4. 
6. Anyway, i can migrate my windows programs to Linux?


Hello .Zero and welcome,

[Psychocats]("http://www.psychocats.net/ubuntu/index") has got a good site/blog...lots of information.  So is the [Ubuntu pocket guide]("http://www.ubuntupocketguide.com/index_main.html")  which contains great tutorials to get you acquainted (again) with Ubuntu.

You may install Ubuntu side-by-side with windows (each OS in their respective partitions).  One option in the installation process is called GUIDED RESIZE which allows you to grab a slider (looks like hash marks) and slide left or right to allocate partition sizes as you decided.  If you are comfortable with partitioning, you may even create partition prior to installation and just choose MANUAL during the process. 

Lastly, there is the [WUBI]("https://wiki.ubuntu.com/WubiGuide")-install ... which is Ubuntu inside windows ... though I personally prefer to create a partition for Ubuntu.  

Nevertheless, it's your choice.

Reading materials for you with regards to partitioning and installation:

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Here is a link on windows-equivalent programs for linux.

[https://help.ubuntu.com/9.04/switching/applications-equivalents.html](https://help.ubuntu.com/9.04/switching/applications-equivalents.html)
[http://www.linuxalt.com/](http://www.linuxalt.com/)

I personally prefer virtualization and use [virtualbox]("http://www.virtualbox.org/") (XP).

Do read up and research .... and do post back if you need clarifications or assistance. 

Good luck.

---

### Post by raymondh on 2009-07-20
> **.Zero. said:**
> Thanks guys, so if i install Ubuntu 9.04 then i will have no problems with my internet connection and it will automatically get detected like in 7.04, right?

And the about the partition, i plan to removing my Windows completely. My HD is partitioned in C and D. C is where my Windows resides and D is where i have all my documents. So my main concern is, C and D being one Physical Drive, that my D will get formatted as well. I have no problems with my C drive getting formatted but i can not afford to lose my documents on D.

Zero,

Try the liveCD first and see how it plays/reacts to your system specs.

EDIT:  Why not dual boot ... that way you keep your windows until you're ready to migrate completely.  Nevertheless, if you plan to sole-boot, you can point the installer to a specific partition hence avoiding your D:drive.

---

### Post by SunnyRabbiera on 2009-07-20
> **.Zero. said:**
> Thanks guys, so if i install Ubuntu 9.04 then i will have no problems with my internet connection and it will automatically get detected like in 7.04, right?
Newer versions usually have better wireless support.
But i would use 8.04 over 9.04 personally because even though 8.04 doesn't have all the "latest and greatest" software its more stable and if you have a intel graphics card 9.04 might suck as 9.04 has major regressions for intel graphics cards.

---

### Post by .Zero. on 2009-07-20
darn, i have an intel 82945G graphics card. So, i'm better of with 8.04? Does it have any major flaws, cuz it would be better to use a new version i guess.

---

### Post by .Zero. on 2009-07-20
> **raymondhenson said:**
> Zero,

Try the liveCD first and see how it plays/reacts to your system specs.

EDIT:  Why not dual boot ... that way you keep your windows until you're ready to migrate completely.  Nevertheless, if you plan to sole-boot, you can point the installer to a specific partition hence avoiding your D:drive.

i would but i live in a remote country where i have to download via torrents and have a crappy connection, so I just have to take chances.

---

### Post by SunnyRabbiera on 2009-07-20
> **.Zero. said:**
> damn, i have an intel 82945G graphics card. So, i'm better of with 8.04? Does it have any major flaws, cuz it would be better to use a new version i guess.

No sometimes latest doesnt always mean greatest.
But Ubuntu 8.04 is nice and stable, 8.04 is good enough to keep in my opinion.
Keep in mind though that you can try 9.04, I just found it too slow to use on a daily basis and thats even without desktop effects.
You may also want to try other distros if Ubuntu doesnt work out, right now I am on OpenSuse for a bit, its alright though it has some little glitches of its own.
No linux distro is perfect, its all about finding the one for you.
Ubuntu is one of the better distros out there though, and downloading most distros are free to download and try out.
The only cost is the CD
Its just a matter of trying things out, experimentation is a good way to learn linux.

---

### Post by stalkier on 2009-07-20
> **raymondhenson said:**
> Zero,

Try the liveCD first and see how it plays/reacts to your system specs.

EDIT:  Why not dual boot ... that way you keep your windows until you're ready to migrate completely.  Nevertheless, if you plan to sole-boot, you can point the installer to a specific partition hence avoiding your D:drive.

+1 on dual-boot. Dual-booting can be a MAJOR advantage to a noob. I dual-booted forever. Still do on one desktop. I run 9.04 solely on a laptop and another desktop. I have NO problems at all.

---

### Post by afroman10496 on 2009-07-20
If you do install Ubuntu, you'll love it- get VirtualBox OSE in the repos. Check this out. In picture one that I attatched, you see the worst OS ever in a Window. Cool, but not totally cool. How about picture two?
(I did not use GIMP! It is called Seamless mode, and you have to get Guest Additions.):)

---

### Post by SunnyRabbiera on 2009-07-20
> **Afroman10496 said:**
> If you do install Ubuntu, you'll love it- get VirtualBox OSE in the repos. Check this out. In picture one that I attatched, you see the worst OS ever in a Window. Cool, but not totally cool. How about picture two?
(I did not use GIMP! It is called Seamless mode, and you have to get Guest Additions.):)

I dont see anything.
Anyhow on the install issue just make sure to back up if possible.
I actually suggest getting a external hard drive in the near future.

---

### Post by .Zero. on 2009-07-20
I would dual boot but i have a problem regarding space. Ok, I have two HDs. One 80Gb, the other 160GB. My 80Gb is partitioned into 40 40. I can only afford to format my C drive. all the other drive D and E, contain documents that i can not erase and sadly i do not own a backup drive.

---

### Post by afroman10496 on 2009-07-20
Sorry- I sorta forgot. Now here it is.:D

---

### Post by SunnyRabbiera on 2009-07-20
> **.Zero. said:**
> I would dual boot but i have a problem regarding space. Ok, I have two HDs. One 80Gb, the other 160GB. My 80Gb is partitioned into 40 40. I can only afford to format my C drive. all the other drive D and E, contain documents that i can not erase and sadly i do not own a backup drive.

Well its best to proably install linux on where your lowest amount of space is.
But backup is a good idea, if you cant afford a external drive get a stack of CD's or DVD's
If you have DVD burning capability use it

> **Afroman10496 said:**
> Sorry- I sorta forgot. Now here it is.:D

Nevemind I see it there now.

---

### Post by .Zero. on 2009-07-20
Yes, DVD burning is what i'm planning to do, but i still don't want to dual boot. I want to completely migrate, cuz Windows sucks with it's errors and viruses. And Linux is faster and more stable too. Let's see how it works out.

---

### Post by halovivek on 2009-07-21
I thought that Windows is the only OS to use fine. But i got frustrated with that once i stuck with virus and spyware. But once i started to use Linux and now i addicted to it.

---

### Post by afroman10496 on 2009-07-21
> **halovivek said:**
> I thought that Windows is the only OS to use fine. But i got frustrated with that once i stuck with virus and spyware. But once i started to use Linux and now i addicted to it.
I know, me too. Micro$oft tricks everyone into thinking every computer runs windows.

---

### Post by credobyte on 2009-07-21
> **Afroman10496 said:**
> I know, me too. Micro$oft tricks everyone into thinking every computer runs windows.

Because 90% ( +/- ) of new PC's come with Windows pre-installed ( which obviously ends up in a fact that MS is the one and only "reliable" OS ).

---

### Post by afroman10496 on 2009-07-21
> **credobyte said:**
> Because 90% ( +/- ) of new PC's come with Windows pre-installed ( which obviously ends up in a fact that MS is the one and only "reliable" OS ).
Also, that's sorta bad for Micro$oft because once they discover the Mac, they might see that everything is better than Windows, and then they will find the best- Ubuntu!:D

---

### Post by credobyte on 2009-07-21
> **Afroman10496 said:**
> Also, that's sorta bad for Micro$oft because once they discover the Mac, they might see that everything is better than Windows, and then they will find the best- Ubuntu!:D

It's not that easy to break stereotypes :roll:

---

### Post by oldrocker99 on 2009-07-21
> **.Zero. said:**
> Thanks guys, so if i install Ubuntu 9.04 then i will have no problems with my internet connection and it will automatically get detected like in 7.04, right?

And the about the partition, i plan to removing my Windows completely. My HD is partitioned in C and D. C is where my Windows resides and D is where i have all my documents. So my main concern is, C and D being one Physical Drive, that my D will get formatted as well. I have no problems with my C drive getting formatted but i can not afford to lose my documents on D.

A note here: If you have an ATI video card, you are better off (at present) installing Intrepid Ibex (8.10) as the no-longer-to-be-updated drivers for a lot of ATI chips are currently incompatible with 9.04. The current state of the open-source drivers is a lot better than it was a year or so ago but doesn't compare with the 9.03 ATI drivers at present.

I've returned to 8.10 with the 9.03 drivers, and it's MUCH better and  faster (and I can play Neverwinter Nights:)) than the open-source drivers on 9.04.

If you have nVidia, you probably won't have any problems. You certainly won't have the problems I have on my SIX MONTH-OLD Toshiba laptop...](*,)  

Just sayin'''

:guitar:

---

### Post by .Zero. on 2009-07-21
Ok, i'm downloading both, Ubuntu 9.04 Jaunty Jackalope and Ubuntu 8.04 Hardy Heron. I'll try the Live CD and which ever works best, i'll install.

---

### Post by RedRat on 2009-07-21
> **.Zero. said:**
> Ok, i'm downloading both, Ubuntu 9.04 Jaunty Jackalope and Ubuntu 8.04 Hardy Heron. I'll try the Live CD and which ever works best, i'll install.

for a newbie, I would strongly suggest that you start out with 8.04 LTS (long term support). I fear, from observing many comments here and in the newsgroups, that you stand a high chance of problems, particularly graphic problems. Get your feet wet with 8.04 and then when the next LTS version of Ubuntu comes out, then move to that. 

Unless you are very comfortable with the command line and some obtuse suggestions for correcting problems, you will spend a lot of frustrating time trying to get these other versions up and running smoothly. Concentrate on trying to understand the Linux system then move on. Better to do that with a stable release. 

You will hear the refrain that Linux isn't Windows constantly both here and in other places. It is true and we all bring some bad habits with us from the Windows world. Some things will seem odd to you, but play around and be patient. You will become a confirmed Linux user. It is really rather painful for me to have to go back to Windows every now and then.

---

### Post by .Zero. on 2009-07-23
heyy, i downloaded Ubuntu and it's running fine on the Live CD. I have no problems and my internet connection works pretty well with my internet without any configuration. yay! I love this version of Linux and am happy with it. I have not installed it yet because of what the CD autorun said on windows. 

It said that i could install Ubuntu inside windows without a dedicated partition. What does this mean? Does this mean that I can have Ubuntu and Windows on the same partion on my HD, without my windows files being affected? Can i dual boot this way? If Windows and Ubuntu can both operate on my C: Drive then am i fine with dual boot.

---

### Post by SunnyRabbiera on 2009-07-23
> **.Zero. said:**
> heyy, i downloaded Ubuntu and it's running fine on the Live CD. I have no problems and my internet connection works pretty well with my internet without any configuration. yay! I love this version of Linux and am happy with it. I have not installed it yet because of what the CD autorun said on windows. 

It said that i could install Ubuntu inside windows without a dedicated partition. What does this mean? Does this mean that I can have Ubuntu and Windows on the same partion on my HD, without my windows files being affected? Can i dual boot this way? If Windows and Ubuntu can both operate on my C: Drive then am i fine with dual boot.

Yes there is something called Wubi.
Wubi installs Ubuntu inside of Windows, its handy for those who are afraid of dual booting.
But I will mention that people have had issues with Wubi, I think its worth a shot personally but its up to you if you want to do a dual boot, use wubi or erase Windows entirely.
You said earlier you wanted to wipe windows so Wubi is sort of meaningless.

---

### Post by .Zero. on 2009-07-23
I did, but as it said that it could survive on the same partition that windows is on, i thought i'd give it a try. Because, I can not format my other drives and the only drive that i can take a chance with is Drive C. A far a dual boot is concerned, I believe that the two operating systems have to be on seperate partitiones/drives. But i can run both on one partition, then i'd go for it. So, Will Ubuntu run on the same drive as Windows?

---

### Post by enri2 on 2009-07-23
visual basic is owned by microsoft so no.


 you can use real basic , but it costs money and there is a free version too

---

### Post by jrothwell97 on 2009-07-23
> **enri2 said:**
> visual basic is owned by microsoft so no.


 you can use real basic , but it costs money and there is a free version too
But Visual Basic is so far detached from 'classic' BASIC (which is what Real Basic is) that if you want to program in Visual Basic, you *really* need Windows to do it.

---

### Post by .Zero. on 2009-07-23
so i guess i have no option but to dual boot.

---

### Post by .Zero. on 2009-07-23
Ubuntu installed and running great. Wohoo. Love this. But i could not get rid of Windows, so it is still there. Does anyone know how to put Ubuntu as the default OS. I mean, when i open my PC, the OS selection will be on Windows Automatically, i want it to be on Ubuntu so that I don't have to be there when the pc boots.

---

### Post by raymondh on 2009-07-23
Am assuming you installed thru WUBI (as you have posted).  From the [wubi guide]("https://wiki.ubuntu.com/WubiGuide%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0%C2%A0#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?") itself, you'll have to edit the windows bootloader files.

---

### Post by afroman10496 on 2009-07-23
> **.Zero. said:**
> Ubuntu installed and running great. Wohoo. Love this. But i could not get rid of Windows, so it is still there. Does anyone know how to put Ubuntu as the default OS. I mean, when i open my PC, the OS selection will be on Windows Automatically, i want it to be on Ubuntu so that I don't have to be there when the pc boots.
I think you should do a clean install to have it by default. Back up your data and burn a live cd, boot your pc with the cd in it, and select "Guided" when it comes to disk portioning. Hope it helps:D

---

### Post by .Zero. on 2009-07-23
another question. Where do all the installed programes go. I installed Songbird, i closed it and I can't seem to get it back up again. Help.

---

### Post by mudcat on 2009-07-23
Easiest way to change the default OS at grub is to use the startup-manager (System>Admin>Startup-manager)

---

### Post by raymondh on 2009-07-23
@ .Zero

Congratulations on having your ubuntu installed.

Just 2 tips .... it's often better for you to start a new thread when you have a new issue to discuss. Also, when posting a new thread, kindly indicate in your post if it is a WUBI-install as some workarounds are WUBI-specific (i.e. "how to make ubuntu default" as an example)

As for songbird, look at applications > sound & video.  Or, press ALT + F2 and type songbird to run it.



@ mudcat

Assuming that OP does have a WUBI-install (of which we still do not know until he says so).... A wubi install uses the windows bootloader first and will only use GRUB after choosing Ubuntu. From the [wubi guide]("https://wiki.ubuntu.com/WubiGuide"):

*Ubuntu is not installed as the default boot option, you have to select it in the windows boot menu. To change that, in windows XP go to control_panel > system > advanced > startup_and_recovery and edit the "Default Operating System", if you want you can change the timeout as well.*

Now, if OP does have a separate-partition-dual-boot, then SUM is a good GUI to use.

---

