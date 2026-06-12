---
title: "copying files to cd or flash drive"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by Loren Bliss on 2010-12-28
I am trying to copy files to  a CD or a flash drive and find the process seemingly impossible in Ubuntu -- nothing even remotely like the process on Microsoft, which is simple, quick and easy. 

Can anyone please help? 

(I have found some Online instructions but alas I do not speak Nurdish; I am a professional writer/photographer for whom the computer is a Rube Goldberg office/darkroom/filing system but am otherwise a total computer-illiterate; in other words you'll have to assume I'm the archetypal "compleat idiot.")  

Thank you,
Loren Bliss

---

### Post by kroq-gar78 on 2010-12-28
Loren Bliss,

It is quite similar to Windoz, just that the external drives (flash drives, hard drives, CDs/DVDs, etc.) are on the left of the window/file manager.

First, go to where your files are in the file browser. Next, copy the files by right clicking on them and selecting "copy". Then, look at the left panel of the file browser. There should be something there with some sort of human readable name (most of the time). It should be next to something called "File System". Click on the flash drive. Next, paste the files by right clicking on the white space (folder which you just opened) and selecting "paste".

---

### Post by hhh on 2010-12-28
You can just drag and drop to the flash drive...

~In your file browser (Nautilus, part of Places), navigate to the file you want to copy.
~Plug the USB drive in, another instance of Nautilus should open and an icon should appear on your desktop.
~Drag and drop or copy and paste from one window to the other.
~Eject (unmount) the USB by right-clicking the USB icon on the desktop and choosing the right option.

-edit- sorry kroq. Figures, 40 people look at this thread without saying anything, and then I step on your toes.

---

### Post by Vi3tHoneyX on 2010-12-28
[COLOR="DarkRed"]And if you don't want to use either... Dropbox.com is really cool and useful! Just saying[/COLOR]. : )

---

### Post by tgalati4 on 2010-12-28
Well if you did speak Nurdish then you would do something like:

Open a terminal:

sudo fdisk -l

df -h

Say your flash drive is located at /dev/sde1 and mounted at /media/flash_drive

cd /media

ls -la

cd

sudo cp -r /home/lbliss /media/flash_drive

sudo umount /media/flash_drive

Now you can remove the drive.

As a professional writer, I presume that you can type.

---

