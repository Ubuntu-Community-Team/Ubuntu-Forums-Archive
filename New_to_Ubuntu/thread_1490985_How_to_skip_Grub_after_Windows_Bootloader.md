---
title: "How to skip Grub after Windows Bootloader?"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by sanoelk on 2010-05-23
When I boot up my computer, it displays the Windows Bootloader showing two options - Windows 7, Ubuntu.
After choosing Ubuntu, it goes to the Grub menu - where I have to select Ubuntu again.

Is there any way to skip the Grub part of booting up to Ubuntu? So that after selecting Ubuntu from the Windows Bootloader, it will automatically load up Ubuntu without going into Grub?

Thanks. :)

---

### Post by hansdown on 2010-05-23
Welcome to the forum sanoelk.

Is this a wubi install?

---

### Post by sanoelk on 2010-05-23
Thanks. :)
Yes, this is a Wubi install. Would that be a problem? :(

---

### Post by hansdown on 2010-05-23
> **sanoelk said:**
> Thanks. :)
Yes, this is a Wubi install. Would that be problem? :(

Probably not, I just don't have experience with that.

Sorry.

---

### Post by sanoelk on 2010-05-23
Too bad. I hope someone can help me with this.
I was thinking of removing Grub altogether, but I don't know if it's safe (besides I don't know how to).

---

### Post by sanoelk on 2010-05-23
WOW!

After researching on this issue I managed to find a solution for this.

So what I did was,

Open Terminal and type: gksu gedit /etc/default/grub

It would open the grub file in gedit. (It would also ask for your password.)

In the grub file, look for the line that says: GRUB_TIMEOUT=10

Change it from "GRUB_TIMEOUT=10" to "GRUB_TIMEOUT=0"

After that, save the changes made in the grub file. Close gedit.

Go back to the terminal. And enter this: sudo update-grub

I restarted my laptop and voila! no more Grub menu after Windows Bootloader!

What I did was I just hid the Grub menu for 0 seconds (as good as skipping it). ;)

This thread helped me a lot --> [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

But what I find weird in this thread is that it assumed that there is a # sign in front of the line GRUB_HIDDEN_TIMEOUT=0, because when I opened my grub file it doesn't have any. It says there on the thread that it is needed to hide the grub menu, but when I tried to reboot my laptop with GRUB_TIMEOUT=1 and without the # in front of GRUB_HIDDEN_TIMEOUT=0, it still showed the menu for one second.

So I figured that removing the # sign is not really enough to hide the grub menu. At least in my case. 


But I'm glad that i finally "skipped" the grub menu. :)

---

### Post by Zemblan on 2010-05-23
The # symbol at the beginning of line means that it's a comment. Any lines with that symbol in front are ignored by grub, the # symbol is used to indicate a comment in many config files and shell scripts.

---

### Post by sanoelk on 2010-05-23
Thanks for confirming that.

But yeah, I figured that out from the grub file in gedit. So what I meant was even if you don't make that specific line appear as a comment (by adding the #), it really doesn't have any effect in hiding the grub menu. :)

---

### Post by philinux on 2010-05-23
> **sanoelk said:**
> Thanks for confirming that.

But yeah, I figured that out from the grub file in gedit. So what I meant was even if you don't make that specific line appear as a comment (by adding the #), it really doesn't have any effect in hiding the grub menu. :)

The uncommented line is because grub detected  2 operating systems. Click the grub2 link below for more info.

---

### Post by sanoelk on 2010-05-23
> **philinux said:**
> The uncommented line is because grub detected  2 operating systems. Click the grub2 link below for more info.

It's all clear now. Thanks. :)

---

