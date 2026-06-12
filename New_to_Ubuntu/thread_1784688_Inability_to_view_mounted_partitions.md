---
title: "Inability to view mounted partitions"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by avnd on 2011-06-17
Hello there!

I have installed Win 7 and 2 Ubuntus (both 11.04) on my hard drive on 3 separate partitions. Since yesterday, I've been facing the following problem on the 1st Ubuntu. 

Under 'Places' I'm able to see all the partitions under the name I've labelled them. But when I double-click any of them, instead of opening under the file browser (the way the used to before yesterday) and listing the files/folders in that partition, the name of the partition just vanishes from the list and is not to be seen again till a reboot. The same story follows on every reboot. Usually when I double-click, the relevant partition is mounted and is visible on the desktop too. Not so now. But, I have no problem opening the filesystem of the current Ubuntu.

The other Ubuntu install works fine though. It functions as it did before yesterday. Interestingly, I've updated both installs similarly and I've not installed any application outside of the repositories and I only browse with the 'no-script' enabled in Firefox.

So, when I double-clicked the label of the partition and it vanished and went to 'Disk Utility', I was able to see that all the 'vanished' partitions were actually mounted. The mount point was  at the 'Media' folder. So, when I went there, I was able to see the names of the 'vanished' partitions'. But I didn't know what files they were. I tried opening them with both 'File Browser'(Error Msg: The location is not a folder) and 'Text Editor' (Error Msg: Could not open the file. You do not have the permissions). 

I have no clue as to how to proceed. I'd be glad if someone could refer me to a relevant discussion (I was personally not able to find one) or offer me some guidance. Thanks and cheers!

P.S. I also tried running under the Classic Ubuntu instead of the Unity Desktop. The problem remains the same.

---

### Post by dargaud on 2011-06-17
What does this tell you ? ```
sudo fdisk -l
```

---

### Post by 3xp10r3r|X13 on 2011-06-17
To mount and dismount partitions following commands might be very useful for you:

To mount a partition open up your terminal and type:

```

mount /dev/xy -t auto -v /folder-you-want-to-mount-it-to

```In the first part you select the partition you want to mount and specify the format its filesystem has (in this case it is auto detect) The second part is the folder you want to mount that partition to.

To dismount it:

```

umount /dev/xy

```It is really umount not unmount!!! Well and yes, after that (meant is the "umount" command) just mention the partition you want to throw out of your (in this case it is "/dev/xy") system.


You should use the terminal to manage your partitions, once you're used to it it's much easier and faster than the graphical interface.

Questions?

---

### Post by _0R10N on 2011-06-17
Well, if you're able to see the partitions from other utilities, then it must be a problem of some nautilus extension.

You could run from a console
```
nautilus /media/XXXX
```

And then it will open a nautilus window to explore the files and folder inside the given partition.

---

### Post by avnd on 2011-06-17
> **dargaud said:**
> What does this tell you ? ```
sudo fdisk -l
```

 This is my output from 'sudo fdisk -l', Dargaud.

/dev/sda1 - the 'boot partition'. Has the Grub files.
/dev/sda2 - Win 7 partition.
/dev/sda5 - Swap space.
/dev/sda6 - Ubuntu (that has the problem in discussion).
/dev/sda7 - Ubuntu (that works fine).
/dev/sda8 - Data partition.

---

### Post by avnd on 2011-06-17
Thanks for the alternative, 3xp10r3r|X13. I'll surely try it, mate. In the meanwhile I'd love to fix the graphical interface thingy and figure out what went wrong with this. Any suggestions?

---

### Post by avnd on 2011-06-17
> **_0R10N said:**
> Well, if you're able to see the partitions from other utilities, then it must be a problem of some nautilus extension.

You could run from a console
```
nautilus /media/XXXX
```And then it will open a nautilus window to explore the files and folder inside the given partition.

I tried that command from the terminal, OR10N. I get the same error message as I did when I tried from the graphical interface. "Could not display /media/DATA. The location is not a folder".

