---
title: "the most basic question possible"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by stickman51 on 2008-12-11
Sorry, folks, I'm lower on the totem pole than a beginner. Ran out and bought another laptop, strictly for Ubuntu; it has Windows Vista Home BASIC.

I downloaded Ubuntu 8.10 to a different laptop (the new one is not online yet) and as soon as it was done downloading, it told me to insert a blank CD. It then burned a CD. Nothing was left on my desktop. Now, all I need to do is stick that CD into the new laptop, right? On the CD, I see this:
folders:
    .disk
     casper
     dists
     install
     isolinux
     pics
     pool
     preseed
files:
     autorun.inf
     md5sum.txt
     README.diskdef...
     ubuntu
     umenu.exe
     wubi.exe
And I suppose the autorun will install Ubuntu so that when I boot up, I get a choice between the 2 Operating Systems.

Is that all there is to it? That just seems too easy.

---

### Post by 73ckn797 on 2008-12-11
If you downloaded the "iso" file then all you have to do, to begin, is to boot the computer with the burned disk and follow the instructions.

---

### Post by OutOfReach on 2008-12-11
You need to reboot (with the CD in the CD Drive) and it will allow you to boot into the LiveCD and if you like Ubuntu you can install it from there.

---

### Post by BwackNinja on 2008-12-11
The autorun does not install ubuntu. To install, you need to reboot your computer with the CD in the drive. It will then prompt you to either 'try ubuntu without making any changes to your computer' or 'install ubuntu.' The only part of the installer you may have trouble with is the partitioner, though the guided install may be all you need. 

Don't hesistate to ask any more questions :)

EDIT: LOL, third, not even second XD

---

### Post by linux phreak on 2008-12-11
Burn the CD as an image not data.Then boot from the CD.This setting can be changed in the BIOS.

---

### Post by earthpigg on 2008-12-11
everything everyone else has stated is correct.

in addition, the _only_ time an ubuntu install can even be slightly complicated is if you want to dual boot.

---

### Post by Dr Small on 2008-12-11
> **earthpigg said:**
> everything everyone else has stated is correct.

in addition, the _only_ time an ubuntu install can even be slightly complicated is if you want to dual boot.
and even that isn't that complicated, if you read the installer.

---

### Post by 73ckn797 on 2008-12-11
Is there an echo in this thread?__________:lolflag:

---

### Post by jay576 on 2008-12-11
didn't ubuntu allow installations from with windows now so you dont even have to reboot.  i thought it was an option last time i had a disk in while using windows

---

### Post by Dr Small on 2008-12-11
> **73ckn797 said:**
> Is there an echo in this thread?__________:lolflag:
No. Actually, it's located at /bin/echo :D

---

### Post by anewguy on 2008-12-12
> **Dr Small said:**
> No. Actually, it's located at /bin/echo :D

I can't seem to find that directory....I can't seem to find that directory....I can't seem to find that directory....I can't seem to find that directory....I can't seem...

I loved your reply! :lolflag:

---

### Post by 73ckn797 on 2008-12-12
> **Dr Small said:**
> No. Actually, it's located at /bin/echo :D

