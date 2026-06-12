---
title: "Suspend (S3) Resumes Immediately"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by Cuco3 on 2009-09-29
Has anyone experienced a problem that when you put the computer to suspend / sleep it resumes immediately?

Also, I noticed that when it does resume, all my open windows are gone / closed. Weird...

I'm using:
Dual Boot WinXP w/ Jaunty completely updated
Intel D845PESV Motherboard
GeForce 7600 GS Video Card
WD 80GB JB Hard Drive
Sony DVD/RW Drive
PS/2 Keyboard and Mouse

BIOS settings are:
Plug n Play OS: YES
Suspend Mode: S3

I've also tried disabling USB and USB Boot through the BIOS with no success.

If I had to guess, it's a device that is sending a Wake-Up event, but I don't know how to check which devices are configured to do that in Ubuntu. Although, it strikes me as strange that all my open programs are now closed when it resumes.

I also did some research. Some people suggest that in the front panel USB connectors in the motherboard you should use +5VSB instead of +5V but my mobo doesn't appear to have an option for that through a jumper or BIOS setting.

I also read something about usbcore.autosuspend=, but configuring that setting varies for each distro and I think for Ubuntu it says you have to recompile the kernel (I'm relatively new to Ubuntu so, even if that was the proper way to do it, I wouldn't do it unless I knew how to).

---

### Post by Cuco3 on 2009-09-30
Anybody had this problem before and have had it resolved?

---

### Post by Cuco3 on 2009-09-30
I think it might have something to do with the Ubuntu Power Mgmt using a hybrid of Suspend/Hibernate.

The sympsom are:
1. When the computer resumes, it doesn't resume immediately; it shows the Ubuntu startup loading screen as if it resuming from Hibernate.
2. All my programs are closed /missing when it does, which probably means it didn't have enough space to write to the swap file.
3. I read that people where having the same problem resuming from hibernate when their swap file wasn't big enough.

---

### Post by dearingj on 2009-09-30
Have you tried suspending from within Windows, and if so, does it have the same problem? The fact that your windows are no longer open gives me the impression that some software (either Ubuntu or one of the apps you had open when you suspended) is the cause of the problem, not your hardware.

---

### Post by dearingj on 2009-09-30
You can give your computer a new swap file (which will be used in addition to the swap partition that Ubuntu uses by default). Here's how: [http://www.linuxjournal.com/video/emergency-swapfile-when-your-memory-fills](http://www.linuxjournal.com/video/emergency-swapfile-when-your-memory-fills)

Try this, and see if it fixes your problem.

---

### Post by Cuco3 on 2009-09-30
Thanks man.

I just set the system up a couple days ago.

Never tried it in Windows (just like to dual boot for when I need to use windows)

Tried it in Windows and the same thing happened!

So I went to the BIOS and tried some settings:
1. From "After power failure: Last State" to "Stay Off"

Changing that setting stopped it from "resuming", which is the wrong word for it; it didn't gracefully enter Sleep Mode so it rebooted as per BIOS setting. :P

2. So I tried "Standby Mode: S3" to "S1"

And now it gracefully enters Standby, although with the fans still runing. :( (has a loud cpu fan)

Gonna try unplugging the power cord for 20 seconds. If that doesn't work, I'll try updating the BIOS before I write it off as s faulty motherboard... although everything works fine except for the S3 standby mode.

---

### Post by Cuco3 on 2009-10-03
_[COLOR=Red]**[SIZE=5]***SOLVED***[/SIZE]**[/COLOR]_ 

(sorta)

The culprit was actually the Power Supply.

Bought a new one, replaced it, and now suspend works ... in Windows XP.

In Ubuntu, it appears to suspend gracefully. But when you go to wake it up, the keyboard is functional for like 3 seconds then it crashes; the screen stays black / blank with the hard drive light on. Pressing Numlock or Capslock doesn't get the lights on the keyboard to change so it's definitely a crash.

I'd love to isolate the culprit, or analyze pm-suspend.log to check for failures, but not sure how to go about that in Ubuntu / Linux.

I'm gonna start a new thread to track my progress and hopefully people will offer their advice.

First thing I'll do is try upgrading to Karmic Koala (9.10). If not, I'm gonna try Hardy Heron (8.04).

---

