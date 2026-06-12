---
title: "Installing ubuntu in Windows Vista"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by paker on 2010-03-24
1) I have a Vista laptop with 100 GB C: space. Can someone kindly give me a link to how-to-install ubuntu in Vista?

2) I need to have a folder in C: that can be accessed by both Vista and ubuntu. It contains music (mp3 and flac mostly), video (avi, mp4, mkv mostly), and image files (jpg mostly). Please give me a how-to link or key words for google search.

3) Vista shows C: has 50 GB available out of 100 GB capacity. When I double click on C:, I see 4 folders:

program files: 4 GB
sw setup: 3 
users: 2
windows: 8

Sum of these 4 folders is 17 GB, and I should have 83 GB available. But vista says c: is half full. What's going on?

Thanks.

---

### Post by uRock on 2010-03-24
The folder for Wubi would be hidden. This link should give you some insight as to what is going on. [http://wubi-installer.org/support.php](http://wubi-installer.org/support.php)

Cheers,
Ronnie

---

### Post by 3rdalbum on 2010-03-24
Do you actually want to run Ubuntu within a window on Vista? (Virtualisation)

Or dual-boot, where Ubuntu is actually running on the hardware?

If you want virtualisation, then go to [www.virtualbox.com](www.virtualbox.com). It's very easy to set up, including setting up a shared folder, but if you get stuck you can do a Google search for "Ubuntu in virtualbox".

If you want to do dual-boot, then first back up all your Vista files, burn the Ubuntu CD, go to your BIOS setup and tell it to boot from CD, and then actually boot up with the CD in the drive. When it asks you how you want to install Ubuntu, choose "Side by side", and drag the handle on the bottom bar graph towards the left until the new partitioning scheme looks alright (i.e. you've given Ubuntu as much room as you want).

Resizing might take a while. It might take a long time, like 5 hours, or it might take a couple of minutes. If you have defragmented your hard disk before installing Ubuntu it will probably be quicker rather than slower.

At the end of it all, when you reboot you'll be given the choice between Ubuntu and Vista. When you choose Ubuntu and boot up and log in, you can go to the Places menu and your Vista partition will be there; you just select that and you can access anything from there, including your folder of MP3s.

---

### Post by gordintoronto on 2010-03-25
> **paker said:**
> 2) I need to have a folder in C: that can be accessed by both Vista and ubuntu. It contains music (mp3 and flac mostly), video (avi, mp4, mkv mostly), and image files (jpg mostly). Please give me a how-to link or key words for google search.

3) Vista shows C: has 50 GB available out of 100 GB capacity. When I double click on C:, I see 4 folders:

program files: 4 GB
sw setup: 3 
users: 2
windows: 8

Sum of these 4 folders is 17 GB, and I should have 83 GB available. But vista says c: is half full. What's going on

The last question first: if you right-click on C: and select properties, it will tell you have many folders it has. I think it's more than 4. Change the settings in Windows Explorer to "show hidden files".

In Ubuntu, you can click on Places/Computer, and you should see your C: drive, probably identified as XXX.X GB media. You can double-click on it and browse through the directory structure. You should have full access to all files.

---

### Post by paker on 2010-03-25
I think I got enough details from your replies to install double boot. Thank you.

---

### Post by Mark Phelps on 2010-03-25
OK, but do NOT use the Ubuntu installer to shrink your Vista partition.  Doing so runs the risk of corrupting the Vista OS and rendering it unbootable.  

Instead, use the Vista Disk Management tool, and while it allows for less shrinkage, it also does not corrupt your OS partition in the process.

Then, when you install Ubuntu, choose the "largest free space" option and let it do its own partitioning in that space.

---

