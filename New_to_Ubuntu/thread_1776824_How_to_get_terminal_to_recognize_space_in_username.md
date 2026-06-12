---
title: "How to get terminal to recognize space in username"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by SkydvrA35591 on 2011-06-06
I'm trying to get data off an old hard drive that crapped out on me in my Mac. I put it in an external case, but it doesn't spin up when connected to my Mac, but spins up on my Netbook which is dual boot Win7 and Ubuntu.

The hard drive mounts and I can see the folders, but I can't do anything with them. I get a message about not having permission.
I did a search and tried using Terminal, but I can't seem to get it to work.
In file manager I get **media/Macontosh HD** when I put the cursor over the drive name.

I am entering **sudo chown -R media/Macontosh HD** enter
Then I get prompted for my user password, which I input and hit enter
Then I get 'media/Macontosh' not recognized (or something similar)

I'm new to Linux and Ubuntu, I've only enter commands a few times on another OS and they were pretty simple. To me it seems like it is not recognizing anything after the space. In my searching I came across something that mentioned spaces could be tricky in the username, but found nothing on how it actually works.

Any help would be greatly appreciated.

---

### Post by Dondermans on 2011-06-06
Try Macontosh\ HD

---

### Post by collisionystm on 2011-06-06
> **SkydvrA35591 said:**
> I'm trying to get data off an old hard drive that crapped out on me in my Mac. I put it in an external case, but it doesn't spin up when connected to my Mac, but spins up on my Netbook which is dual boot Win7 and Ubuntu.

The hard drive mounts and I can see the folders, but I can't do anything with them. I get a message about not having permission.
I did a search and tried using Terminal, but I can't seem to get it to work.
In file manager I get **media/Macontosh HD** when I put the cursor over the drive name.

I am entering **sudo chown -R media/Macontosh HD** enter
Then I get prompted for my user password, which I input and hit enter
Then I get 'media/Macontosh' not recognized (or something similar)

I'm new to Linux and Ubuntu, I've only enter commands a few times on another OS and they were pretty simple. To me it seems like it is not recognizing anything after the space. In my searching I came across something that mentioned spaces could be tricky in the username, but found nothing on how it actually works.

Any help would be greatly appreciated.

One great thing about the terminal... You can use TAB to complete your commands. For example type cd /media/Mac*TAB* and it will auto complete for you with the proper syntax.
sudo chown -R <username> /media/Mac*TAB*

If you choose to do manually, the proper syntax is

sudo chown -R <username> /media/Macontosh\ HD/

---

### Post by collisionystm on 2011-06-06
Oh and BTW, I see this is probably a USB hard drive, correct? You cannot set permissions unless it is a linux file system, such as EXT4.

---

### Post by coffeecat on 2011-06-06
A few points. 

Your drive is probably formatted with the journalled version of HFS+ which is only readable out of the box in Ubuntu, not writeable which is one reason your 'sudo chown' command won't work. (It is possible to get hfs+ journalled writeable by installing another package and using a --force option with mount, but that's another story. I have a better suggestion below.)

The problem about not having permission is that the UID for your Mac files is probably 501, whereas your Ubuntu UID will be 1000. The way round that is to invoke root privileges, as you are attempting, but see below.

To escape a space in a terminal command, use the backslash (\) character. So "Macontosh HD" would be typed "Macontosh\ HD".

Anyway, the easiest way to copy your Mac files is to invoke a root nautilus with:

```
gksudo nautilus /media
```That will open in the media folder. Double-click on the "Macontosh HD" mountpoint and then you should be able to browse the HFS+ filesystem and copy your files using drag and drop.

One thing to beware of: using a root nautilus *might* change the ownership of all the copied files to root or it might retain the UID=501 ownership. Tbh, I'm not certain. If this happens a "sudo chown" on the copied files in the Linux filesystem will fix this.

---

