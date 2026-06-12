---
title: "Copy programs and config?"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Da-Chosen-One on 2010-05-22
I believe I am going to have to reinstall Ubuntu as I have removed a package and nobody seems to be able to help me **(posted** [_[COLOR="Blue"]**here**[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1489893")**)** I have access to the Ubuntu 10.04 ext2 partition from my Windows 7 install and I was wondering: 

[B][CENTER]Can I make a full copy of all of the files on the partition, 
reinstall Ubuntu on that partition 
and paste all of the files back on top 
to try and restore all of my programs and settings. [/CENTER][/B]

Will it work? 
And if not what else can I do to atleast preserve part of my install?
    Thanks for reading, 
       Craig

---

### Post by Ozymandias_117 on 2010-05-22
You can ALWAYS back up your /home directory, which has all your configuration files for your programs (At least most of them).

/usr is where most installed programs would be, I don't know how it would work if you tried to back it up and just replace it in the new one (If you do try it, make sure you also get /lib and if you have them /lib32 - This has all the common library files you would have downloaded for programs).

/etc has the system configuration files - some of the programs you have may look here for their settings and crash if they don't find anything.

You may also want /var/games which has all your highscores and /var/lib since it's another spot for libraries may be useful.


You shouldn't need /bin /boot /cdrom /dev /media /mnt /opt /proc /root /sbin /selinux /srv /sys /tmp 


NOTE: I have no idea if what you're planning will work or not. But these are the folders I would back up if I was going to try it.

---

### Post by ankspo71 on 2010-05-22
Hi,
As long as you have enough room on your windows partition, you should be able to copy over as much as you like from your Ubuntu partitions while using the Ubuntu live cd. By default, windows can't read linux partitions, so using the ubuntu live cd is probably the best choice. 

Your /home directory is probably the most valuable to you so be sure to copy that one first if space is limited. 

The second most important folder to me is the /var folder, because it contains all of the deb files that belong to the packages that you have downloaded and installed through Ubuntu's repositories. If you choose to do a partial backup using this folder, then all those programs can be installed with one pass using this command in the terminal:
sudo dpkg -i /var/cache/apt/archives/*

Once you go to reinstall Ubuntu, it is usually possible to recover your existing installation by using manual partitioning. Once you get to that stage, you tell the manual partitioner to use the existing partitions as ext2 (or whichever filesystem type you used originally) but don't mark them to be formatted so it will save any extra existing data on there. Your original username and password will be required if you want to use the original personal home folder. If you choose to format your Ubuntu partitions, you will have the data that you copied over to your window's partition for you to copy back.
Hope this helps.

---

