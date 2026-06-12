---
title: "Installation detects XP, but Grub doesn't offer it after install"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by carusoswi on 2009-11-07
I installed Ubuntu Studio 9.10 this morning.  Clean install.
Towards the end of the installation, there is a screen that shows other operating systems (on my system, that would be XP Pro).

"If all your other systems are shown, it should be safe to write Grub to your MBR" or some such message appears.

I click ok, and installation completes.

The problem is that when I boot up, no option for XP appears.

What went wrong?

I tried reinstalling with no positive effect.

I have a backup of my 9.04 menu.lst which I'll have to search for, and I figure I can copy/paste the windows section into the 9.10 menu.lst to restore access to my XP OS, but why did this happen?

Caruso

---

### Post by wrgb2 on 2009-11-07
I don't think Grub 2 uses the menu.lst file anymore.  Have you tried:

sudo update-grub ?

---

### Post by philinux on 2009-11-07
> **wrgb2 said:**
> I don't think Grub 2 uses the menu.lst file anymore.  Have you tried:

sudo update-grub ?

+1 yes there is a known bug unfortunately where grub2 fails to put the windows boot loader into it's menu.

Running 

```
sudo update-grub
```

Should fix it.

---

### Post by carusoswi on 2009-11-07
> **wrgb2 said:**
> I don't think Grub 2 uses the menu.lst file anymore.  Have you tried:

sudo update-grub ?

Actually, when I rebooted after the third installation of 9.10, XP was there.  Glad you mentioned that Grub 2 doesn't use menu.lst.  I would not have known.  Probably would have made a mess of things.

I'm certain I'll grow into this 9.10 version, but I am experiencing frustrations, so far.

For example, the symbols in the upper right hand corner of open windows display three circles, one for minimize, one for maximize, one for close.  Three circles . . . why?  How is that an improvement. Those circles convey no meaning.  I'm use to the - x and or large box, little box to indicate what one can anticipate from a mouse click.  I don't get that.

Also, there are no desktop icons at the bottom right of my screen to switch between desktop one and two . . . is that gone, also?

. . . and the menu at the top of the screen is all encased under the main icon at upper left . . . I don't see the value of it, but I can certainly tolerate and get used to using it.  I guess I don't see the value in changing just for the sake of change, and other than change, I see no inherent value in these changes.

BTW, I didn't make a conscious choice to upgrade this morning.  I kept getting interrupted by the upgrade dialog box, finally clicked ok, and it broke my system . . . could not boot into Ubuntu, no choice but to install.

Thanks for your reply.

Caruso

---

### Post by wrgb2 on 2009-11-07
Sounds to me like your gdm config files are messed up.  See this thread: [http://ubuntuforums.org/showthread.php?t=1253012&highlight=reconfigure+gdm](http://ubuntuforums.org/showthread.php?t=1253012&highlight=reconfigure+gdm) for how to reinstall and reconfigure GDM.

---

### Post by parminder_mangat on 2009-11-07
what is difference between ubuntu studio and ubuntu gnome

---

### Post by carusoswi on 2009-11-08
> **wrgb2 said:**
> Sounds to me like your gdm config files are messed up.  See this thread: [http://ubuntuforums.org/showthread.php?t=1253012&highlight=reconfigure+gdm](http://ubuntuforums.org/showthread.php?t=1253012&highlight=reconfigure+gdm) for how to reinstall and reconfigure GDM.

. . . checked out that thread and don't see how that problem relates to mine.

I have now, probably, reinstalled the UbuntuStudio 9.10 OS six times this weekend, although not really due to any problem with the OS.  I'm having a problem getting Gimp 2.7.1 to work properly, and have resigned myself to just dropping back to the latest version of 2.6 until things get sorted out (for my purposes, the difference between the two isn't that great, although I am a risk taker and enjoyed using 2.7.1 which ran almost without flaw on my UbuntuStudio 9.04).

What I have learned concerning the missing XP entry in Grub after installation is that you have to do a cold boot, as in turn the system off completely, before the XP option will appear in the Grub menu list.

I don't know why this should be, but it is.

I had tried running the Update Grub, and, it always found my XP OS, but restarting did nothing to cure the problem.  Shutting down completely, then starting fixes the problem without even running the Update Grub option.

Perhaps this observation will aid in sorting out the problem.

As for my other minor complaints, they are really minor, and I don't know if they are specific to the Studio theme or not (since I have not played with the non-Studio 9.10 setup).

Caruso

---

### Post by carusoswi on 2009-11-08
> **parminder_mangat said:**
> what is difference between ubuntu studio and ubuntu gnome

I think there is no underlying difference.  Studio is packaged to automatically install those packages that would be of most interest/use to someone with an interest in multi-media production (and that would be me).

If you were already aware of all the multimedia offerings available, you could just load up gnome and install them from the repositories.

Additionally, there are some cosmetic differences, but, again, I'm guessing any of those could be applied to a gnome installation.

I cannot offer empirical evidence, but it seems to me that my system's audio worked better after I switched to Studio, but that's probably just because it needed whatever collection of packages Studio installs that gnome does not.

I switched to Studio and like it, so I'm sticking with it.

Give it a try.  You may like it, too.

Caruso

---

