---
title: "Windows XP and Ubuntu 9.04 on the same machine"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by smorton on 2009-06-20
I have a Windows XP OS and I want to install the latest version of Ubuntu desktop.  I don't like the dual boot idea.

If you install it via a virtual machine does it hog your resources?  I have 3 GB or ram, but my computer isn't as fast as I would like. (as lthough pretty fast)

Any thought/input welcome.

smorton

---

### Post by ~sHyLoCk~ on 2009-06-20
You can use within Windows using wubi, did you try that?

---

### Post by muteXe on 2009-06-20
When you create your VM you specify how much RAM you want to make it have. 1 Gb for your ubuntu should be enough.

---

### Post by smorton on 2009-06-20
How do you:

 use . . .  . within Windows using wubi, did you try that?

Thanks

sm

---

### Post by kendoori on 2009-06-20
WUBI will not allow you to use Windows at the same time as you use Ubuntu, unless you create a virtual machine for Ubuntu using something like VirtualBox. I actually did that as one of my intermediary steps.

I'm fresh off of this process, so here's how I did my baby steps.

1-Played around with LiveCD (no installation)
2-Installed WUBI, which gave me a bit of a dual boot type setup, without committing to repartioning my hard drive. I could easily go back to my day to day XP install at any time. Down side of this, is that if I wanted to move between OS, I need to reboot.
3-Migrated my WUBI install to a dual boot setup, and created a virtual machine for XP, that I now run from inside of Ubuntu. I have XP on a dedicated partition and Ubuntu on a dedicated partition.

XP runs very well as a virtual machine, and as mentioned by someone else in this thread, 1MB for XP is fine. 

I played around with the VMWare converter, but chose to do a clean set up of XP for my virtual machine.

I'm mostly commited to living in Ubuntu, but it's useful to have XP readily available in case I need it. VirtualBox's seamless mode works very well, so that XP just melds into Ubuntu UI wise.

---

### Post by smorton on 2009-06-20
Went to town and had ubuntu desktop downloaded when I got back.  Now I burn to a CD, right?  (not a DVD)

What is WUBI?

I want to use Windows as primary system now as I have to use it for my business.  I wonder how much memory/things like that ubuntu will hog?  I am thinking of going with the virtual machine, but that would be for ubuntu.

I guess 1 gb of ram is what I was told by someone.  I assume I can undo anything I do by going back to a restore points.

Thoughts/imput?

Thanks

sm

---

### Post by smorton on 2009-06-20
wubi.  What is it?  I have tried to find out and can't.

Thanks

sm

---

### Post by rcayea on 2009-06-20
If you are wondering what kind of tool it is, I would guess you could read that on the website. I would suggest going to the website and searching for info. I guess in basic terms it is an installer (?) for linux to run as an .exe program.

---

### Post by smorton on 2009-06-20
Yes, I went to the website and found it.  Sorry for being lazy.

Sm

---

### Post by bodhi.zazen on 2009-06-20
> **~sHyLoCk~ said:**
> You can use within Windows using wubi, did you try that?

No wubi is not virtualization. wubi is installing ubuntu into a file mounted in ubuntu in lo.

wubi does not require grub or resizing a windows partition but is otherwise dual booting.

---

### Post by bodhi.zazen on 2009-06-20
> **smorton said:**
> Went to town and had ubuntu desktop downloaded when I got back.  Now I burn to a CD, right?  (not a DVD)

What is WUBI?

I want to use Windows as primary system now as I have to use it for my business.  I wonder how much memory/things like that ubuntu will hog?  I am thinking of going with the virtual machine, but that would be for ubuntu.

I guess 1 gb of ram is what I was told by someone.  I assume I can undo anything I do by going back to a restore points.

Thoughts/imput?

Thanks

sm

You can run Ubuntu in say VirtualBox with 512-1024 Mb RAM. Start with 512 and increase if needed.

The only problem I have seen with VBox in windows is if you use a usb mouse, but I would imagine that was fixed.

---

### Post by markharding557 on 2009-06-20
if you just want to get the feel of ubuntu or any linux then virtualbox is a very good way of doing that without altering anything on your computer

---

