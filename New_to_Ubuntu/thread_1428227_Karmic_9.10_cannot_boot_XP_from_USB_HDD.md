---
title: "Karmic 9.10 cannot boot XP from USB HDD"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by The Pilgrim on 2010-03-12
I have to boot a Win OS. Former XP Home is untouched on the previous HDD (I mean bootable if main drive) and USB conected. The machine is a laptop with a rudimentary BIOS (Compal EDL 71), so no USB boot option available. 
GRUB sees XP OS, and after a few interventions guided from a post in the forum  I did get rid of the error message, but all I can get now is a black screen with the cursor blinking in the upper left. I have to restart to get out of there. Ubuntu works normal.

So, the questions are: How to boot the Windows OS from the external HDD? Is it possible?

Please help and thank you for your time.

Stefan

---

### Post by MichealH on 2010-03-12
When you boot up look for a "Boot Menu" option (typically F11) and If you keep pressing it you should see a box select your USB HDD from the menu.

---

### Post by The Pilgrim on 2010-03-13
Done that a moment ago, no result, nothing happens.

Does that relates with the poor bios option? (no USB boot) ?

GRUB sees xp, but can it jump over BIOS and boot an OS directly from an external drive?

Anyway, thanks for the help intention.

---

### Post by MichealH on 2010-03-13
> **The Pilgrim said:**
> Done that a moment ago, no result, nothing happens.

Does that relates with the poor bios option? (no USB boot) ?

GRUB sees xp, but can it jump over BIOS and boot an OS directly from an external drive?

Anyway, thanks for the help intention.

So, GRUB sees your XP? Maybe install a GRUB onto your usb and do what I said above or It may be a bad bios option.

---

### Post by The Pilgrim on 2010-03-13
[URL="http://ubuntuforums.org/member.php?u=883491"][COLOR=Black]MichealH please do not forget  it's an Absolute beginner talk. Be more specific please.[/COLOR]
[/URL]

---

### Post by MichealH on 2010-03-13
> **The Pilgrim said:**
> [URL="http://ubuntuforums.org/member.php?u=883491"][COLOR=Black]MichealH please do not forget  it's an Absolute beginner talk. Be more specific please.[/COLOR]
[/URL]

