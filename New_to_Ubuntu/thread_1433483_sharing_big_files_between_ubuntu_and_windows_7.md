---
title: "sharing big files between ubuntu and windows 7"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by vincentberenz on 2010-03-19
Dear all,

I have a laptop running both Karmic Koala and Windows 7 in two different partitions.
I have a third partition that I want to use to share files between them.

The thing is, some of these files will be bigger than 4GO, not allowing the use of FAT (if I am correct ?).

So I formatted the third partition in NTFS (using windows). But when if I copy files from Ubuntu to this partition, and reboot in Windows, the files are nowhere to be seen. Then if I go back to linux, same things, the files seem to have disappeared.  (note : I use "safely remove" before shutting down linux) (another note : same phenomenon if I copy files directly to the windows partition from ubuntu)

Was all this to be expected ?
If so, is there another way to safely share (big) files between windows and ubuntu ?

thanks a lot

---

### Post by coffeecat on 2010-03-19
NTFS is a perfectly good way of sharing files between Ubuntu and Windows. I've done that on all my machines for a few years now, including with Windows 7.

A couple of questions: how are you mounting the NTFS partition in Ubuntu, with the Places menu, with a line in /etc/fstab, or the mount command? If one of the last two, please post the code you are using. Also, I have to ask this, you are not copying files into the $RECYCLE.BIN folder, are you?

One point: it's best not to write directly into the Windows C: drive, that's what a shared partition is for. This was OK in XP, but Vista would sometimes behave oddly if you did (can't remember the details) and the same may be true of W7.

**Edit** I've done a bit of googling and it seems that some people have had this problem too - including on this forum. But the very few references I could find suggest that this is an uncommon problem. Unfortunately, the less than handful of relevant hits I could find were not resolved. So, any other information you can give will help. Have you tried copying with the terminal 'cp' command? This might give us a useful error message which you wouldn't see using the file browser.

---

