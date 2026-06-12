---
title: "Did the Ubuntu live session corrupt my MBR?"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by New_to_the_game on 2010-09-29
My problem is this

Steps:

4.- I received a cd ubuntu 9.04  Desktop edition.
5.- I read the "cover" that came with the CD.
6.- I elected to "Try Ubuntu" and loaded the cd into the cd drive.

7.- The CD started up and then advised me had to reboot.
8. - I selected the first option - Try Ubuntu.....
9.-  It then asked me for language,  (I guess it loaded into memory) and then into a DOS looking screen advising me to select help to see what commands are available.
10.- I entered reboot.
11.- remove the CD.

12.- system rebooted 
last thing I saw on the screen:
"error loading operating system"

Now:

Placing the Ubuntu CD in the drive, system rebooted, and Linux loaded.

Questions:
- Look at Step 7, was this a normal function of the disk?
- In all probably, my MBR  was damaged or corrupted - how?
- within the CD using the TRY mode, can Linux fix my MBR so
XP starts.
- Do I have to use an XP CD in recovery mode to fix the MBR boot problem.
- Does a later version of Ubuntu  fix or address this problem.

I would like to fix this problem with YOUR tools, so I may show future users that Linux is just as good or better than XP, VISTA, Window7.

---

### Post by spiky001 on 2010-09-29
Hi to fix the mbr you need the windows disc hope this helps [http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/) if not i,m sure we can sort it

---

### Post by Elfy on 2010-09-29
It might be worth finding out exactly what's going on with your system partitions. 

Boot with the livecd - then from Apps - Accessories open a terminal.

Run this command and post the results you get back here.

```
sudo fdisk -l
```

---

