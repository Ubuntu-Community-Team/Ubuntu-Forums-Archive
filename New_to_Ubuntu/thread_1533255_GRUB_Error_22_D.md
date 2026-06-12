---
title: "GRUB Error 22 :D"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by Wataru8675 on 2010-07-17
Heya, folks.

I'll just explain everything I did to get to this point...  I know GRUB Error 22 questions are fairly common, but I can't find any threads that answer my question...
I went to remove Ubuntu from one of my boxes.  I popped in my Lucid Live CD, went to GParted, and deleted everything that was Ubuntu-related, and expanded my Win7 partition to take up the new space.  I went to restart my computer and the _first thing_ I see is:

```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22
```I found that by hitting Ctrl+Alt+Del, I could get rid of this screen and get to my Toshiba screen that I usually see first thing when I boot (before GRUB).  Here I can hit F2 for Setup Utility and F12 for Boot Manager.  I can get into Boot Manager and can run a Live CD if needed.

Where would I need to go within Lucid's Live CD in order to uninstall GRUB, or tell it to not be my default manager, or whatever I need to do?  (EDIT:  I don't have a Win7 recovery disc...)  I'm currently posting from my other Ubuntu-only box, so I'll try and type a step-by-step as to what happens if need be.

Thanks for all your help, folks...'preciate it!
-Wataru

---

### Post by jtarin on 2010-07-17
You will need to reinstall Grub as you let it overwrite your MBR. Once this is done you have no choice but to use Grub. The only way to overcome this for Win7 is use a repair disk to rewrite the MBR.Next time use EasyBCD to dualboot.

---

### Post by Wataru8675 on 2010-07-17
I seem to be running into some issues trying to reinstall it...  I'm fine using GRUB, really, if for no other reason than the fact that I'm used to seeing it every time I boot up.  I found this thread ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)).

sudo grub did nothing, so I installed grub via sudo apt-get install grub.
Now when I type find /boot/grub/stage1, I get Error 15: file not found.

I'll try and sniff out another explanation for this while I'm waiting for a reply...but are there any ideas, or threads you know of off the top of you head that you can direct me to in the case that I don't find anything?

---

### Post by jtarin on 2010-07-17
Topic 13....[This page]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by bumanie on 2010-07-17
If you don't have a win 7 disk, go [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") and get a win 7 repair disk. I have used their vista repair disc and it worked fine repairing the bootloader and re-writing the mbr.

---

### Post by Wataru8675 on 2010-07-17
Sweet.  I followed Topic 13 to a T, using my Windows partition as the one being...whatevered...

Now I start up, see my Toshiba screen, and my GrUB menu just says:

error: file not found.
grub rescue> _

And I can type into grub rescue>...

---

### Post by Wataru8675 on 2010-07-17
Also, thank you Bumanie...I'm torrenting the recovery disc file right now.

---

### Post by jtarin on 2010-07-17
Good news again!

---

### Post by Wataru8675 on 2010-07-17
Great!  I got it done!  For reference for people searching, I'll summarize what I did:

I torrented the .iso to which bumanie linked me, and then burned that image to a disc.  I booted up using the disc, and used the command prompt (the option at the bottom of the screen).  There I entered "bootsect nt60 c: /mbr".  I then restarted, and Windows booted automatically.

Thanks for your help, folks!

---

