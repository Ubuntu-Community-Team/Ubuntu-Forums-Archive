---
title: "Help with switching from XP"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by crazygameofpoker on 2011-01-28
Just a quick question (yes, I've looked all over for this, but I don't think I'm using the right search queries...). I'm switching from XP (bye bye Trojans) and I've already gone through the installation process and tried Ubuntu with my USB drive. Now I'm back on XP and wondering, is there anything else I need to do? Do I need to delete all of My Documents (which are backed up anyway)? How do I make sure I'm not "leaving anything behind"? Thanks very much.

---

### Post by mastablasta on 2011-01-28
back up any files you want to backup (data files), then you need to install ubuntu to your hard drive. if you plan to not use XP anymore then you just install to the hwole hard drive. it will automaticly reformat and reparittion the disk and in the process overwrite any data you had.

---

### Post by 1clue on 2011-01-28
You're planning on formatting the drive right?

Once you do that, there's nothing left behind.  If you didn't put it someplace else it's gone.

---

### Post by amsterdamharu on 2011-01-28
> I've already gone through the installation process Did you install wubi or install it on it's own partition(s)?

> and tried Ubuntu with my USB driveIf you haven't installed it yet I suggest booting with the live CD/USB and run the boot info script.
Start Ubuntu live CD/usb and download the boot info script.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Copy it to your Desktop (it usually is in Downloads).
Run the following commands:
```
cd ~/Desktop
sudo bash boot_info_script*
```To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
There should be a file on your Desktop named RESULTS.txt please post the content of this file here too using &#91;code]Your pasted stuff&#91;/code]
You can install Ubuntu and leave XP on it. I assume you have a running Ubuntu now so why not leave XP alone?

When you've used Ubuntu for a while and are a 100% sure you don't want XP anymore then you can remove it and reclaim the partition in Ubuntu. I have used Ubuntu/Fedora now for 2 years but still have XP on my machine because I found out that Ubuntu doesn't read some VCD/DVD I need for my work. It doesn't have a working QQ (chat software) now and never had a working pps.tv (streaming video) which I sometimes use to watch tv.

---

### Post by crazygameofpoker on 2011-01-29
Thanks for all of your help. I realize now that my question was pretty stupid. I went on and took XP off with it.

---

