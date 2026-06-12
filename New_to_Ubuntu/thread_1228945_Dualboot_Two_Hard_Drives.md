---
title: "Dualboot Two Hard Drives"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by nym1 on 2009-08-01
Man, I hate to do this, but I am brand new to this forum, and cannot for the life of me figure out how to ask a question that is not tied to a preeixsitng one??? 

Sort of a "start new question", "post a question", etc.

I checked the faqs for the site, and in the search I entered things such as "how to ask a question", but was unable to get anywhere, SO i am just dropping my question into a remotely-related question in the hopes that someone will see it. *sheesh- i feel stoopid*

I have a system that was running fine using Grub to boot into Vista x64 and Ubuntu, but had to reinstall Vista; that went fine, and I have searched online for help on how to reinstall Grub to the MBR. 

My question is this; How do you use the cd to reinstall Grub? I went into the live cd and did the steps, and the terminal says it was successful, but when I exit out and restart my computer, Grub is still not there, and it just goes right into windows??

btw, I have twin drives in my PC; Vista on the one, and Ubuntu on the other, so I am assuming that my vista reinstall has not touched my linux partition on the 2nd drive.

Any help would be greatly appreciated, as I just don't know enough about linux to know why Grub is not there...

Also if anyone can tell me the PROPER WAY to ask a question, of course that would be appreicated as well :O)

Thanks,

nym

---

### Post by unutbu on 2009-08-01
Welcome to the forums, nym1.
Here is a tutorial on forum basics: [http://ubuntuforums.org/showthread.php?t=726150](http://ubuntuforums.org/showthread.php?t=726150)
and how to start new threads:
[http://ubuntuforums.org/showpost.php?p=4527023&postcount=3](http://ubuntuforums.org/showpost.php?p=4527023&postcount=3)

Since you have 2 drives, and the PC boots straight to Vista, it sounds like your BIOS is set to boot the Vista drive, and you've installed GRUB on the other drive. To boot Ubuntu, try entering the BIOS menu and changing the boot order of the drives.

---

### Post by LewRockwell on 2009-08-01
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by nym1 on 2009-08-02
Thank you for the links unutbu, don't know how I missed that!! And of course for the information. Gonna go try that and see if it works right now!

If I may a follow up question (I am trying to learn and understand as much about the OS-interaction and such as possible); When I did the reinstall of Vista, did part of it's overwriting of the MBR include changing the setting in my BIOS to target that drive?

Or to ask it another way, when I initially installed Linux on the second drive, did linux make alterations as to which drive the computer boots in?

Just trying to wrap my head around what has occurred...

Thanks!!

nym

---

### Post by philinux on 2009-08-02
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Might help.

---

### Post by nym1 on 2009-08-02
Thanks LewRockwell for the link, it looks interesting!

nym

---

### Post by unutbu on 2009-08-02
> Or to ask it another way, when I initially installed Linux on the second drive, did linux make alterations as to which drive the computer boots in?

The Ubuntu installer (near the end of the process) asks where you wish to install GRUB (the bootloader). The default setting installs GRUB on the primary (boot) drive, even if Ubuntu is installed on a secondary drive. 

If that is what you did, then you should be seeing the GRUB menu.

If you install Vista after Ubuntu, then Vista will overwrite GRUB with its own bootloader. This bootloader will kick you directly into Vista with no option to boot Ubuntu.

To fix this, you then need to reinstall GRUB. There are many ways to do this.
philinux has mentioned [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351),
and LewRockwell has mentioned [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/).
You may also find more details here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you'd like more details tailored to your situation, it would help you if run
[boot_info_script]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")
and post the RESULTS.txt file here.

---

### Post by nym1 on 2009-08-02
unutbu,

Ok, I have changed the necessary setting in my BIOS, and the grub loader did show up fine. Ican now get into ubuntu no problem - however, I am now getting the following error when I select the option to get into windows:

"Starting up ...
BOOTMGR is missing
Press Ctrl+Alt+Del to restart"

Not sure what I need to do in that case?

Any help would be appreciated 

nym

---

### Post by nym1 on 2009-08-02
> **nym1 said:**
> unutbu,

Ok, I have changed the necessary setting in my BIOS, and the grub loader did show up fine. Ican now get into ubuntu no problem - however, I am now getting the following error when I select the option to get into windows:

"Starting up ...
BOOTMGR is missing
Press Ctrl+Alt+Del to restart"

Not sure what I need to do in that case?

Any help would be appreciated 

nym


Sorry, sent this last one before I saw the last post - I will dig into it a little more... If I cant get it running, it will post the text of boot info as requested.

I did did find philinux's linked page and followed those instructions before posting to this site, but even though the process said it was successful, grub still did not appear when I restarted my system... 

 Thanks to all who are lending a hand!!!

nym

---

### Post by LewRockwell on 2009-08-02
> **nym1 said:**
> unutbu,

Ok, I have changed the necessary setting in my BIOS, and the grub loader did show up fine. Ican now get into ubuntu no problem - however, I am now getting the following error when I select the option to get into windows:

"Starting up ...
BOOTMGR is missing
Press Ctrl+Alt+Del to restart"

Not sure what I need to do in that case?

Any help would be appreciated 

nym

If I recall correctly, the SuperGrubDisk has the potential to fix these problems

Note: As with any new tool, procedure, and/or process...there is a learning curve involved. SuperGrubDisk is no exception to that rule.

HOWEVER: Once you've learned then you will wonder how you lived without it.

To wit: Try to live seven days without electricity, two days without food, and/or even one day without any liquids.

.

---

### Post by nym1 on 2009-08-02
Ok, I got it working!!!

Grub was obviously installed and working, since when I changed the hdd priority in BIOS, grub was able to load linux; The problem was me not understanding what I was reading. when in Grub in Terminal, I was running the setup command on the partion that the stage1 was found in, not 'hd0'. So, did 'setup (hdo)', and I am back in action!!!

I must say, I am new to the world of linux, and was worried that it would be way over my head. But in between the excellent documentation online, and forums such as this who don't outright flame noobs and actually do their best to genuinely help (and in a non-condescending way), I feel more more confident that I will be able to master this OS.

A hearty Thank You to unutbu, LewRockwell, and philinux.!!!!

nym

---

### Post by SuperSonic4 on 2009-08-02
> **nym1 said:**
> unutbu,

Ok, I have changed the necessary setting in my BIOS, and the grub loader did show up fine. Ican now get into ubuntu no problem - however, I am now getting the following error when I select the option to get into windows:

"Starting up ...
BOOTMGR is missing
Press Ctrl+Alt+Del to restart"

Not sure what I need to do in that case?

Any help would be appreciated 

nym

FYI it is probably because grub said vista was on your first hdd instead of the second (ie hd0 not hd1)

---