[Maybe see this Howto? http://ubuntuforums.org/showthread.php?t=992426]("http://ubuntuforums.org/showthread.php?t=992426")

---

### Post by The Pilgrim on 2010-03-14
Sorry, a bit ahead of me in this moment. Perhaps a non solution issue... And I was so enthusiastic :((  ... so many expectations :((

Anyway thank you for you help. I'll still try to look  for a sollution.

---

### Post by marshmallow1304 on 2010-03-14
You can put [PLoP Boot Manager]("http://www.plop.at/en/bootmanager.html") on a CD or floppy, boot to that, then use it to boot to your USB drive.

---

### Post by J V on 2010-03-14
Why not just install a half-decent bios... There are open source solutions for everything you know :)

---

### Post by The Pilgrim on 2010-03-15
> **marshmallow1304 said:**
> You can put [PLoP Boot Manager]("http://www.plop.at/en/bootmanager.html") on a CD or floppy, boot to that, then use it to boot to your USB drive.

I'll look into it. But is it any better than GRUB? Remember GRub sees XP on the external HDD (it is the former drive from the laptop, which has a XP home complete functional OS), but cannot start it.

Thank you.

---

### Post by The Pilgrim on 2010-03-15
> **J V said:**
> Why not just install a half-decent bios... There are open source solutions for everything you know :)

Flashing BIOS is the last thing I would mess about. Tech support for Complal EDL 71 is xtremely hard to find and if I fail I loose the computer. Not an option..

---

### Post by d3v1150m471c on 2010-03-15
Your grub menu has nothing to do with bios. If you want to boot from usb then it has to be selected to do so in the bios menu before it clears and passes to grub.

---

### Post by The Pilgrim on 2010-03-15
Yes, but someone on this forum said that he deliberately turned off in Bios the option of USB booting, and could bypass this issue, booting from external drive. Unfortunately I'm too new in Linux for this way of solving the problem. Soo, still searching, may be an easy fix might appear (could that be a "Karma" issue??).

---

### Post by Mark Phelps on 2010-03-15
Word of advice -- don't mess with your BIOS.  Easy way to end up with an "electric brick" if you don't know EXACTLY what you're doing.

Also, it's "Karmic Koala" -- the next release of Ubuntu, due out the end of this April.

But, if you're having BIOS-related problems, it's not going to do anything for you.  Machine boots using the BIOS long before it sees any OS.

---

### Post by The Pilgrim on 2010-03-15
> **Mark Phelps said:**
> 
But, if you're having BIOS-related problems, it's not going to do anything for you.  Machine boots using the BIOS long before it sees any OS.

If the factory missing option to boot from USB can be a BIOS problem, then yes, I have a  problem. I have to find IF there is a way to boot from the USB external drive (with a functional XP home on it, seen by GRUB).

---

### Post by stevenh512 on 2010-03-15
Sounds to me like this might actually be a Windows configuration issue. When you moved the internal drive with Windows installed and put it on USB, did you edit the Windows BOOT.INI file? If it was installed on the internal drive, that's where BOOT.INI is going to tell the Windows boot loader to look for the OS, it doesn't know to look on the USB drive unless you do some editing. I could be wrong, but if GRUB can see the drive then I'd imagine it has enough USB support built-in to boot the drive (just like the PLoP boot manager mentioned earlier in this thread).

Just for fun, reboot and select Windows from your GRUB menu, then immediately start tapping the F8 key for a few seconds. Hopefully a menu will come up with options like Safe Mode, if so your Windows bootloader is booting just fine and it's most likely just a matter of editing that one file and rebooting to safe mode to fix up any broken registry entries (good luck, that's never fun).

---

### Post by The Pilgrim on 2010-03-15
Stevenh, it didn't work. F8 means nothing at this moment. And editing win's bootloader is something I have to be guided through..

thank you guys for trying to help. Maybe we'll get it somehow.

---

### Post by stevenh512 on 2010-03-15
I don't have access to an XP machine at the moment and it's been a long time since I've moved an XP drive like that so I probably wouldn't be too much help trying to talk you through editing the BOOT.INI file.

Now that I think about it, GRUB and your BIOS could be the problem though. The other boot manager mentioned earlier in this thread (PLoP) might be worth a try. I know early in the boot process Windows relies on BIOS calls to detect hardware, what I don't know is whether or not GRUB extends any of those real-mode BIOS interrupt calls to allow Windows (or DOS, or any other OS or boot loader that uses BIOS to detect the drive) to see the drive. PLoP does, you can even use it as a USB driver for DOS so that and a BOOT.INI edit should be enough to get Windows booting.

---

### Post by presence1960 on 2010-03-15
You have to jump through a lot of hoops to get windows to boot from an  USB/external disk. I did a search on google and the sites that have how-to's on booting windows from USB/external are a mixed bag. Some claim success using the various methods posted but others claim utter failure. Microsoft steadfastly claims that windows can not be booted from a USB/external disk. With all the time & trouble to do these things that may or may not work you can have windows installed to an internal disk and working.

GRUB will detect the windows on the external because it only looks for boot files/directories and will list those found in menu.lst (GRUB Legacy) or grub.cfg (GRUB 2). But the fact that they are in the GRUB menu does not mean they will actually boot. To understand what I am saying copy your windows boot files/directories to a linux partition. Update GRUB and windows will be listed on the GRUB menu for that linux partition because GRUB found those windows boot files. But if you try to boot that windows entry (linux partition) windows will not boot.

---

### Post by The Pilgrim on 2010-03-15
If you're right, I'm in deep trouble. I really need windoz for autocad. Tryed a 2004 release in Wine, but is working unsatisfactory. And didn't find so far a Linux app to work with *.dwg files. I hate to turn back to xp. And I would feel more confy with an external drive to run it...

Should I hope?

---

### Post by thegod_slayer on 2010-03-15
hello friends.....

i have been using ubuntu since the past 3 months.....
i have done a lot of research work before i went on to linux....
cause i am having a wipro lappy(full ubuntu) and a desktop(dual boot between xp and ubuntu) having intel processor.

so as far as i have gathered knowledge on os, i think that linux should be installed after installing windows.
the reason behind this is that linux can automatically understanding what os is already installed.
but our dear windows can not understand what os is already installed.
so all the books on linux installation says to install linux after installing windows, not the other way round.

---

### Post by thegod_slayer on 2010-03-15
sorry for the incomplete reply........

as linux can understand what os is installed it optimises itself
accordingly.
but in the case of windows as it doesn't understand what os has been insatalled it thinks that the full hardrive is his and thus rises a conflict between the two..

---

### Post by The Pilgrim on 2010-03-15
That would mean head scratching again...

You know, they say that hope is the last to die.

---

### Post by marshmallow1304 on 2010-03-15
> **The Pilgrim said:**
> If you're right, I'm in deep trouble. I really need windoz for autocad. Tryed a 2004 release in Wine, but is working unsatisfactory. And didn't find so far a Linux app to work with *.dwg files. I hate to turn back to xp. And I would feel more confy with an external drive to run it...

Should I hope?

Maybe have a look at [VirtualBox]("http://www.virtualbox.org/").  Depending on your specs, you may be able to run XP comfortably from within Ubuntu.

---

### Post by presence1960 on 2010-03-15
> **thegod_slayer said:**
> hello friends.....

i have been using ubuntu since the past 3 months.....
i have done a lot of research work before i went on to linux....
cause i am having a wipro lappy(full ubuntu) and a desktop(dual boot between xp and ubuntu) having intel processor.

so as far as i have gathered knowledge on os, i think that linux should be installed after installing windows.
the reason behind this is that linux can automatically understanding what os is already installed.
but our dear windows can not understand what os is already installed.
so all the books on linux installation says to install linux after installing windows, not the other way round.

You read the wrong books my friend:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

Also once you install windows after Linux all you need to do is restore GRUB to MBR, if windows is not in the GRUB menu run the update-grub command.

Please try to research before you make blanket statements, especially to see whether they are true or not.

---

### Post by presence1960 on 2010-03-15
> **thegod_slayer said:**
> sorry for the incomplete reply........

as linux can understand what os is installed it optimises itself
accordingly.
but in the case of windows as it doesn't understand what os has been insatalled it thinks that the full hardrive is his and thus rises a conflict between the two..

pure poppycock! All you need to do is restore GRUB to MBR because windows will overwrite it. Then if windows is not in the GRUB menu run the update-grub command or if using Legacy GRUB add a chainload entry for windows to menu.lst.

---

### Post by presence1960 on 2010-03-15
> **The Pilgrim said:**
> If you're right, I'm in deep trouble. I really need windoz for autocad. Tryed a 2004 release in Wine, but is working unsatisfactory. And didn't find so far a Linux app to work with *.dwg files. I hate to turn back to xp. And I would feel more confy with an external drive to run it...

Should I hope?

Like I said about those how-to's to get windows to boot from an external/USB disk that some people succeeded and some failed. It won't hurt to try, maybe you will be one of those who succeeded. 

I have to ask- Why won't you install it on your internal disk?

---

### Post by The Pilgrim on 2010-03-16
> **presence1960 said:**
> 
I have to ask- Why won't you install it on your internal disk?

This I think is the next move; I do not know how long will it take to solve the external drive boot, and I must be able to work. (any direct path to do that safely? excuse me, got a bit dizzy lookin' allover for answers). 

But the quest for the usb boot remains. Though I have an xp license, I would preffer to have a completly clean, Linux based system. And, getting OT, I wanted to leave windows for long ago, but didn't have the time for that; crysis had to come for me to have the time to learn & search. Not to mention the feeling of freedom that Linux is offering.

Again thank you guys for minding other people sorrows. :)

---

### Post by Doctor Mike on 2010-03-16
> **The Pilgrim said:**
> This I think is the next move; I do not know how long will it take to solve the external drive boot, and I must be able to work. (any direct path to do that safely? excuse me, got a bit dizzy lookin' allover for answers). 

But the quest for the usb boot remains. Though I have an xp license, I would preffer to have a completly clean, Linux based system. And, getting OT, I wanted to leave windows for long ago, but didn't have the time for that; crysis had to come for me to have the time to learn & search. Not to mention the feeling of freedom that Linux is offering.

Again thank you guys for minding other people sorrows. :)simple question. If your XP is installed on a usb drive is it a copy, from another system. If it's a copy or from another system you will have trouble getting to work anyway. But if it was installed on a usb drive then getting it to boot should not be a problem. If it's the original drive put everything back the way you had it (reboot) and then look at a Ubuntu install.

---

### Post by The Pilgrim on 2010-03-16
> **Doctor Mike said:**
> simple question. If your XP is installed on a usb drive is it a copy, from another system. If it's a copy or from another system you will have trouble getting to work anyway. But if it was installed on a usb drive then getting it to boot should not be a problem. If it's the original drive put everything back the way you had it (reboot) and then look at a Ubuntu install.

Extended answer.

XP is installed on USB drive which was the previous laptop's hdd. I made an upgrade to 160G (from 80) and put a brand new Ubuntu Karmic Koala 9.10. I'm trying now to boot the external XP (which has everything functional) without reinstaling any of the 2 OS (exporting from Mozilla and Thunderbird was a pain, etc).

<<If it's the original drive put everything back the way you had it (reboot) and then look at a Ubuntu install>> You mean put back the drive in the laptop? and after that install Ubuntu on a new partition?

<<But if it was installed on a usb drive then getting it to boot should not be a problem.>>
Please be more specific.

Thank you.

---

### Post by Doctor Mike on 2010-03-17
> **The Pilgrim said:**
> Extended answer.

XP is installed on USB drive which was the previous laptop's hdd. I made an upgrade to 160G (from 80) and put a brand new Ubuntu Karmic Koala 9.10. I'm trying now to boot the external XP (which has everything functional) without reinstaling any of the 2 OS (exporting from Mozilla and Thunderbird was a pain, etc).

<<If it's the original drive put everything back the way you had it (reboot) and then look at a Ubuntu install>> You mean put back the drive in the laptop? and after that install Ubuntu on a new partition?

<<But if it was installed on a usb drive then getting it to boot should not be a problem.>>
Please be more specific.

Thank you.OK, the easiest way to proceed is to switch the position of the two drives. Why... because XP's software protection might not have liked the move and prevented its boot up. Second, if your USB has the ability to boot up, your already installed copy of Ubuntu (on the 160 Gig HDD) should boot from the USB position.

If your USB will not boot the second (Ubuntu) drive there may be ways around that, but XP is the problem child here and we need to have it where it will be happy.

If XP fails to boot when placed in its original position there may be other problems that need to be addressed. 

Do the switch and let me know what happens.

---

### Post by The Pilgrim on 2010-03-17
I'll test the switch this we and post results. Probably GRUB will have to be looked for, but XP will work with no problems, I'm sure. 

The point is I feel this will be a downgrade. Loosing a battle but not the war? Hope so. In the end (of course, a temporary end) Ubuntu should run IN the machine and xp OUT (where it belongs?).

Cheers

---

### Post by Doctor Mike on 2010-03-18
> **The Pilgrim said:**
> I'll test the switch this we and post results. Probably GRUB will have to be looked for, but XP will work with no problems, I'm sure. 

The point is I feel this will be a downgrade. Loosing a battle but not the war? Hope so. In the end (of course, a temporary end) Ubuntu should run IN the machine and xp OUT (where it belongs?).

CheersThe war is not lost. There are always ways to make a thing work. Sometimes they have to be invented. The only thing that bothers me is that you may be forced to have both systems on the same drive. I do not, and can use each as a tool to restore images of the HDD of the other or correct file problems (more Ubuntu too XP) Xp does not see EXT4 which is the file system for Ubuntu. But I have told you in my email that I will try to help or point you to better source if needed. Oh message about pointing to better source died before sending... You will win the war period...

---

### Post by ScottinSoCal on 2010-03-18
> **The Pilgrim said:**
> I have to boot a Win OS. Former XP Home is untouched on the previous HDD (I mean bootable if main drive) and USB conected.

This is not going to happen the way you have it set up. You can remove your current hard drive, reinstall the old one with XP on it, and boot that way, if you really have to.

The problem is, XP does it's own drive mapping thing, to tell it what hardware is where. Yours is currently mapped to be the primary hard drive inside the notebook - it won't even consider booting if it's changed to be the USB external drive, because it's looking for all the load files on the primary internal HD. Back in the days of primary and secondary IDE drives, you couldn't even switch a drive from primary to secondary and still have it boot. It's just the way the OS works. Sorry.

---

### Post by Doctor Mike on 2010-03-18
> **ScottinSoCal said:**
> This is not going to happen the way you have it set up. You can remove your current hard drive, reinstall the old one with XP on it, and boot that way, if you really have to.

The problem is, XP does it's own drive mapping thing, to tell it what hardware is where. Yours is currently mapped to be the primary hard drive inside the notebook - it won't even consider booting if it's changed to be the USB external drive, because it's looking for all the load files on the primary internal HD. Back in the days of primary and secondary IDE drives, you couldn't even switch a drive from primary to secondary and still have it boot. It's just the way the OS works. Sorry. Yes if you read the earlier post the user was in need of getting back to work (cad I think), so I tried to find  a solution (Temp) that would do that and provide a test to confirm boot ability from USB. Imaging the drive and possible boot strap with grub on the primary drive is a possible way to have options for booting even from a normally non-booting usb. But, I try to make my answer fit the need and the users level of understanding for the problem. I responded to this post because I thought other responders had offered solutions that didn't take into account all of the users' current needs. User has issues with bios update. So do I. Not what I'd call a first step. However, I believe the user has a retail install cd which can be used with a repair install to switch hard drives (with image). If you feel I have missed bigtime send me a message because I also don't wish to discourage anyone. thank you.

The bios ability to boot from USB has not been confirmed at this point. I know that windows of almost any recent kind would object (to put it mildly) but small steps can do no harm and may produce a workable solution. Possibly with additional help, but that's something we all hope for.

---

### Post by ScottinSoCal on 2010-03-18
> **Doctor Mike said:**
> However, I believe the user has a retail install cd which can be used with a repair install to switch hard drives (with image). If you feel I have missed bigtime send me a message because I also don't wish to discourage anyone. thank you.

I've never had any luck trying to use the repair to get it to switch drives, unfortunately. I used to carry a WinXP hard drive in a spare caddy that I could slip in and out of my notebook for those few times I needed my old WinXP working. Since I've dumped Windows completely, I don't even use that any more. I think I have it ghosted somewhere, though.

It could be reinstalled to boot from the USB drive, IIRC (it's been too long since I've installed XP), but that wouldn't get him his old programs back without also reinstalling them, and it didn't sound like he wanted to do that. And, of course, there's the nighmarish option of backing up of the old registry, editing it manually to change drive references, then putting it back in, but that's also more fun than most people want to have. Easiest by far in most notebooks is just to swap the hard drives.

---

### Post by Doctor Mike on 2010-03-18
> **ScottinSoCal said:**
> I've never had any luck trying to use the repair to get it to switch drives, unfortunately. I used to carry a WinXP hard drive in a spare caddy that I could slip in and out of my notebook for those few times I needed my old WinXP working. Since I've dumped Windows completely, I don't even use that any more. I think I have it ghosted somewhere, though.

It could be reinstalled to boot from the USB drive, IIRC (it's been too long since I've installed XP), but that wouldn't get him his old programs back without also reinstalling them, and it didn't sound like he wanted to do that. And, of course, there's the nighmarish option of backing up of the old registry, editing it manually to change drive references, then putting it back in, but that's also more fun than most people want to have. Easiest by far in most notebooks is just to swap the hard drives.
Until he has a viable solution for his work (CAD I believe) he must use XP, please read the post...

---

### Post by Doctor Mike on 2010-03-18
If I'm not mistaken with a retail cd (after or without oem install) one has many options including moving hardware, including moving os to a new computer (as long as you remove/kill the old one), Oem installs do not like hardware changes and hard drive switching is a pain unique to each user and system. And don't tell me it can't be done even on an OEM as installed, because it can, but will not be covered here, or by me. This forum is not about bypassing built in safeguards for software integrity. It's about being human and I'm trying to do just that... And if I sound like a snot please forgive me, I am not the most experienced Ubuntu user, but not without experience of many system and os's and repair issues. So' as I have said if you know a better solution (more effective) please post. Otherwise please take into account the original users post, needs and current trepidation about a possible switch to Ubuntu. I only run xp because of two software items and xp office support.

---

### Post by The Pilgrim on 2010-04-03
Thank you all guys for your kind effort. For the moment the situation remains as it was. The latest couple of weeks time for this project was xtremly short (sorry for not posting regardin' your latest advices) and the only time I had to use autocad was solved on an old Dell GX110 desktop (crisis still here..). Mean time I'm trying to find a suitable cad solution for linux (moving around brlcad, but a pain to install - I still do not know how to do that). And be a normal guy with a normal OS, runing normal software.

Ah, and  may you all have a Happy Easter! (which in Romania is celebrated today)

Thank you again!

Stefan

---