P.S. DATA is the label of one of my partitions.

---

### Post by 3xp10r3r|X13 on 2011-06-17
I'm glad to hear, that the terminal offers a decent alternative for you. 

Your permission problem:

It's quite simple. You are currently logged in as a standard user, which means that you are not allowed to to any changes to your system directory, apart from /home/user which is apparently the directory you're assigned to. The thing you would need to do now is opening nautilus as a super user. Therefore just log in as root and run nautilus from the terminal. 

either:

```


root@pc nautilus

or

user@pc sudo nautilus

```

or, if using KDE:

```


user@pc kdesu dolphin

```

That way, you open nautilus or dolphin as the root user, which means that you have all privileges you are able to have. Including: doing changes to your system directories

That was the permission thing.

To have that added partition/hd mounted by default to your home directory, you would need to add it to fstab. (edit the options such as read and write etc..)

I hope you now how to do so (fstab is located in /etc/fstab)

---

### Post by avnd on 2011-06-17
I tried opening an image from the 'recent files' list and I get the error message "Could not load image xxx. Failed to open input stream for file".  If that's of any help. (I'll try googling it myself in the meanwhile).  @3xp10r3r|X13: Being a newbie and not knowing much, I'm a little iffy about logging in as root, mate. All I'm trying is to find out what could've possibly gone wrong since my previous stable settings, so that I could revert back to that. I'll take some time trying your help instructions and get back to you on how it turns out, mate. :)

---

### Post by avnd on 2011-06-17
Hello again!

I appear to have come to an understanding of what happended. I had made a few changes to permissions at the media folder for the grub files. I followed the instructions at this page. 
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
I apparently have done a mistake there. I don't know what though. In the previous page, under the heading &quot;Changing main Grub boot menu settings&quot;, after the commands, 
&quot;sudo chmod 777 /media/GRUBpartition/boot/grub/menu.lst&quot; and
&quot;sudo nano /media/GRUBpartition/boot/grub/menu.lst&quot;,
I sought to return the permissions (I have to admit that I did not have the fullest understanding of what I was doing), and was planning to run &quot;sudo chmod 744 /media/GRUBpartition/boot/grub/menu.lst&quot; (I was basing this on the instructions in the previous paragraphs under &quot;Copy boot files to the small Grub partition). But I accidentally pressed 'Enter' after typing &quot;sudo chmod 744 /media&quot;.

I guess this might be the reason to what happened.

I took a look at the permissions for the media folder under both the Ubuntu installs.
In the problematic install the media folder had the following permissions:
Owner  : Root:  Create and delete
Group   : Root:  List files only
Others  : List files only

In the working Ubuntu install the media folder had the following permissions:
Owner   : Root: Create and delete
Group   : Root: Access
Others   : Access

So, I tried running the following command,
&quot;sudo chmod 777 /media&quot; at the terminal.
Now, it is working as before. Normally. But the media folder now has the permissions:
Owner : Root: Create and delete
Group: Root: Create and delete
Others: Create and delete.

Seeing the permissions on the working Ubuntu that I have, I realise that by default the media folder only 'Access' permissions to non-root users. What command should I run to restore it to the default install permissions? I don't understand the numbering permissions system and did all that only following the instructions. So I'd be glad if someone could tell me the right numbers to enter following chmod and correct me if this doesn't seem to be the problem at all!

Thanks!   P.S. I tried going through the file permissions commands. I only see read, write and execute. What is the equivalent of 'Access'?

---

### Post by avnd on 2011-06-17
Hello again!

I changed the permissions for the 'media' folder by opening nautilus with root access through the terminal and change the permissions for the group and others to 'access' and things are working fine.  

Thanks to everyone who spared their time and offered help.  

Cheers! 

P.S. It'd be nice if someone could tell me what is meant by 'access' permission. I don't see any equivalent for it using the numbers 0 to 8 under chmod.

---

