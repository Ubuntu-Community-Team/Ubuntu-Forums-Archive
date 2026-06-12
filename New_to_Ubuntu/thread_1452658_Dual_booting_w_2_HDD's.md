---
title: "Dual booting w/ 2 HDD's"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by synicalx on 2010-04-12
Hey all, long time no post!

Anyways I've just switched from a Wubi install of Karmic to a full install on a seperate HDD (40gb 2.5" Seagate). I figured I'd take no risks and unplug my main HDD while installing Ubuntu. All was going swimmingly until I finished the installation/updating, shut down and plugged my main HDD back in. Now on startup I get the choice of booting into Ubuntu or Windows 7, W7 boots fine (posting from there now) but Ubuntu will come up with a couple of lines of text saying "Continuing installation etc etc, press Esc to view more boot options" (can't remember exactly what it says, but it's something to that effect). 

When this happens, it'll stay on the Ubuntu logo for about 1 minute (in a lower resolution than normal) and then the screen flickers and goes black. The funny thing is that I can boot just fine when I unplug my main HDD!

Anyone got any ideas?

Btw, both drives are SATA

---

### Post by NCLI on 2010-04-12
I think reinstalling Ubuntu with both drivers plugged-in would be the easiest way to fix this. Your other drive is probably counted before your Ubuntu drive by the BIOS, and the Linux Kernel. 

This means that when you installed Ubuntu, the drive you installed to was seen by the kernel, and GRUB, as being Drive #1. Now that you've plugged the other drive back in, it's seen as Drive #2.

Just a guess, but it can't hurt to try a re-install.

EDIT: BTW, is this 9.10, or an earlier version?

---

### Post by e4uforums on 2010-04-12
I would second the above.  I just finished a similar installation with Win7 on one drive, Karmic on another, and a RAID1 array.  I kept all drives plugged in and the install went through great.

As you know the installer is very verbose when choosing which drive you want to install to.  The only real problem I see is actually choosing the wrong drive to install to - so long as you choose the correct drive you should be fine.

I'm sure there's a pro out there that could tell you how to actually "fix" this rather than just a "do over", but installing fresh will certainly get you up and running the way you'd like.

---

### Post by IndyGunFreak on 2010-04-12
> **synicalx said:**
> Hey all, long time no post!

Anyways I've just switched from a Wubi install of Karmic to a full install on a seperate HDD (40gb 2.5" Seagate). I figured I'd take no risks and unplug my main HDD while installing Ubuntu. All was going swimmingly until I finished the installation/updating, shut down and plugged my main HDD back in. Now on startup I get the choice of booting into Ubuntu or Windows 7, W7 boots fine (posting from there now) but Ubuntu will come up with a couple of lines of text saying "Continuing installation etc etc, press Esc to view more boot options" (can't remember exactly what it says, but it's something to that effect). 

When this happens, it'll stay on the Ubuntu logo for about 1 minute (in a lower resolution than normal) and then the screen flickers and goes black. The funny thing is that I can boot just fine when I unplug my main HDD!

Anyone got any ideas?

Btw, both drives are SATA

I'm curious to know... If you disconnected the drive during the new install, how would you expect it to know where to look for the new install?  You should have anticipated this problem... If you do a "clean" install, I would recommend going into Windows and completely uninstalling Wubi first.

I agree w/ both of the above posters for the fix.

---

### Post by synicalx on 2010-04-12
> **IndyGUnFreak said:**
> I'm curious to know... If you disconnected the drive during the new install, how would you expect it to know where to look for the new install?  You should have anticipated this problem... If you do a "clean" install, I would recommend going into Windows and completely uninstalling Wubi first.

I agree w/ both of the above posters for the fix.

Thanks everyone who posted!

Just to clarify, I unplugged the main HDD before installation and after un-installing Wubi. And yeah I'm using 9.10

I'll give a fresh install a go - only problem is I'll have to do it manually so I'll hunt around for a nice guide. Reason being the installer won't do an auto install on my 40gb because it only seems to detect the 500gb, however I can get it to see the 40gb under 2 conditions; 1. 500gb in unplugged (simple) or 2. I do it manually and explicitly point to the 40gb.

Thanks again for your help, I'll post back in a few hours once I'm home/have Ubuntu reinstalled :)

---

### Post by WinterRain on 2010-04-12
That is indeed strange. I have been dual booting by unplugging drives and installing for years, and have never had that happen. Keep us informed of your progress.

---

### Post by synicalx on 2010-04-12
Ugh sorry to post back again so soon, just wondering if anyone has a quick guide to using the 'Manual' option in the LiveCD's GUI? I can find tutorials on how to install with the 'Guided' options, but they won't let me select my 40gb HDD...

---

### Post by WinterRain on 2010-04-12
When doing a manual install, highlight the partition you want to use, and click "change" or "edit" (can't remember now) and make it "/". Not much else to do except hit next.

---

### Post by synicalx on 2010-04-12
> **WinterRain said:**
> When doing a manual install, highlight the partition you want to use, and click "change" or "edit" (can't remember now) and make it "/". Not much else to do except hit next.

Haha damn your smart :D

I was thinking I had to set /dev directories and all! But alas I always try to make things harder than they actually are...


EDIT:

Just got home and reinstall 9.10 manually - works perfectly!

Boot times a slightly more sluggish, but well worth it in the end.

Thanks for the tips guys ;)

---

