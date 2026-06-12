---
title: "Install Problem: Gnome Power Management"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by lupirius on 2010-05-02
I get this message when I start up ubuntu: Install Problem: the configuration defaults for gnome power manager have not been installed correctly.

I just reinstalled ubuntu through a partition. I am really knew to this but I think this might have something to with the fact that I only had about 40 Mb of space left on that partition. When I try to log in, it just sends me back to log in screen. There doesn't seem to be a terminal screen anywhere so i don't know how commands can solve this problem. I already tried removing the partition but it screwed up my computer to the point where there was just a grub recovery screen so I reinstalled it back in the free space which is now too small and can barely hold ubuntu. I can boot up with windows 7 now at least.

Can someone help me please? I have no idea what I am doing. I just want to get ubuntu back up and increase the size of the partition so that I can actually do something with it.

---

### Post by ddecator on 2010-05-03
> **lupirius said:**
> I just want to get ubuntu back up and increase the size of the partition so that I can actually do something with it.

For partitioning, you should be able to use a Live CD of Ubuntu, then use GParted to manage your partitions.

---

### Post by John Atypical on 2010-05-11
I just had a horrific few days with the same error; unable to boot and the prospect of two week's work lost. Linux really HATES a full hard drive. My 64GB SSD got stuffed to the gills by a rogue rsync command; think I made a mistake with the destination directory, so it just kept making copies of copies of copies on my hard drive until it was full. Result? GNOME Power Manager error you described. Booting with a live CD isn't an obvious fix because Linux file permissions prevent you from rescuing your files in this situation.

I fixed the problem by using the live CD (Lucid), and opening a terminal to get root by typing sudo /bin/bash.

Then used rm -r -v xxxx to remove the offending backup directory, which was absolutely hogging space.

rm = remove file/directory
-r = remove recursively; needed for directories as opposed to individual files
-v = verbose logging, so can see what's going on in the terminal
xxxx = path to directory you want to remove (look at gParted to get correct path to HDD).

If this helps you or anyone I'll be well chuffed.

---

### Post by Daremo_06 on 2010-07-28
> **John Atypical said:**
> I just had a horrific few days with the same error; unable to boot and the prospect of two week's work lost. Linux really HATES a full hard drive. My 64GB SSD got stuffed to the gills by a rogue rsync command; think I made a mistake with the destination directory, so it just kept making copies of copies of copies on my hard drive until it was full. Result? GNOME Power Manager error you described. Booting with a live CD isn't an obvious fix because Linux file permissions prevent you from rescuing your files in this situation.

I fixed the problem by using the live CD (Lucid), and opening a terminal to get root by typing sudo /bin/bash.

Then used rm -r -v xxxx to remove the offending backup directory, which was absolutely hogging space.

rm = remove file/directory
-r = remove recursively; needed for directories as opposed to individual files
-v = verbose logging, so can see what's going on in the terminal
xxxx = path to directory you want to remove (look at gParted to get correct path to HDD).

If this helps you or anyone I'll be well chuffed.

I have this exact same problem.

I found that the cdrom directory somehow is choking my machine.  I was running a recovery program for deleted files and somehow it was saving them there and filled up the drive.

I am attempting to do the steps listed above, but when I try to run ```
rm -r -v /USA and Canada 825.2159
``` from the root@ubuntu:/cdrom# directory all i get is

```
rm: cannot remove '/USA': No such file or directory
rm: cannot remove 'and': No such file or directory
rm: cannot remove 'Canada': No such file or directory
rm: cannot remove '825.2159': No such file or directory
```

It seems to me all i need to do is change the permissions on the folder and then delete the whole damn thing.  How can I do this booting off of 9.10 USB key?  

Thanks in advance!

---

### Post by WA4MOE on 2010-11-21
I have  the power manager problem. Have been attempting to reove it, change it, all kinds of methods. Still nothing. Either it replies with "Unrecognized command" or other error. 
It has been 3 weeks since I tried to install Ubuntu 10.04 and nothing works. Cannot boot from USB or live CD. It is totally unworkable and I'm just about ready to throw the whole thing in the dumpster. 
Wish I could get some real help. Have tried to search various forums and nothing helps.

---

### Post by dedlycow on 2011-01-10
Hello all
 I am having this problem also on my 10.04  acer aspire laptop.
 I have also searched but can not find a solution. Has any one found a way to fix this problem yet.
 Thanks Dedly

---

### Post by Panhead Bill on 2011-01-19
Add me to the list of people with this problem.
I did try to apt-get remove then apt-get install gnome-power manager, but still no go.

At least if I reformat and reinstall, I won't lose much as it wan a recent install.

---

### Post by dexaco on 2011-10-07
I just had this problem with a rogue backup. I used Parted-Magic 6.6 and booted from a CD I burned from the .iso download. Parted-Magic includes a file manager which allowed me to delete the rogue backup and free some (quite a lot, actually) space on the hard drive. Restart proceeded normally, and I could sort out the problem.

---

### Post by zengrz on 2011-10-07
> **Daremo_06 said:**
> 

I am attempting to do the steps listed above, but when I try to run ```
rm -r -v /USA and Canada 825.2159
``` from the root@ubuntu:/cdrom# directory all i get is...

Thanks in advance!

Isn't this the Tomtom map? :D

I am having the same problem =(

---

### Post by MontyMan on 2011-10-07
Looks like the issue is the spaces in the directory name.  Does anyone know what quoting characters Zengrz should use, in order to make Linux understand the directory name?

---

### Post by Krytarik on 2011-10-07
> **MontyMan said:**
> Looks like the issue is the spaces in the directory name.  Does anyone know what quoting characters Zengrz should use, in order to make Linux understand the directory name?
Of course; it's like you say, quotes. :P
Single and double quotes will both do, like this:
```
rm -r -v '/USA and Canada 825.2159'
```However, you could also 'escape' the spaces, like this:
```
rm -r -v /USA\ and\ Canada\ 825.2159
```

---

### Post by aviks on 2013-02-02
I am having the same problem. 

I think its with low space on the disk (since I got the message low disk space before I got this problem). I deleted some bulk files but prob didn't get fixed.

somewhere I saw some commands for fixing this (sudo apt-get --reinstall install gnome-power-manager & sudo apt-get install ubuntu-desktop) but the problem is I cannot connect to my proxy server. (before I had this problem every time I start my system I had to enter network keyring, is it related to this?)

Can anybody share some easy workout for this horrible nasty stupid thing ????

any help is appreciated.

---

