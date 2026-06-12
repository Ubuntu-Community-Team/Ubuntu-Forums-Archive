---
title: "Copy files to usb via terminal with two OS"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by maggie_b on 2011-03-10
First of all I deleted firefox from my aspire one netbook running on linpus linux lite and it deleted my desktop so couldnt access or run anything, was just a black screen with internet search bar and tool bar at the bottom.

After searching forums I discovered the best thing to do was to run ubuntu netbook from usb so I could access the terminal to save my files before properly installing ubuntu netbook and erasing everything that was on there previously. Which is where I'm at currently.

So in short I have two Linux OS and need to copy files saved on linpus to usb from ubuntu terminal.

I am a complete newbie and will need talking through everything I'm afraid. Please help.

---

### Post by nothingspecial on 2011-03-10
You are going to need another usb stick to do this the very easy way. If you have one, plug it in and go to the places menu.

Find your computers file system and copy your stuff to the other stick. I'm unfarmiliar with linpus and the netbook remix interface but your files should be in the media folder and so should the other stick.

---

### Post by maqtanim on 2011-03-10
Welcome to the Community! :D

I don't think you will need any "terminal things" for copying files. I am making it very simple:
- Just gather two USB drives. One is for Bootable USB with Ubuntu, another is for backing up the current data.
- [Download]("http://www.ubuntu.com/netbook") Ubuntu Netbook Remix.
- Follow the [instructions]("http://www.ubuntu.com/desktop/get-ubuntu/download") (from step 2) to make a Bootable USB
- Now boot the netbook from Bootable Ubuntu USB.
- You'll find an option for trying it. Select that.
- Now from the left panel select the Files-Folder icon. Open any of them.
- When the file browser opens, from the left panel, go to the "Computer". You'll find your present data there.
- Copy the 'home' directory into other USB drive. Home directory is where all of your data usually stores (unless you choose different directory).
- After copying remove the second USB. Now you can install Ubuntu.

---

### Post by maggie_b on 2011-03-10
Thanks for the speedy reply,

Sorry for the confusion, but I know nothing. How can I find my computers file system? Is this all through terminal? Because I cannot access anything from the desktop other than through the terminal.

---

### Post by maggie_b on 2011-03-10
whoops, just seen the next reply sorry.....ok will try that, thank you.

see how it goes.

---

### Post by maggie_b on 2011-03-10
ok, I'm on the 'try ubuntu' desktop, selected files and folders, opened one up and in the file browser and couldnt see 'computer' so clicked on 'file system'. There is a file called home in there but it only has a file called ubuntu in there containing all the documents from this new os. I checked all the other files and it just seems to be everything from ubuntu, nothing from my linpus lite.

Have a missed a bit out?

---

### Post by nothingspecial on 2011-03-10
Is there anything in /media

---

### Post by maggie_b on 2011-03-10
no, nothing in media at all.

Is there any other way to try and find the files?

---

### Post by maggie_b on 2011-03-10
in file system there is another file called 'rofs' and there is a duplicate of all the files in file system, but still there is nothing in the 'home' file.

---

### Post by nothingspecial on 2011-03-10
Ok, lets do it the old fashioned way,

Find terminal in the accessories menu or whereever they keep it in netbook remix

copy and paste these 2 lines then copy what they say into a new post back here.

```
sudo fdisk -l
```
```
mount
```

---

### Post by maggie_b on 2011-03-10
after sudo fdisk -l

Disk /dev/sda: 160.0GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd91ac89e

     Device Boot     Start       End       Blocks     Id  System
/dev/sda1    *           1     19326   155236063+     83  Linux
/dev/sda2            19327     19457     1052257+     82  Linux swap / Solaris

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71517830

     Device Boot     Start       End       Blocks     Id  System
/dev/sdb1    *           1      3878     3908992+      b  W95 FAT32

---

### Post by maggie_b on 2011-03-10
you know, I think this is a bit too advanced and I need to set off for work in a bit, so think I'm just going to leave it and install ubuntu over the top and erase it. the files I wanted to save really are not worth all this hassle. Sorry to waste your time.

Thanks very much for your help.

---

### Post by nothingspecial on 2011-03-10
ok, but it's not really hard, I can show you what to do if you like. Have a nice afternoon at work :D

---

### Post by maqtanim on 2011-03-10
> **maggie_b said:**
> ok, I'm on the 'try ubuntu' desktop, selected files and folders, opened one up and in the file browser and couldnt see 'computer' so clicked on 'file system'. 
After opening the file browser, press **Ctrl+L. **An address bar will be appeared. Type **computer:///** there and hit the Enter. You should see your hard disc here...

---

