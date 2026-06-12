---
title: "And even more Ubuntu questions"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by 29732 on 2010-08-16
hi everyone!
i have made another list of questions for everyone to answer! 

**_LIST UPDATED 08/17/10 9:48PM EST_**

1. How can i move some space from a partition to put it as space for another partition? (basically just make a partition i want bigger)
2. What is the difference between ubuntu ultimate edition and normal ubuntu?

more questions coming soon!

---

### Post by ankspo71 on 2010-08-16
Hi,
1. You can install clamtk, which provides a GUI for clam antivirus.

2. This would be the plymouth background. [http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)

3. Have you tried installing virtualbox guest addtions? You need to install it from within the GUI of virtualbox for it to be able to be used. This should help, but I'm not sure because I rarely use virtualbox.

4. I prefer vlc because it can play just about anything audio and video related. 

5. You must mean the docks. cairo dock, docky, and avant window navigator (AWN) are the three most popular.

---

### Post by 29732 on 2010-08-16
> **ankspo71 said:**
> Hi,
1. You can install clamtk, which provides a GUI for clam antivirus.

2. This would be the plymouth background. [http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)

3. Have you tried installing virtualbox guest addtions? You need to install it from within the GUI of virtualbox for it to be able to be used. This should help, but I'm not sure because I rarely use virtualbox.

4. I prefer vlc because it can play just about anything audio and video related. 

5. You must mean the docks. cairo dock, docky, and avant window navigator (AWN) are the three most popular.
on your answers:
1. what about avast?
2. thanks, ill try it out
3. i did, it still won't let me
4. i once changes the vlc's skin and accidentaly deleted the file and now it won't play (i am planning to reinstall it)
5. i'll try them out as well

and remember, more questions coming soon!

---

### Post by 29732 on 2010-08-16
ok now on number 2,
i meant when i boot ubuntu it shows me that ubuntu logo on a purple background and those 5 dots
i wanted to change the background on THAT

---

### Post by michaelaye on 2010-08-16
1. i dont use any antivirus but i heard clamAV is good.

2. i do not know how to do that.

3.  u need to add ur self to the vboxusers group. to do this go to System then Administration then go to Users and Groups. click on Manage Groups. Find the vboxusers. select it and click on properities. and make sure the box next to ur username is checked. u may have to restart the computer for this to take effect.

4. i use vlc for almost everything video related and rhythmbox for music.

5. u can use docks if u want, other then that i do not know.

:)

---

### Post by ankspo71 on 2010-08-16
Hi,
I don't know what to say about avast... What was the error message, so other people can help find the problem.
 
