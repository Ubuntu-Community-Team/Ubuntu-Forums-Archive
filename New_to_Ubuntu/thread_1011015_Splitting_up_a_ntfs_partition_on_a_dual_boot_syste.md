---
title: "Splitting up a ntfs partition on a dual boot system?"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Nico-dk on 2008-12-14
So after a few hiccups. I managed to dual boot my new M1530 (xp / ubuntu), even having the media direct button as XP boot, and power button as grub.

HD0 now:
[COLOR="Navy"]xp - 70gb - Primary[/COLOR]
[COLOR="Red"]/ - 12gb - Primary
/home - 67gb - logical
swap - 3gb[/COLOR]

What I want:
[COLOR="Navy"]xp - 23gb - Primary[/COLOR]
  [COLOR="Blue"]  Games - 20gb - logical
  audio - 12gb - logical
  graphics - 15gb - logical[/COLOR]
[COLOR="Red"]/ - 12gb - Primary
/home - 67gb - logical
swap - 3gb[/COLOR]

Is this doable w/o screwing up any of my other partitions?
It doesn't matter if I'll have to do this from xp or Ubuntu, I'll be using a GUI based partition manager in either case.

---

### Post by taurus on 2008-12-14
I am looking at your "What I want:" and I am trying to figure out where do you get the space for games, audio, & graphics since your xp, /, /home, and swap are using up the same space as before?

---

### Post by Nico-dk on 2008-12-14
Ooops, forgot to mention, XP will be downsized and that space will be used for the 3 ntfs partitions.
XP should end up being 20-25gb

---

### Post by Nico-dk on 2008-12-15
I'll try again.
Can I savely muck around with the ntfs partition

---

### Post by Nico-dk on 2008-12-15
... using Gparted?

---

### Post by Nico-dk on 2008-12-16
So I decided to give this a try with Gparted tonight. Anyone want to contribute any thoughts?

---

### Post by Nico-dk on 2008-12-16
Last bump before dinner, tucking in the girls and the "operation"

You can still help out a newbie, before he possibly screws up both his XP and Ubuntu installation.

---

### Post by taurus on 2008-12-16
Back up your important files first.

---

### Post by vanadium on 2008-12-16
It is all possible what you want, but it is a bad idea which you will regret sooner than later. There is no practical use in splitting a small 70 GB partition in dwarf partitions. It will limit your flexibility. Splitting in several partitions is suited for larger server system.

It is not a standard operation, and while it is very well possible, it requires some technical knowledge.

In fact, this question does not belong to an absolute beginners forum.

---

### Post by caljohnsmith on 2008-12-16
> **Nico-dk said:**
> So after a few hiccups. I managed to dual boot my new M1530 (xp / ubuntu), even having the media direct button as XP boot, and power button as grub.

HD0 now:
[COLOR="Navy"]xp - 70gb - Primary[/COLOR]
[COLOR="Red"]/ - 12gb - Primary
/home - 67gb - logical
swap - 3gb[/COLOR]

What I want:
[COLOR="Navy"]xp - 23gb - Primary[/COLOR]
  [COLOR="Blue"]  Games - 20gb - logical
  audio - 12gb - logical
  graphics - 15gb - logical[/COLOR]
[COLOR="Red"]/ - 12gb - Primary
/home - 67gb - logical
swap - 3gb[/COLOR]

Is this doable w/o screwing up any of my other partitions?
It doesn't matter if I'll have to do this from xp or Ubuntu, I'll be using a GUI based partition manager in either case.
If your partitions are physically in the order that you list them, then I don't think you will be able to do what you want. If you shrink XP and want to use the extra space as an extended partition to hold the new logical partitions for audio and graphics, then you would have to get rid of your /home logical partition; you can only have one extended partition that can't be interrupted by a primary partition, and your 12 GB Ubuntu partition is in the middle (if your physical layout is as shown above). 

