---
title: "10-10 install aborted by GLib-WARNING"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by BearDrummer on 2011-01-30
I am new to Ubuntu.  I managed to load Ubuntu side-by-side on my son's computer (logged into it now), but not on the intended computer...  I tried 10.04.1 multiple times, changing everything, and never saw the desktop, except in "trial" mode.  Following advice, I tried a different one... I downloaded 10.10, ran it through the cd-image burner on my son's computer, loaded it into the cd tray on the intended computer, and recieved the following message 3 times in a row.

[COLOR=Blue](process:223): GLib-WARNING  **: Get pwuid_r(): failed due to unknown user id (0)[/COLOR]

I did some research, and it said that it was caused by using a hard shut-down on the prior run.  Hard shutdown is the only way to re-try loading.  Any ideas?

---

### Post by robsoles on 2011-01-30
Have you 'loaded defaults' in the BIOS of the machine you are getting these error messages on? If not then I suggest you take photos (archaic method but workable) of the settings in each page of your BIOS and then reset it to defaults, reboot and if something you can't stand is happening worse than your current situation then compare the photos to the 'default' settings in BIOS and change as little back as you can manage to make the new problem go away - probability of no new problems but, just in case...

Speaking of just in case: If you've made 14 or so posts without being welcomed then that is a pity. Welcome to UF :)

Anyway, with a bit of luck it will be a non-default setting in BIOS that is sitting in your way and just defaulting it will make it easily install the OS of your choice.

If that fails then please shut the computer right down and give it five minutes off and then boot it from the 10.10 (or whatever you have, capable) LiveCD and give us a plain description of what it does and lots more details on the specs of the system doing this to you.

---

### Post by mörgæs on 2011-01-31
There is a bug fix for this:
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

Have you applied all updates?

---

### Post by BearDrummer on 2011-01-31
> **robsoles said:**
> 
Speaking of just in case: If you've made 14 or so posts without being welcomed then that is a pity. Welcome to UF :)

Anyway, with a bit of luck it will be a non-default setting in BIOS that is sitting in your way and just defaulting it will make it easily install the OS of your choice.

If that fails then please shut the computer right down and give it five minutes off and then boot it from the 10.10 (or whatever you have, capable) LiveCD and give us a plain description of what it does and lots more details on the specs of the system doing this to you.

Thank you for the welcome... As I was posting in "install issues" instead of "newbie", the lack of a welcome is understandable.  And, as it is my birthday today, maybe the powers-that-be  will grant me a working computer...

I had a more successful attempt - it had the status bar and everything, up to about 68%, then I got a "Install crash" message...  I tried again while I looked for my notebook to write down the error numbers, etc.  I have re-attempted several times, and have not gotten that far since.  

I made two 10.04.1 live discs, and one 10.10 - I have received the same 2 error messages for all 3.

The computer is a Dell Dimension 4300, operating on a 256 memory stick (we have 2 512's on the way).  I have been rotating out various CD or DVD readers - only the 2 that were in the box when I got it register in BIOS, and will auto-boot.  I have switched out hard drives, and attempted various configurations - 2 40g hard drives mounted, or just one.  Once again, only the hard drive that was in it when I received it works without a "primary drive not found" message.  Any of the drives are accessible when I put an XP disc in - it finds the disc and can install XP up to service pack 1, but won't allow the completion of loading any program after that (the reason I am trying Ubuntu).

the pattern runs similarly with 2 different endings - the GLib-Warning, or a[COLOR=Red] (initramfs) Unable to find a medium containing a live file system[/COLOR]... 

the BIOS load shows on screen as [COLOR=RoyalBlue]Dimension 4300 BIOS Revision A05[/COLOR], 
Then [COLOR=RoyalBlue]Phoenix ROM BIOS PLUS Version 1.10 A05[/COLOR]
It tells me that the primary dirve is not found, and to hit F1 to continue, or F2 for setup. (I hit F1)
The purple screen with the rectangle and the little guy appears, 
followed by a blank screen with flashing line cursor.
It goes black for a little while, then
loads the purple background Ubuntu with the dots rotating underneath.
At this point I either get a 

[COLOR=Red]GLib-WARNING[/COLOR] (first message)
or
[COLOR=Red]BusyBox v1.13.3 (Ubuntu 1:13.3-1ubuntu11) Built in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) unable to find a medium containing a live file system.[/COLOR]

Hitting enter brings up a prompt of (initramfs), but I can't find a command that says "[COLOR=Green]Well look again you old piece of plastic[/COLOR]!"

My wife just told me that my latest attempt gave the install screen...  I will go through that as it happens before sending... 
 I get farther by attempting side by side, so I am giving the XP load 10G and the Ubuntu 30G...
Made it through the 7 screens to the Install button...  And froze on 25%.  I let it sit on 25% for half an hour before restarting.

I am currently re-attempting again.

---

### Post by mörgæs on 2011-01-31
With 256 MB memory it is a waste of time to try to install Ubuntu. Best is to wait until the machine has the full GB. 

Lubuntu or Puppy will work, though.

---

### Post by robsoles on 2011-01-31
Happy Birthday!!! Although I'm fearing you won't see this machine boot from one of the LiveCDs you have right now.

It sounds to me like the machine needs certain parameters set at boot time to 'come up off the LiveCD' successfully. I'll go read up on that stuff before shooting my mouth/fingers off and post again when I think I'm capable of doing your situation more good than harm ;)

The fact that it comes to a 'crunch' in Windows may indicate a failed 'capability' of the laptop in question and that 'capability' may be called on by the LiveCD sooner than Windows finally gets around to having a driver to 'enable' "that" with. Just something that occurred to me, sorry if it's the case.

Anyway, anybody who wants to gazump me with some boot arguments that might (or better still, should) help BearDrummer then, oh please do :)

---

### Post by BearDrummer on 2011-02-02
OK, due to the fact that I will have 2 512 RAM here soon to replace the 256 that shows to be running only at 166, and the fact that the CD reader has quit being acknowledged by the computer, I am putting off this project at least until the RAM arrives.  As the computer is working less and less, I may have to just put the computer itself in the trash, and start over again when we can afford another. It is becoming rather apparent that there are multiple hardware problems that are, at the very least, contributing to the problems installing.

I appreciate the advice and attempts at help that have been offered.

---