I see more and more people recommending bitdefender these days though. [http://www.bitdefender.com/business/antivirus-for-unices.html](http://www.bitdefender.com/business/antivirus-for-unices.html) Note that there is a link on the right side of the page where you can request a free license (for home use only).

I currently only use [http://www.virustotal.com/](http://www.virustotal.com/) to test suspicious files for viruses because I rarely have contact with untrustsble files. They scan each file you upload with multiple virus scanners.

I just saw your other reply too. Here's 2 links with more information on how to change the plymouth background.

[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)
(scroll down to "To create a very basic theme (wallpaper only) try the following:")
Note that this link also says the background image must be PNG images.

[http://digitizor.com/2010/07/04/how-to-set-your-desktop-wallpaper-as-the-gdm-and-plymouth-background-in-ubuntu-10-04/](http://digitizor.com/2010/07/04/how-to-set-your-desktop-wallpaper-as-the-gdm-and-plymouth-background-in-ubuntu-10-04/)

Hope this helps.

---

### Post by 29732 on 2010-08-16
the error is:
An error occurred in avast! engine: Invalid argument

---

### Post by JKyleOKC on 2010-08-16
> **29732 said:**
> 3. i did, it still won't let meThe "ose" version of vbox, that's in the respositories, doesn't support USB at all. You can go to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and scroll down to the instructions on how to add their location to your Software Sources list, then download the PUEL (Personal Use and Evaluation License) version, which **does** support USB and is totally free to use, even for commercial purposes.

There's a problem with the current version ( 3.2.8 ) of the PUEL version that makes USB devices unavailable for some users. It apparently depends on the specific hardware; I have this version installed on two boxes. On one of them, USB works perfectly; on the other, all devices are grayed out and reported as "unavailable." Bug reports have been filed with Oracle and it appears that they're working on it. They're quite responsive to most bug reports (3.2.8 came out less than a week after 3.2.6, to fix reported problems).

---

### Post by 29732 on 2010-08-16
so i have to wait until the bug is fixed?

---

### Post by 29732 on 2010-08-16
oh and 
[SIZE="7"]BONUS QUESTION![/SIZE]
Is there a program that is similar to windows indexing service?

---

### Post by JKyleOKC on 2010-08-16
No need to wait; your system may not be affected by the bug at all, and even if it is you won't be any worse off than you are now with the ose version. In addition, after you've added the Oracle site to your Software Sources, you'll be notified of all updates when they come out and can install them immediately.

As for an equivalent to the Windows indexing service, that's one service I disable immediately on any Windows setup I do, since I don't like its thrashing of my disk drives. Linux has something rather similar in the "locate" command, which depends on an index that gets updated every morning shortly after 7:30 a.m. on my systems. The Lucid version of Ubuntu includes a program called "catfish" which is even better; it doesn't bother with an index, but does a high-speed search across all mounted file systems. The drive on this system is 500 GB and a catfish search is almost instant in giving results.

---

### Post by 29732 on 2010-08-16
wow, catfish is FAST
and another question,
how can i burn cds or read info from them on virtualbox?

---

### Post by 29732 on 2010-08-16
oh and how can i play games on it without either immediately exiting it or resstarting the VM?

---

### Post by L2U2K2E on 2010-08-16
> **29732 said:**
> hi everyone!
i have made another list of questions for everyone to answer! 

1. What is a good antivirus for ubuntu?
I see no reason for one. 

> 4. Any good media player anyone? It's not winamp, but I like Banshee. Many others like amarok, although it seemed buggy in gnome when I tried it.

---

### Post by JKyleOKC on 2010-08-16
I've not tried burning CDs from vbox, nor gaming with it, so someone else will have to answer those questions.

If I need to burn a CD or DVD, I'll use the "shared folders" feature to copy the file or files from Windows into my Xubuntu host, and then use the burner from the host. I think that would be more reliable than dealing with the translation processes involved in virtualization, and copying to/from a shared folder is almost instantaneous for every file I've moved that way, some of which take several minutes to copy from one directory to another on the host.

I may have misled you about the speed of catfish; most of the 500 GB on my drive are still unused, so it's probably only searching 100 to 150 GB. That's still pretty speedy, though.

---

### Post by 29732 on 2010-08-17
my partition (out of a 320GB hard drive) is 75GB and i used it all up (25GB on my Win7VM, go figure) and on vista(which i dont use, my mother does)it is the rest of the hard drive
how can i move some of the vista's space onto ubuntu's?

and i don't know how to move a folder from the VM to ubuntu..
too confusing >.<

---

### Post by JKyleOKC on 2010-08-17
Changing the size of partitions is a tricky business, and always has the potential of losing everything. I don't recommend that beginners try it; even with all my experience, I don't attempt it myself! For starters, you need to have a full backup of everything just in case things go wrong, and replacing Windows from backups has its own set of problems.

With Vista and Win7 I understand that partition editing has to be done using their own tools, which won't recognize the Linux partitions. Otherwise the Windows systems don't work after the edit, as I understand the situation. It's a "catch 22" problem; either way one goes the result is possible disaster.

The 25-GB size of your VM sounds as if you created a fairly large virtual disk and chose the option that allocates all of it during the creation step. My virtual disks consume more than 80 GB total although none of them is more than half full.

To move a folder, you first create a "shared folder" in your VM. At the bottom of the VBox window is a row of icons for the disk, CD, USB, and so on. The one that looks like a file folder is for the shared folders. Click it, then click the single bold line that appears, to open the shared folder dialog (you can also do this from the VBox setting screen when the VM is powered down). Initially this dialog shows just a couple of lines and no folders, with some icons near its righthand edge. Click the topmost icon and you get an "add folder" dialog that lets you navigate to any folder on your host, and select it to be shared with the VM. You'll need to have full access to whatever directory you choose for sharing; I simply select my home directory by going to "/home" and highlighting my user name.

You then access the shared folders from the VM through Windows' "network places" window and open them like any other folder of the VM, once connected. From here, the shared host folders act like normal Windows folders in the VM and you can move files in and out of them. From the host, a shared folder remains a normal directory, so files moved in by the VM are accessible to the host.

It's very much like using a USB drive to move files from one system to another, but works much faster.

---

### Post by 29732 on 2010-08-17
> **JKyleOKC said:**
> Changing the size of partitions is a tricky business, and always has the potential of losing everything. I don't recommend that beginners try it; even with all my experience, I don't attempt it myself! For starters, you need to have a full backup of everything just in case things go wrong, and replacing Windows from backups has its own set of problems.

With Vista and Win7 I understand that partition editing has to be done using their own tools, which won't recognize the Linux partitions. Otherwise the Windows systems don't work after the edit, as I understand the situation. It's a "catch 22" problem; either way one goes the result is possible disaster.

The 25-GB size of your VM sounds as if you created a fairly large virtual disk and chose the option that allocates all of it during the creation step. My virtual disks consume more than 80 GB total although none of them is more than half full.

To move a folder, you first create a "shared folder" in your VM. At the bottom of the VBox window is a row of icons for the disk, CD, USB, and so on. The one that looks like a file folder is for the shared folders. Click it, then click the single bold line that appears, to open the shared folder dialog (you can also do this from the VBox setting screen when the VM is powered down). Initially this dialog shows just a couple of lines and no folders, with some icons near its righthand edge. Click the topmost icon and you get an "add folder" dialog that lets you navigate to any folder on your host, and select it to be shared with the VM. You'll need to have full access to whatever directory you choose for sharing; I simply select my home directory by going to "/home" and highlighting my user name.

You then access the shared folders from the VM through Windows' "network places" window and open them like any other folder of the VM, once connected. From here, the shared host folders act like normal Windows folders in the VM and you can move files in and out of them. From the host, a shared folder remains a normal directory, so files moved in by the VM are accessible to the host.

It's very much like using a USB drive to move files from one system to another, but works much faster.
ok and now as i understand it..
when i installed ubuntu, it let me install it side-by side, and it created it's own partition, nothing went wrong.
what steps does it do to do that?
and maybe if i install ubuntu again, i can make more space for my partition (it just would be three partitions and then format both partitions, and install ubuntu on the free space that i just made
is that possible? 

and as for the shared folders, i know how to get folders from ubuntu onto the VM, it's just i want to do the opposite: move a folder from the VM onto ubuntu

---

### Post by 29732 on 2010-08-17
or even maybe format just the extra space partition, and make it a /home partition
and i have everything backed up so no problem with that

---

### Post by 29732 on 2010-08-17
and adding to the list of questions.. 
is there a program that can burn lightscribe disks???

---

### Post by JKyleOKC on 2010-08-17
I've seen one, but lost its address. Try googling for "lightscribe linux ubuntu" and see what, if anything, shows up.

---

### Post by 29732 on 2010-08-17
ok 
anyway, 
i will have an updated list of questions on my first post, be sure to check it out!

---

### Post by 29732 on 2010-08-19
buump :/

---

### Post by uRock on 2010-08-19
> **29732 said:**
> ok 
anyway, 
i will have an updated list of questions on my first post, be sure to check it out!
Start a new thread with new questions. Constantly changing them in the first post will confuse people who may be reading the thread to find an answer.

---

### Post by 29732 on 2010-08-19
oh ok thanks

---

