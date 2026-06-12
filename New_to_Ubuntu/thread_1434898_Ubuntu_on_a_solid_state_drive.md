---
title: "Ubuntu on a solid state drive"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Bob Appleby on 2010-03-20
I have an HP mini equipped with solid state drives. Ubuntu is loaded within windows on an 8 gig drive (windows is on another 8 gig drive) and it works very well. Wanting more space I purchased a 16 gig drive and loaded Ubuntu on it. Everything went just like loadeng the 8 gig drive. Then on booting into ubuntu the computer went to the grub boot loader. Why did it go to grub and more important, what command should I type to get grub to load ubuntu?

---

### Post by harrisonk on 2010-03-20
[SIZE=2]Hello

There is no problem here, the Ubuntu install just told grub to pop up every time the computer loads. As for your second question just hit enter to load the operating system you want.

If you want to hide the GRUB boot menu just find the entry in menu.lst for GRUB, The menu entry would look something like (I use GRUB 2 right now so this is from memory):

```

#show or hide the boot menu 1=show 0=hide
GRUB_BOOT_MENU_SHOW=1

```

In GRUB 2 go to synaptic and search for startup manager, then start it, it is locaded in the system -> Administration menu. It will ask for your password so just enter it.
At the bottom of the screen there will be an option that says:

Show boot splash if it is checked then uncheck it.

Just be sure that your SSD isn't the problem.

Harrison
[/SIZE]

---

### Post by Bob Appleby on 2010-03-21
I'll do that and see what happens. Glad it is that simple. Thank you very much.

---

### Post by Bob Appleby on 2010-03-22
Unfortunately hitting enter did not work. It just continued with grub. Another bit of information might help in solving the problem. It enters grub right after the ubuntu disk is ejected.

---

### Post by harrisonk on 2010-03-23
Hello

Are you trying to boot a cd? in that case you need diferent instructions.

What exactly do you see past the post screen?

Harrison

---

### Post by Bob Appleby on 2010-03-24
I'm not booting a CD. I'm trying to install ubuntu inside windows which I've  done successfully many times on two different 8 gig drives. With the 16 gig drive, everything proceeds normally up to and including ejection of the CD. At that point grub opens rather than continuation of the rather lengthy installation. 

The grub command linux results in a question about the kernel, which I don't know how to answer. It seems rather strange that a 16 gig drive works differently than and 8 gig. The main drive, in the netbook is also 8 gig on which ubuntu will install.

---

### Post by JKyleOKC on 2010-03-24
If you're seeing the word "grub" in the prompt, you're not at the grub menu but rather inside of grub's control program, which is asking what you want it to do...

I suspect that the cause of the problem, in such a case, is because replacing the 8 GB SSD with the 16 GB unit caused it to get a different UUID (a "universally unique identifier" which is a huge hex number shown as a string of digits), but the old UUID (of the 8 GB SSD) is still in grub's data as a possible destination. Since the old one isn't there any more, this confuses grub, which then asks you "What next, boss?" by posting that prompt.

The quick fix is to put the 8 GB unit back in, then wait for someone more knowlegeable about grub than I am to tell you how to respond to that prompt. This will give you back the use of your machine while waiting. Unfortunately there are two very different versions of grub out there, and the one you have is probably very different from the one on my 8.04 systems! It'll be easy to fix, once someone who knows the correct sequence of grub commands to type in appears, though...

---