[SIZE=7]I created that directory...[SIZE=6]directory...[SIZE=5]directory...[SIZE=4]directory...[SIZE=3]directory...[SIZE=2]directory...[SIZE=1]directory![/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by howlingmadhowie on 2008-12-12
> **73ckn797 said:**
> [SIZE=7]I created that directory...[SIZE=6]directory...[SIZE=5]directory...[SIZE=4]directory...[SIZE=3]directory...[SIZE=2]directory...[SIZE=1]directory![/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

or mayber at /usr/bin/banner ?

btw, the live cd is very slow. don't worry! if you install it, ubuntu will run fast :) it's just that cd-drives are a lot slower than hard-drives.

---

### Post by stickman51 on 2008-12-12
> **linux phreak said:**
> Burn the CD as an image not data.Then boot from the CD.This setting can be changed in the BIOS.

THANKS for all those answers. I did download the .iso file ( "ubuntu-8.10-desktop-i386.iso") but before I did anything, it started burning the CD so I don't know if it was burned as an image or data. Can you tell me from the list of folders and files I mentioned in my original question?

BTW; the "desktop" in the filename does not mean I cannot use it on my notebooks does it?

---

### Post by perspectoff on 2008-12-12
Basic user questions answered at:

[http://ubuntuguide.org](http://ubuntuguide.org) (UbuntuGuide)

and

[http://kubuntuguide.org](http://kubuntuguide.org) (KubuntuGuide)

You will have more questions, like how to dual-boot, etc.

Read the Guide.

---

### Post by Paqman on 2008-12-12
> **stickman51 said:**
> 
BTW; the "desktop" in the filename does not mean I cannot use it on my notebooks does it?

It's fine for laptops. They just mean "desktop" as opposed to "server".

---

### Post by nike007 on 2008-12-12
once you have burned the ISO. insert the CD and reboot, on reboot when it boots from the disc, you will get various options, to try it, install it, etc, either you can install from that startup screen itself [ choosing size of partition appropriately or completely erasing windows .. or you could boot into windows and run wubi.exe from the cd, it will install ubuntu inside the WIndows folder [ again choose size appropriately .. but it wont partition the HD]

in the end, its your choice

nike007

---

### Post by OldGrey on 2008-12-12
By the way you describe it I doubt that you burned the disc as an image rather than a data file. You will soon know though if you try to boot from it as it will not work if its a data file. However there are many free programs aroiund that will burn an iso image for you.

---

### Post by hyper_ch on 2008-12-12
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by stickman51 on 2008-12-12
> **perspectoff said:**
> Basic user questions answered at:

[http://ubuntuguide.org](http://ubuntuguide.org) (UbuntuGuide)

and

[http://kubuntuguide.org](http://kubuntuguide.org) (KubuntuGuide)

You will have more questions, like how to dual-boot, etc.

Read the Guide.

perspectoff; I've tried reading Linux notes but it seems like geekspeak to me; I get lost in the first para. With Windows, at least, it is usually all "user-friendly" and easy to navigate. BUT I hate Microsoft & Vista and really WANT to learn/use Linux so I bought an extra laptop JUST for that. Forgive me if I ask a lot of dumb questions.   ;-)

---

### Post by snova on 2008-12-12
> **stickman51 said:**
> Is that all there is to it? That just seems too easy.

Put the CD in the drive, and reboot. Make sure the BIOS is set to start from the CD, and it should work. Assuming the CD burned without errors, just press Enter. (Just to make sure of it, there is an option in the menu to test the disk.)

The only thing I would like to remind you is to be careful with the installer. It's not immediately obvious, but "Guided Install" will, I think, take over the entire hard drive (and wipe out Windows!).

It's a simple matter to have it install side-by-side, a "dual boot", where you have both Windows and Ubuntu installed on the same hard drive. I think it will provide a choice each time you turn the computer on.

[quote=OldGrey]
By the way you describe it I doubt that you burned the disc as an image rather than a data file. You will soon know though if you try to boot from it as it will not work if its a data file. However there are many free programs aroiund that will burn an iso image for you.[/quote]

It looks right to me. All the files are there, after all.

---

### Post by donkyhotay on 2008-12-12
> **stickman51 said:**
> Forgive me if I ask a lot of dumb questions.   ;-)

Dumb questions aren't dumb. Everyone begins somewhere and a desire to learn about this stuff is important because without it you'll never get anywhere (at least when it comes to computers). I personally believe that most of the people that say 'I tried linux and it's too hard I'm going back to my windows/mac' are people that aren't willing to learn how to use it. Linux is different from both systems and you can't expect to be an instant master of it. Read the documentation, follow the tutorials, and if you don't understand something then definitely ask.

---

### Post by rlunger on 2008-12-12
> **jay576 said:**
> didn't ubuntu allow installations from with windows now so you dont even have to reboot.  i thought it was an option last time i had a disk in while using windows

Yes, this is correct.  The first time I installed Ubuntu was from my Windows Desktop.  When I rebooted my computer, GRUB booted and I had the option of using Ubuntu or Windows.  It IS that simple.

---

### Post by 73ckn797 on 2008-12-12
If you do not have a program to burn an "ISO", then Google for "CDBurnerXP". It is free, works in Vista also and does a great job. It is what I used to burn my first Ubuntu "ISO" with.

---

### Post by stickman51 on 2008-12-12
so far so good; almost. Burned the CD (correctly this time!) and ran it; I opted to INSTALL Linux which it did. Then I removed the CD and rebooted as instructed, BUT, when it booted up, it did not offer me the opportunity to boot into Ubuntu; it booted into Vista again. And I cannot even find Ubuntu in the Start menu. Hmmmmmm; where did I mess up this time, I wonder. Any ideas please?

---

### Post by snova on 2008-12-12
It won't be on the Start Menu, it's not a program.

There should have been a prompt, "Press Esc to enter the menu" or something like that before Vista started. Did you try that?

---

### Post by stickman51 on 2008-12-12
No, there was no option to press anything; it just plain booted as normal to Vista. I re-started but same thing. Then I shut down completely and then restarted cold. Yikes; that gave me the option to choose Linux BUT the window that followed was not what I expected; it was "Start Installer..............." on 3 lines followed by "Read-only Demo..............."
That's not what I need is it?

---

### Post by snova on 2008-12-12
> Then I shut down completely and then restarted cold.

I don't get it, how *else* can you restart?

Just checking, but did you remove the disk? That would cause it to boot back into the live CD.

---

### Post by stickman51 on 2008-12-12
Yes, I did remove the disk as soon as it ejected after installing Ubuntu.

---

### Post by stickman51 on 2008-12-12
On the DOS window with the 5 options, I chose the first one, "Start Installer...." and that started to install Ubuntu (again??) When that was done, it booted back to Vista. So I restarted AGAIN. This time after clicking Ubuntu, another Dos window with the header "GRUB4DOS....." came up. I chose "Ubuntu 8.10 kernel 2.6.27-7-generic" and clicked "b" to boot. Ubuntu came up nicely but it would not accept my password. I had entered one at some point though. I don't want to have to use a password but I can't even get into Unbuntu now, without it. ARGH!!!!

---

### Post by stickman51 on 2008-12-12
Looks like I have a new problem now; Ubuntu seems to be running find but it will not accept my password. I do not want a password and would prefer to be rid of it. But I cannot even get in if it won't accept my password. Any suggestions?

This seems to be a new problem and I suppose I should start a new thread on this one. Will do that.

---

### Post by -kg- on 2008-12-12
A couple of things:

> THANKS for all those answers. I did download the .iso file ( "ubuntu-8.10-desktop-i386.iso") but before I did anything, it started burning the CD so I don't know if it was burned as an image or data. Can you tell me from the list of folders and files I mentioned in my original question?

I would say that you had burnt the disk as an .iso.  If you had burnt it as a data disk, I believe you would have had one file on the disk...the original .iso file.

> The only thing I would like to remind you is to be careful with the installer. It's not immediately obvious, but "Guided Install" will, I think, take over the entire hard drive (and wipe out Windows!).

No, the only way you could wipe out your Windows partition would be to use a disk partitioning software and purposefully wipe the Windows partition out.  What the two "Guided Install" selections do is to:

1) (Attempt to) Resize your Windows partition to make room for the required partitions for Ubuntu or;

2) Create and format your Ubuntu partitions in the largest contiguous unused hard drive space (if you have such a space).

Even the manual partitioning selection will not delete a partition unless you tell it to do that.  What selection you use depends on the conditions on your hard drive.  You should be perfectly safe no matter which selection you make.

> It's a simple matter to have it install side-by-side, a "dual boot", where you have both Windows and Ubuntu installed on the same hard drive. I think it will provide a choice each time you turn the computer on.

Correct.  If you make the default installation, the Linux bootloader, GRUB, will be installed in your MBR.  Upon each reboot you will be presented with a menu in which you will be given several selections, including your Windows installation (if you have one).  It's not necessarily a "pretty" menu (though you can make it a bit nicer) and it doesn't support a mouse (have to use the arrow keys and "enter"), but it works terrifically, and with a great many other OSes besides Linux.

> so far so good; almost. Burned the CD (correctly this time!) and ran it; I opted to INSTALL Linux which it did. Then I removed the CD and rebooted as instructed, BUT, when it booted up, it did not offer me the opportunity to boot into Ubuntu; it booted into Vista again.

From the way you stated this, am I correct in my assumption that you removed the CD ***before*** you rebooted?  When rebooting from the LiveCD, you should select rebooting, then wait until the installer either ejects the CD and/or tells you to remove it before you do so.

> There should have been a prompt, "Press Esc to enter the menu" or something like that before Vista started. Did you try that?****

Yes, there should have been a prompt...it's called the GRUB boot menu.  On it you should have seen 4 lines...the actual Ubuntu selection, the "Recovery" option, "Memtest," and your Windows selection.  You shouldn't have to press any key to get to this menu...it should come up on booting.

> not what I expected; it was "Start Installer..............." on 3 lines followed by "Read-only Demo..............."
That's not what I need is it?

No, it certainly isn't.  That's another thing that gave me the impression you might have not waited for the proper time to take the disk out of the drive.

> [QUOTE]Then I shut down completely and then restarted cold.

I don't get it, how else can you restart?[/QUOTE]

There are two ways you can restart (actually, reboot).  In Windows, when you select "Restart," it is actually a "warm reboot" or warm restart.  When you select "Shutdown" and the computer shuts down (i.e., the computer's power goes *completely* off), then when you turn the computer back on and it boots into whatever OS, it is called a cold restart, or a cold reboot.

In the old DOS days (before there was Windows), you would initiate a warm reboot using <ctrl, alt, del>.  Cold rebooting was initiated by simply turning the computer's power off.

Well, you just posted back, and it seems you "successfully" got into Ubuntu...

> Ubuntu came up nicely but it would not accept my password. I had entered one at some point though. I don't want to have to use a password but I can't even get into Unbuntu now, without it. ARGH!!!!

Looks like I have a new problem now; Ubuntu seems to be running find but it will not accept my password. I do not want a password and would prefer to be rid of it. But I cannot even get in if it won't accept my password. Any suggestions?


Actually, I don't think that's an option (at least, I haven't found a way, though I really don't think I'd want to do without it).  You pretty well *must* (and really want to) use a password with Linux.  That's one of the things that makes Linux so superior to Windows...it's security.  No password...no security.

Every time you must use a command as a "Super User" (via the "sudo" command, or doing operations on your computer like Updating, installing software, and such), you are asked for your password.  This keeps others from hacking in to your system and wreaking havoc (unlike Windows and it's virus', spyware, and such problems).

You either need to remember the password you put in, or you will need to reinstall and remember your password.  I would choose a password that is secure, yet easy to remember.

---

### Post by Paul86fxr on 2008-12-12
I'm just jumping on the band wagon, I agree with everyone above

---

### Post by stickman51 on 2008-12-12
OK, I'll stick the CD in again and follow the prompts to reinstall it, being extra careful to enter and remember my password. I really do not need a password on this machine though; would prefer not to have one. Never uses it in Windows either. Pray fur me, y'hear?

---

### Post by snova on 2008-12-12
I think there is a way to have the login screen log you in automatically, without password. I don't know the exact process, but it'll probably be at System -> Administration -> Login Window.

---

### Post by egalvan on 2008-12-12
> **earthpigg said:**
> 
in addition, the _only_ time an ubuntu install can even be slightly complicated is if you want to dual boot.

I must disagree...

The first time a person tries an installation can *also* be complicated.

Unfamiliar words, unfamiliar commands, unfamiliar ideas...
these can all cause uncertainty...

Linux is not Windows...Windows is not Linux...

And all of us, at one point in our lives, did not know what a computer was all about.

Let's give students a hand up in their education.

Remember, everything is easy if you know how to do it...

---

### Post by Sorivenul on 2008-12-12
> **snova said:**
> I think there is a way to have the login screen log you in automatically, without password. I don't know the exact process, but it'll probably be at System -> Administration -> Login Window.
Correct.  Under the "Security" tab, select the "Automatic Login" option and your user.

Despite the fact you can login automatically, I strongly recommend against it.  It is not a good security practice, and can compromise your data if your computer ever gets stolen.

Also it is good to have a password in order to confirm some actions that normally need to be done as root, which can be done using the "sudo" command on Ubuntu.  More information on Root/Sudo can be found [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by sigurnjak on 2008-12-12
Let me jump in as well !):P
In system administration got to login window . There you can set up your account to auto log in , so  you wont have to put in your password  every time you  boot in Ubuntu !

But this being laptop  i would not do that  since it can be  easily stolen and everyone can access your account  , bank , etc.

---

### Post by sigurnjak on 2008-12-12
Oops ! echo , echo , again!

---

### Post by -kg- on 2008-12-12
Oh heck...hope you read this!

If it comes up and you don't have the room to do a guided install, just abort the install and boot up to the LiveCD and run GPartEd (Gnome Partition Editor) under the "System/Administration" menu.

Once there, you should see an image of your hard drive.  Delete all "ext3" and "Swap" partitions, then, once back at the desktop, you should be able to install normally.

Just be sure ***not*** to delete any Windows (FAT or NTFS) partitions.

---

### Post by linux phreak on 2008-12-12
Make sure to backup all your data before installing the OS.

---

### Post by stickman51 on 2008-12-12
Yikes, this is not what I expected. I sure appreciate you all putting up with me; without that I'd have given up and taken the new computer back to the store.

I have run the CD again, and installed it again, and was VERY careful with my password. Alas, it booted up but would not accept my password.

Vista is starting to look better all the time   ;-)

[SIZE="4"]WHOOOOOOOOOOPS! I entered my password two more times and the third time it WAS accepted. Looks like I'm finally in.[/SIZE]

What a performance. It even went online just fine.

THANK YOU TO ALL OF YOU WHO HELPED and TRIED to help. If you don't mind, I'll be back with more questions.

---

### Post by -kg- on 2008-12-12
Ask away...any time!  I know what it's like, too!

I've been into computers since before Windows (I remember seeing Windows 1.0 on the software shelf) but I'm fairly much a newbie with Linux myself.  I've been helped (and helped and helped...and *still* being helped!), so I'm returning as much of the help I received as I can to others just starting.

---

### Post by stickman51 on 2008-12-12
Hi, kg, it really is great how so many good people will help like this. I try when I can; for example, my "picnic table making" page is extremely popular and I've had loads of email from folks who used it. I made a note of all I did on this Ubuntu project, and it is on my website for the benefit of my relatives (and others of course) who might like to see it: [http://www.sticksite.com/linux/](http://www.sticksite.com/linux/)

Wish the whole WORLD could/WOULD get along so well!!

I wonder how many countries were involved in my 2 threads on this subject; several, I suspect.

---

### Post by 73ckn797 on 2008-12-13
> **stickman51 said:**
> Hi, kg, it really is great how so many good people will help like this. I try when I can; for example, my "picnic table making" page is extremely popular and I've had loads of email from folks who used it. I made a note of all I did on this Ubuntu project, and it is on my website for the benefit of my relatives (and others of course) who might like to see it: [http://www.sticksite.com/linux/](http://www.sticksite.com/linux/)

Wish the whole WORLD could/WOULD get along so well!!

I wonder how many countries were involved in my 2 threads on this subject; several, I suspect.


It is called Ubuntu.

---

