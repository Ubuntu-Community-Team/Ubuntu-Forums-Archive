---
title: "Grub 2 GUI"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by dunklegend on 2009-12-04
What's the name of the application that lets you change the grub (Grub 2) in a graphical way?

---

### Post by cariboo on 2009-12-04
There isn't one yet, you can use startupmanager to change boot order, but thats about it. The person responsible for startupmanager is hard at word updating it so that it will work with grub2.

Startupmanager is in the repositories.

---

### Post by dunklegend on 2009-12-04
Thank you, that's what I was looking for.

---

### Post by dunklegend on 2009-12-10
I tried to edit the default OS with startupmanager, so Windows would select it as a default, but it still boots Ubuntu as a default.

Do you have a link of a step by step on how to edit GRUB 2?

---

### Post by QIII on 2009-12-10
ranch hand has put together a great compendium of all things GRUB2.

Take a look here.  He has given several links at the bottom.

[http://ubuntuforums.org/showthread.php?p=8191211](http://ubuntuforums.org/showthread.php?p=8191211)

---

### Post by ranch hand on 2009-12-11
You are probably looking for Start Up Manager.  You can try it at your own risk.

It is not ready for Grub2 quite yet.  There is one guy that is the developer.  Grub2 is completely different than grub-legacy.  SUM will get there.

Give the guy a chance, grub2 is still changing.  Kind of hard to hit a moving target.

If you forget every thing you know about grub-legacy and how "easy" it was to edit, you will realize that grub2, while it takes a little more to set up, is much easier in the long run to manage.

To blow my own horn, the link in my sig is a good place to start.  the first 3 links I provide are the best there is for in depth info.  The 2nd and 3rd are here on the forums and I know that drs305 has been working at experimenting and documenting since Karmic-testing-Alpha2 when grub2 was introduced.  We had kind of a rough ride at first.

Grub1.97 as opposed to grub1.97beta4 is in the repos for 10.04-testing.  It is even nicer.

---

### Post by dunklegend on 2009-12-15
Thanks QIII and ranch hand, I will take a look at the links and see if I can solve my problem.

---

### Post by oldfred on 2009-12-15
I thought you had to use numbers to select but you can use names:

If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

GRUB_DEFAULT="Windows Vista (on /dev/sda1)"

---

### Post by dunklegend on 2009-12-16
> **ranch hand said:**
> You are probably looking for Start Up Manager.  You can try it at your own risk.

It is not ready for Grub2 quite yet.  There is one guy that is the developer.  Grub2 is completely different than grub-legacy.  SUM will get there.

Give the guy a chance, grub2 is still changing.  Kind of hard to hit a moving target.

If you forget every thing you know about grub-legacy and how "easy" it was to edit, you will realize that grub2, while it takes a little more to set up, is much easier in the long run to manage.

To blow my own horn, the link in my sig is a good place to start.  the first 3 links I provide are the best there is for in depth info.  The 2nd and 3rd are here on the forums and I know that drs305 has been working at experimenting and documenting since Karmic-testing-Alpha2 when grub2 was introduced.  We had kind of a rough ride at first.

Grub1.97 as opposed to grub1.97beta4 is in the repos for 10.04-testing.  It is even nicer.

Sorry ranch, I've been reading a lot about GRUB2, and tried to edit some of the files, but I had no luck.

how can I put windows XP as the default OS?
My wife doesn't like that windows is the default option and if I don't change it fast I'll have to uninstall Ubuntu, and I don't want to do that.

Thanks in advance.

---

### Post by meho_r on 2009-12-16
> **dunklegend said:**
> Sorry ranch, I've been reading a lot about GRUB2, and tried to edit some of the files, but I had no luck.

how can I put windows XP as the default OS?
My wife doesn't like that windows is the default option and if I don't change it fast I'll have to uninstall Ubuntu, and I don't want to do that.

Thanks in advance.

oldfred already answered to your question in the post just before yours. Basicly, edit the line
```
GRUB_DEFAULT=0
```
in **/etc/default/grub** and instead of "0" put "1" or "2", depending on which place Windows entry is (if you have only Ubuntu and Windows installed, it is probably "1"), or even better, the full name of your Windows entry, as oldfred recommended.

After this change, don't forget to run:
```
sudo update-grub
```

For more infos, read the section named "grub (/etc/default/grub)" provided [here.](https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202)

---

### Post by drs305 on 2009-12-16
> **dunklegend said:**
> Sorry ranch, I've been reading a lot about GRUB2, and tried to edit some of the files, but I had no luck.

how can I put windows XP as the default OS?
My wife doesn't like that windows is the default option and if I don't change it fast I'll have to uninstall Ubuntu, and I don't want to do that.

Thanks in advance.

This guide will tell you how to accomplish some of the major changes a user would normally make:
[Grub 2 - 5 Common Tasks ]("http://ubuntuforums.org/showthread.php?t=1302743")

Look at Section 2.

---

### Post by dunklegend on 2009-12-17
This is what I get when I try to update grub


dunklegend@dunklegend-desktop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

and my default OS is still ubuntu, even though that in /etc/default/grub the default is 7 which is windows XP

---

### Post by drs305 on 2009-12-17
> **dunklegend said:**
> This is what I get when I try to update grub


dunklegend@dunklegend-desktop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: [COLOR="DarkRed"]**/boot/grub/default**[/COLOR]
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
**[COLOR="DarkRed"]Updating /boot/grub/menu.lst[/COLOR]** ... done

and my default OS is still ubuntu, even though that in /etc/default/grub the default is 7 which is windows XP

It looks to me like you are still using Grub legacy (i.e. /boot/grub/menu.lst). Grub 2 doesn't have a /boot/grub/default - you may have placed /etc/default/grub in the wrong folder (which matters only if using G2 anyway). Have you looked at the version on the boot screen? Grub legacy is 0.97, Ubuntu's Grub 2 is currently 1.97beta4.

You should also be able to check the version with "grub-install -v" but looking at the actualy title during boot is the most definitive answer to which one you are booting.

If you confirm you are actually booting from Grub and not Grub 2, post the contents of /boot/grub/menu.lst and we can help you set your default OS.

---

### Post by oldfred on 2009-12-17
I thought you said grub2, menu.lst is grub legacy. Just edit menu.lst and move your windows entry above the automagic area or it will get overwritten on the next update. (about at the top third is where automagic starts).

---

### Post by dunklegend on 2009-12-28
I am using GRUB2, I don't know why do I have some of the old files.
How can I clean GRUB legacy and just leave GRUB2?

---

### Post by drs305 on 2009-12-28
For online upgrades to Karmic, the Grub legacy files are retained in case the user wishes to revert to the older version. Once you are successfully using G2, you can delete menu.lst. However, in your case I would either rename it or move it until you are sure you aren't having any further problems with Grub 2.

---

### Post by ranch hand on 2009-12-28
> **drs305 said:**
> for online upgrades to karmic, the grub legacy files are retained in case the user wishes to revert to the older version. Once you are successfully using g2, you can delete menu.lst. However, in your case i would either rename it or move it until you are sure you aren't having any further problems with grub 2.
+127

---

