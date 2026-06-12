---
title: "Recovery from crash"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by Fallible on 2009-09-10
Hello, I am not a sophisticated user. I have been using 9.04 Jaunty Jackalope for several months and I've had a serious crash that limits severely the quality of my Ubuntu experience. I believe it occurred on or around the time I was experimenting with "Simple Backup", but near that time I was also attempting to transfer backup information from my desktop via a USB external hard drive via two encrypted volumes using TrueCrypt. 

I'm not sure whether it was a program conflict or I inappropriately interrupted the process, but now I have the following problems:
1) Recurrent insufficient disk space, despite deleting lost+found folders, Trash, running Janitor.
2) Configuration changes in appearance don't stick.
3) Wireless password information has to be re-entered each time.
4) Weird behavior in other programs, such as Firefox 3.52 (Shiretoko) and 3.0x, such as failure of search boxes to work, inability to store new bookmarks.

I have seen references to "recover mode" but can't find how to start it, and I'm not sure I'd know what to do if I did find it. Any advice would be most appreciated!

---

### Post by NightwishFan on 2009-09-10
As for recover mode, on the OS select screen (Grub) when your computer boots you can select "Recovery Mode". If such a screen does not appear it will say "Press ESC for Menu" and do so to access the list.

You can use the baobab disk tool in Applications -> Accesories. It will find out where all the space is taken by.

---

### Post by mapes12 on 2009-09-10
> I believe it occurred on or around the time I was experimenting with "Simple Backup", but near that time I was also attempting to transfer backup information from my desktop via a USB external hard drive via two encrypted volumes using TrueCrypt.Me thinks it's broken :(

How confident are you about a full reinstall? We can guide you and help you backup your critical data ahead of the task.

---

### Post by tgalati4 on 2009-09-10
Well, if you are out of disk space, linux will run slowly and painfully.

Try to get to a terminal and post the output of:

df -h

Anything that says Use% 100% is bad.

Backups take a lot of space because the backup image is usually created to /tmp and files are added to it until it is finished.  When done, then it is renamed and placed wherever backups are normally stored.

---

### Post by Fallible on 2009-09-10
Thanks for the help and advice. Proceeding to re-install. Fortunately, no critical data lost. Perhaps a little extra beverage at beverage hour tonight ...

---

### Post by tgalati4 on 2009-09-10
You must drink fast.  My minty installs take only 15 minutes.  My fastest install was 13 minutes on a core2Duo with fast disks.

---

