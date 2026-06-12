---
title: "How to make Backup of Whole Ubuntu system+software+plugin+themes+compiz"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by piyushchandrakar on 2010-03-17
I love UBUNTU....i dont wanna lose it...

After Reinstalling windows how 2 boot ubuntu i.e installed via Wubi perviously on windows 7.

I am running Ubuntu 9.10 on my Laptop, where it installed via Wubi on Windows 7.

[windows 7 (C:)and ubuntu on the different drive(U:)(NTFS)*its not a dual boot as installed via wubi]. 

For some reason My Windows needs a reinstall but in this case i think i will also lost ubuntu because its installed via Wubi.

Part 1 -
****I need to back up all the data that is installed in ubuntu i.e. SMplayer,Graphical GTK theme,Compiz,Emerald. and its setting,means the whole ubuntu system. So that after installing windows and ubuntu as a dual boot (not wubi again)i do not need to configure and install the whole ubuntu data/software again. Its pain for me to downlad again and again the data for ubuntu [Coz low speed connection :-( ]

Part 2 -
****if it is possible that after Reinstalling windows i can boot into ubuntu that is previously installed via Wubi on different drive that please tell me, how could i do that.
****if it is not possible than please show me the way to do backup all the data,software,plugin that is downloaded.etc.

I need to back up the whole Ubuntu because after installing windows i am goin 2 format the ubuntu drive and make it to Ext4 that is currently NTFS and then i will install the Fresh 9.10 on that.

---

### Post by Pougnet on 2010-03-17
Follow this excellent guide [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087). Hope it helps.

---

### Post by raydeen on 2010-03-17
If you installed via Wubi, I *think* your entire Ubuntu installation should be easily backed up. It's been a while since I used the Wubi installer. According to the Wubi page, it should be installed at:

```

c:\ubuntu\disks\root.disk

```

I would think that backing up that file to an external drive and then replacing it later after you've reinstalled Windows and a basic Wubi/Ubuntu install, it *should* put things back the way they were. To be safe, I'd back up all your important home folder files first (Desktop, Documents, etc.)

Hopefully someone with some more experience can shed some light. Just remember that the external drive is going to have to be formatted as NTFS so that you can copy the Wubi install to it. FAT32 won't be able to handle a file that big.

---

### Post by jbalazs on 2010-03-17
[IMG]http://www.geekconnection.org/remastersys/ubuntu.html[/IMG]

---

### Post by jbalazs on 2010-03-17
[IMG]http://www.geekconnection.org/remastersys/ubuntu.html[/IMG][http://http://www.geekconnection.org/remastersys/ubuntu.html]("http://http://www.geekconnection.org/remastersys/ubuntu.html")

---

### Post by bwbloch on 2010-11-16
Can someone confirm what raydeen has advised above, that if you installed via Wubi, you can do a complete backup (OS, added software, etc.) by backing up c:\ubuntu\disks\root.disk in Windows?  (I'd rather do this than tar.gz.)

If one needs to recover from a crash, then you just reinstall Wubi and replace the new root.disk with the backed up root.disk?

Just want to make sure.

Thanks!

---

### Post by HavarN on 2010-11-16
I haven't tried it. But it should work, as long as the wubi bootloader (don't know if it is just grub) is reinstalled. Replacing root.disk should do the trick.

root.disk is basically just a raw hard disk in a file.

You can see its partitions and block-size with:
fdisk -lu root.disk

you would get something like this:
```
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    31999999    15998976   82  Linux swap / Solaris
/dev/sda2        32002046   976771071   472384513    5  Extended
/dev/sda5        32002048   976771071   472384512   83  Linux
```

From this you need to find the offset, at which point the ubuntu partition starts. In this example, the offset is 32002048 times 512 = 16385048576.

Then you can mount the Linux/ext# partition with:
sudo mount -o loop,offset=16385048576 root.disk /mnt
*Remember to switch the offset number with the correct number from your file.*

So, I guess what I'm saying is backing up root.disk is sufficient to keep your files.

---

### Post by Telos3K on 2010-11-18
[Heliode's method]("http://ubuntuforums.org/showpost.php?p=175981&postcount=1") for backing up seems to back up *everything*, minus what's excluded.  I (due to inexperience) seem to be not excluding enough -- for example, even though I'm excluding /media, I'm still backing up a lot of data files and running out of space.  I only want to back up the Wubi/Ubuntu OS files (plus, of course, the various installed programs, permissions etc.) to be able to recreate the OS in a dual boot in case of a system failure.  How do I do this?

Thanks!

---