### Post by Old *ix Geek on 2010-09-29
> **New_to_the_game said:**
> Last Night I log on to the forum with a "New Thread."  Forgive me please if I do not live, eat or sleep at my computer.  My problem is this (I'll go by steps, as my previous post was not answered quick enough and they closed the thread.That's not why they closed it.
> 4.- I received a cd ubuntu 9.04  Desktop edition.
5.- I read the "cover" that came with the CD.
6.- I elected to "Try Ubuntu" and loaded the cd into the cd drive.

7.- The CD started up and then advised me had to reboot.
8. - I selected the first option - Try Ubuntu.....
9.-  It then asked me for languageUp to here, everything's exactly as it should be.
> and then into a DOS looking screen advising me to select help to see what commands are availableThat's not normal.
> 10.- I entered reboot.
11.- remove the CD.

12.- system rebootedBack to normal, considering what happened in #9.
> last thing I saw on the screen:
"error loading operating system"Has to be a windoze problem, because the "try Ubuntu" option does NOTHING to your hard drive. As someone pointed out in the other thread, even if you inadvertently chose "install" that still wouldn't explain what happened, because it does NOTHING on its own. You have to make selections, such as language, keyboard style, how much disk space you want to allocate to Ubuntu, and so on. If you did any of that, you'd definitely remember. So, assuming you DIDN'T do any of that, Ubuntu simply could not install itself, or do anything else to your hard drive, on its own.
> Placing the Ubuntu CD in the drive, system rebooted, and Linux loaded.Okay, normal again.
> - Look at Step 7, was this a normal function of the disk?Yes, absolutely. That's the whole point of a live CD, i.e., that you can boot from it to try it out.
> - In all probably, my MBR  was damaged or corrupted - how?In 25 years of installing UNIX and Linux, I've never seen this happen due to UNIX or Linux. Windows? Yes.
> - within the CD using the TRY mode, can Linux fix my MBR so XP starts.I don't know, because I don't believe Ubuntu has anything to do with your MBR problem.
> - Do I have to use an XP CD in recovery mode to fix the MBR boot problem.Again, I don't know, but perhaps.
> - Does a later version of Ubuntu  fix or address this problem.There's never been a problem for me--and I started using (K)Ubuntu back at version 5.04. :confused:

---

### Post by snowpine on 2010-09-29
Hi New to the game, the Ubuntu Live CD is a powerful tool, capable of many actions up to and including wiping your entire drive of all data!

You have two courses of action as I see it:

1. Forget about Ubuntu and restore your Windows boot loader. This is best accomplished with your Windows CD.

2. Install Ubuntu as a "dual boot" with Windows. This will install the GRUB bootloader, which will enable you to choose between Windows and Ubuntu at startup. The process of setting up a dual boot is very well documented in the Ubuntu help pages. Also you should use the "Check this CD for errors" option to verify the md5sum of your download/burn; if there are errors on the disk, then all sorts of unexplained phenomenon can occur. I would also encourage you to use the current Ubuntu release (10.04) since all support for the 9.04 release ends Oct. 23, 2010.

---

### Post by Matt__ on 2010-09-29
try this [fix mbr with ubuntu live cd](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by nlsthzn on 2010-09-29
Hello New_to_the_game,

I am well aware of the thread you started and would like to give you two thumbs up for a much better thread... you have included a ton of information that could help to fix the problem... 

Have you tried recovering from the XP disc?  (Worth a shot...)

---

### Post by Old *ix Geek on 2010-09-29
> **snowpine said:**
> the Ubuntu Live CD is a powerful tool, capable of many actions up to and including wiping your entire drive of all data!We're trying to get across to him/her that the live CD can't do ANYTHING to his hard drive without his input. So, yes, the CD *can* wipe out your entire drive **[color="red"]IF YOU TELL IT TO[/color]**. The OP did not do that, so kindly don't scare him.

---

### Post by SaintDanBert on 2010-09-29
[highlight]Moderators[/highlight] **I, too, request that this thread stick around because it sounds a chord that I hear many folks singing.**

> 
For the "Experts" who are looking at this, my last post (thread) was treated very poorly by some members of this community. I asked honest questions and all I got was buckets of scorn. This is no way to treat new members to your community. Shooting down my thread with out letting me reply was and felt like "who needs another user."


**"Expert"** -- An "ex" is a has-been; A "spirt" is a drip under pressure.  Sorry, I could not resist.

I, too, have 30+ years of bit slinging, but I started with linux over ten years ago.  I will gladly try to help you with your trials (sic) of things linux.  Feel free to contact me by private message if you want more intense help.

You mentioned that you had Ubuntu v9.04. You will find that same edition referred to as "jaunty" because each release gets a cute name.
It will reach an end-of-life during October 2010.  I encourage you to download and burn Ubuntu Lucid (v10.04 LTS) and start there.
[ http://iso.linuxquestions.org/ubuntu/ ]( http://iso.linuxquestions.org/ubuntu/ ) [color=orange] Get the DVD.[/color] (I'm sending you to the LinuxQuestions.org site so that you might add them to your linux oriented bookmarks.) 

Notice that I recommended an edition marked "LTS". That means **Long Term Support**. An LTS gets a three-year support commitment as opposed to an 18-month commitment otherwise. Unlike other edition numbers, these numbers have different meaning. Your edition, "v9.04", was turned loose in the wide during the fourth(04) month of the ninth year (2009). You might find this helpful. [ http://en.wikipedia.org/wiki/List_of_Ubuntu_releases ]( http://en.wikipedia.org/wiki/List_of_Ubuntu_releases ).

There is another reason that I recommend Lucid over Jaunty (er, 9.04). A lot of things changed for the better in significant ways between Hardy (v8.04 LTS) and Lucid (v10.04 LTS). Jaunty was one step along the way -- part olde ways, part new ways. My copy of Jaunty works fine for the past 15 months, but required much more tinkering than my out-of-box Lucid required last Spring. Unless there is some spanner in your works, [color=green]You will be happier with Lucid in the long run.[/color]

Once you have the DVD, power-off power-on boot from DVD. (The power cycle makes sure that your hardware is completely reset.) I suggest you connect to wire network initially -- especially during your play time and formal install.

You will see a boot-time menu.  
[list]
[*]**Try it** -- will run things using the DVD as your system drive.  It will be slow (DVD slower than HDD) but after some time you will get to play with Ubuntu Lucid at the desktop. This is a sandbox. You really must work at things to make any changes to your existing drive files and folders.
[*]**Install** -- (also available from the Try-it desktop) will take the steps needed to write Ubuntu onto your system disks.
(The install software is clever enough to see any existing windows or other bootable parts and step around them.)
[/list]

One purpose of the "try it" option enables you to see if your hardware works (well) with this edition. If you have troubles, you might require some extra tinkering during or shortly after your install.

If you are going to install, it is important that you know your workstation hardware. I recommend Belarc Advisor [ http://www.belarc.com/free_download.html ]( http://www.belarc.com/free_download.html ). It is a free windows-based utility that will tell you all of the parts of your workstation in a convenient report.

This much will get you started ... I hope.  I also hope that I was not one of your "experts".

Bonne chance,
~~~ 0;-Dan

_____
**"guru"** -- **G**eneral **U**nderstanding **R**easonably **U**seless.  I couldn't resist this one either.

---

### Post by Saprissa on 2010-09-29
Your first thread...

[http://ubuntuforums.org/showthread.php?t=1584317]("http://ubuntuforums.org/showthread.php?t=1584317")...

was derisive and scornful right out of the gate.

Do you seriously think that YOU introduced yourself to the community with that thread by putting your best foot forward?

It's as if you walk into a party and immediately start complaining that everything from the invitation to the food and drink are sub standard.  Do you expect you would be welcomed and treated warmly if you did that? Nope.  You'd be asked to leave.

If you need help, ask for help.  Omitting the derision and adopting some manners will get you a lot farther.

---

### Post by eriktheblu on 2010-09-29
> - Look at Step 7, was this a normal function of the disk?
Assuming you inserted the disk while running Windows, yes. Ubuntu is a separate operating system, so this function shows you how to get it to run normally.
> - In all probably, my MBR was damaged or corrupted - how?
This is not normal behavior for the live CD unless you direct it to install. The "Try" option should have booted to a graphical interface to demonstrate the features of Ubuntu.
> - within the CD using the TRY mode, can Linux fix my MBR so XP starts.
It might, but probably not in a way that you want. Do a Google search for "fixmbr" to find Windows specific guides.
> - Do I have to use an XP CD in recovery mode to fix the MBR boot problem.
That's probably your best bet.
> - Does a later version of Ubuntu fix or address this problem.
Maybe. Based on your description I would guess that your Ubuntu CD was not behaving normally. This could be due to a corrupt CD (in which case a properly burned CD may fix the problem) or hardware incompatibility (in which case a later version may have better drivers).

Your version will stop being supported next month, so it is advisable to try the current Long Term Support (LTS) version (10.04)

As for the attitudes on your previous post, they are not unheard of in the Linux community. Having performed multiple installs and live CD tests of Ubuntu I have never encountered a situation like you describe. 

Installing Ubuntu *will* overwrite your MBR, where the trial option should not. Most Ubuntu users have have done both and find it difficult to imagine circumstances where a trial session without install can affect the MBR. The logical (but not necessarily correct) conclusion is that you attempted to install. If you did not install, and your MBR still became corrupt, it is quite likely that the problem was caused by something other than running the live session. My next guess is that you attempted to use the Wubi installer from inside Windows

So my advice:
1. Use your Windows recovery disk and fixmbr

2. Download Ubuntu 10.04, check md5sum, burn, then boot from CD

3. Try it out.

---

### Post by snowpine on 2010-09-29
> **Old *ix Geek said:**
> We're trying to get across to him/her that the live CD can't do ANYTHING to his hard drive without his input. So, yes, the CD *can* wipe out your entire drive **[color="red"]IF YOU TELL IT TO[/color]**. The OP did not do that, so kindly don't scare him.

Respectfully, I disagree... my advice to any new user trying Ubuntu is to 1) BACK UP all existing data; 2) CHECK the CD for errors; 3) READ the helpful documentation at ubuntu.com

I am not trying to scare anyone, just being realistic about the risks involved in trying an unfamiliar operating system.

---

### Post by PRC09 on 2010-09-29
In reading your above post specifically #7...at NO point in the TRY UBUNTU  scenario does your system require a REBOOT........UNLESS you decide to Try using WUBI....Then you have this problem.....Maybe....

---

### Post by spiky001 on 2010-09-29
Why dont we help fox his problem so pc is working  again then he can start from the begining. Also to show we do help

---

### Post by Darkness Des on 2010-09-29
I, for some reason, appear to be the only one that thinks this CD behavior is the strangest I've ever heard of. Did you get the ISO from Ubuntu.com? Did you make sure that the CD had no errors after it was burned?

---

### Post by Calash on 2010-09-29
> **Darkness Des said:**
> I, for some reason, appear to be the only one that thinks this CD behavior is the strangest I've ever heard of. Did you get the ISO from Ubuntu.com? Did you make sure that the CD had no errors after it was burned?

It depends on when he put the CD into the drive.  If this was while in Windows I believe it loads up and offers a Wubi install, reboot, or install some Open Source applications.

If this was a bootup from the disk then yes it is the strangest problem I have every read about.

---

### Post by philinux on 2010-09-29
Sounds like a wubi instal gone wrong maybe.

---

### Post by LowSky on 2010-09-29
> **philinux said:**
> Sounds like a wubi instal gone wrong maybe.

I'm with Phil

---

### Post by Rubi1200 on 2010-09-29
@New_to_the_game 			 		

use the LiveCD, but this time try either a newer version such as 10.04, or even an alternative live distro such as Knoppix and post the results of the bootscript linked at the bottom of my post.

The results will show conclusively if Windows is still on your drive and whether or not, even accidentally, you installed Ubuntu to the drive rather than try it.

Thanks.

---

### Post by philinux on 2010-09-29
Without the output of bootinfoscript ot at least 

sudo fdisk -l

We are very much in the dark.

---

### Post by Old *ix Geek on 2010-09-29
> **PRC09 said:**
> In reading your above post specifically #7...at NO point in the TRY UBUNTU  scenario does your system require a REBOOTOh yes it does. According to Ubuntu's own documentation:
> Ubuntu can be installed with the graphical CD. Make sure that your computer is set to boot from a CD before a hard drive.

   1. Insert the Ubuntu disc into your CD drive.
   2. **[color="red"]Start or restart your computer.[/color]**
[**[color="blue"]Source[/color]**](https://help.ubuntu.com/community/GraphicalInstall)

and:
> When installing or trying the LiveCD version of Ubuntu from a CD, your computer has to be able to boot from that CD. Usually this consists of just **[color="red"]inserting the disk into your CD/DVD drive and rebooting your computer[/color]**.
[**[color="blue"]Source[/color]**](https://help.ubuntu.com/community/BootFromCD)

---

### Post by Darkness Des on 2010-09-29
Well, yes, but that means power on the computer long enough to insert the disc, power it off, then boot off of the disc. If you already booted from it, you shouldn't have to reboot until after you're done with it. In this case, attempting to use it told him to reboot.

---

### Post by New_to_the_game on 2010-09-29
Hello Everyone:

First I would like to say thankyou for your comments and helpful suggestions.  My inital "Thread" was written in a low key "what the hell just happened."  

The thread addressed my frustations, and looking for answers.  The initial scope is something you would expect from a newbe, who trusts something and get something else.

Since my MBR was corrupted, I would hazzard a guess installing a dual boot - XP and Linux would only (or could) create a bigger problem with the MBR.

[SIZE=4]**I have fixed my MBR with a WIN XP disk - it was simple enough. In **[/SIZE]

In all my years I had only one Windows computer that had a failed MBR, and that was a laptop that was dropped while booting up.

I am not by the "problem machine" as I write this, but I will rerun the "Try It" process again and again. (Since I cloned this drive, I can sacrifice it as I get use to Linux.)

[SIZE=3][COLOR=Red]*If I can duplicate the problem, it can be fixed. It is no longer necessary to keep this thread open.*[/COLOR][/SIZE]

As I can not tell you what happened to "kill" the MBR, I will play with the Disk and retry the option(s) several times.  In the end, maybe it was a quirk - that just happened. At least I held off hoping there was a linux fix (but, [SIZE=2]*if linux did not cause the problem, how can one expect it to fix it.*[/SIZE])

Thank you all, good to know I am in the company of great helpers.:popcorn:

---

### Post by philinux on 2010-09-29
Mark the thread as Solved with the Thread tools pull down menu. We only close threads that breach the forum codes of conduct.

Glad you're sorted.

---

### Post by New_to_the_game on 2010-10-02
[SIZE=2][SIZE=4][B]Post Morten (not really that serious)
[/B][/SIZE]
    1.- Upon examination of the problem hard drive
        - I loaded Win xp SP3 boot disk into the recovery mode:  I ran checkdsk /r and fixmbr  (which did not work.

    2.- I installed a good mirrored HD of the above and booted up.
        
    3.- Using Acronis Disk Director I:
        [/SIZE][SIZE=2]- I examined the problem HD and discovered two things:
          First I had a hidden partition, I did not know about and Acronis could not figure it out. Second, the boot drive was no longer a primary drive.
[/SIZE]
[SIZE=2]        - deleted the hidden partition, and incorporated in the boot partition.
        - reset the boot partition as the primary partition.

    4.- Removed the Mirrored Drive and hooked up the problem drive
        and all is well. Since this problem occurred after running Ubuntu,
        (and I may have assumed wrong) I blamed Ubuntu.


    5.- What happened to Ubuntu 9.04?
        Okay, while running windows (XP SP3) I loaded the disk, and was given the options to run Ubuntu.*

    6.- I selected cancel, and explored the Ubuntu disk. At this point I can not tell you what happened. After reading numerous reply's to the forum, It was impossible to determine if I "flipped a switch.

    7.- I rebooted XP with the Ubuntu disk in place. Ubuntu 9.04 came up as described (in a graphics mode similar as a window enviroment.) :)

  --- Since I can not duplicate the "error or conditions that prompted my posting to this forum" my question is just one: ***When Ubuntu loaded, it  only came up in a "DOS Screen mode***"** (white text on a black background.)  If my **hard drive was screwed up** and I booted to Ubuntu - would I not have gotten the graphical interface?  I tried booting several times.... same thing (just a dos text screen.):confused:

* For the creators, a suggestion - loading the disk in a windows environment and wanting to try it "in the BOOT mode" make the text in the dialog box really stand out for us blind users what to do for the try mode.

** The software loaded and I could type "HELP" and it gave me a list of commands and the commands worked. (This was sort of being in a terminal window)

Now, that I see what happens in the try mode, and my hard drive is "Stable." I am going to try and install this version 9.04 (as a dual boot) on my hard drive.
I do have one question- I see a later version is coming out this month -
is upgrading Ubuntu - an easy task?
[/SIZE]

---

### Post by snowpine on 2010-10-02
> **New_to_the_game said:**
> I am going to try and install this version 9.04 (as a dual boot) on my hard drive.
I do have one question- I see a later version is coming out this month -
is upgrading Ubuntu - an easy task?

Great! My only advice is, support for 9.04 ends this month, so I would recommend 10.04, the current stable release.

Upgrading Ubuntu is easy, check it out: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by New_to_the_game on 2010-10-04
Hello all:

I went ahead an installed Ubuntu 9.04 in a 10 gig partition., for a dual boot.

As pointed out to me, my version support will end shortly.

Looking at the Upgrade notes, I do not see an upgrade from
my version 9.04 to the latest version 10.04.

As I see it, I must upgrade to 9.10 first, then to 10.04

Can some one confirm this for me?

An so I will have another new experience with (Ubuntu) Linux.

---

### Post by snowpine on 2010-10-04
> **New_to_the_game said:**
> Looking at the Upgrade notes, I do not see an upgrade from
my version 9.04 to the latest version 10.04.

As I see it, I must upgrade to 9.10 first, then to 10.04

Can some one confirm this for me?

You are correct. :)

---