How about first opening a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
And please identify your partitions.

---

### Post by Nico-dk on 2008-12-16
Thanks a lot to all of you. Seems I'll have to do with one big XP partition, I guess I can still share some folders with Ubuntu (music and gfx), but from experience I don't like the idea of having stuff I like to keep on the same partition as a win installation. Then I'd rather do a clean reinstall/dual boot and downsize the xp partition significantly.

Caljohn, that's the layout.

Out from fdisk:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   161790614    80895276   d7  Unknown
/dev/sda2   *   161790615   185229449    11719417+  83  Linux
/dev/sda3       185229450   312576704    63673627+   5  Extended
/dev/sda5       185229513   306696914    60733701   83  Linux
/dev/sda6       306696978   312576704     2939863+  82  Linux swap / Solaris
```

sda1 = xp
sda2 = HH /
sda3 = ?? (didn't notice that before)
sda5 = /home

---

### Post by caljohnsmith on 2008-12-16
> **Nico-dk said:**
> 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   161790614    80895276   [COLOR="Red"]d7  Unknown[/COLOR]
/dev/sda2   *   161790615   185229449    11719417+  83  Linux
/dev/sda3       185229450   312576704    63673627+   5  Extended
/dev/sda5       185229513   306696914    60733701   83  Linux
/dev/sda6       306696978   312576704     2939863+  82  Linux swap / Solaris
```
I see one problem that I think you would want to correct before you do anything; your Windows partition is listed with a file system ID of "d7" instead of "7" which would be NTFS. You can correct that with:
```
sudo sfdisk -c /dev/sda 1 7
```
But the good news is you only have 2 primary partitions and 1 extended partition right now; that means you could shrink your Windows partition like you planned, and then create a single primary partition to hold Games, Audio, and Graphics. That might be better than having them in your Windows partition I would think. Anyway, let me know what you decide to do. :)

---

### Post by Nico-dk on 2008-12-16
Yup, 2 prim. During my first dual boot attempt, I had a Dell utils (Prim) before creating XP (prim), and then from xp creating 3 logical. This led to me not being able to create a prim for HH.

I like the idea of both HH and XP being able to access my music and graphics. If that's not do-able, I'll just do a new dual boot (could use the exercise) with a minimal xp (just for games). Then run paintshop Pro under Wine and only use HH for all my audio needs.

> **caljohnsmith said:**
> 
```
sudo sfdisk -c /dev/sda 1 7
```

Oooh, nice one. I thought it would recognized as ntfs out of the box.
... I'm still just learning all hte useful commands and switches.

---

### Post by vanadium on 2008-12-16
You can access your data on an ntfs partition without any problem from an Ubuntu installation. As long as you have a Windows system handy, there is no objection on using ntfs under linux for data storage.

Do not forget the power of linux symbolic links. You can create symbolic links to your graphics and audio in your home directory. These behave as true directories and make your data conveniently available right from within your home directory.

In addition to being convenient, it is safe. You reach your data without ever having to navigate windows system directories.

I am not sure why you hesitate putting the data on the Windows installation partition. Anyway, shrinking the ntfs partition and creating an additional one remains a possible option. A warning again: you will need some technical skills to fix it all after the change in partitioning.

---

### Post by travis31 on 2008-12-16
> **vanadium said:**
> You can access your data on an ntfs partition without any problem from an Ubuntu installation. As long as you have a Windows system handy, there is no objection on using ntfs under linux for data storage.

When accessing Windows partition from linux just be careful that you do not change any system files when Windows is in hibernate. This might cause problems on the next boot.

And there are some good free software available to access linux partitions from Windows.

---

### Post by Nico-dk on 2008-12-16
Thanks for the input.

I think I'll do a clean dual boot severly shrinking XP. Since this will only be used for gaming, I might as well put all music and graphics in my /home partition ... That of course depends on how well Paintshop Pro works under wine

---

