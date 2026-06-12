---
title: "Windows vista killed my Ubuntu, can I restore my files?"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by orejasdemurcielagoflaco on 2011-03-05
I had Ubuntu 9 installed with Wubi in a Windows Vista, with a double boot. I was happy and life was good, but I had to use vista for something and while working in it got the blue screen and the computer shut down.

Now when selecting Ubuntu in the double boot, it just reboots again to the double boot. 

I assumed the blue screen damaged some sector in the disk, and tried the checkdisk and usual stuff from Windows, but got nowhere. Wubi only asks if I want to uninstall Ubuntu (which I don't until I can save my stuff)


Is there a way to restore or access the files I had in the Ubuntu partition? (did't had a copy of my email files) 

Thanks in advance,


Orejas de murcielago flaco

---

### Post by bcbc on 2011-03-06
What version of Ubuntu do you have. The 'rebooting' thing is actually common on 10.04 Wubi if you've updated grub packages (these are prompted automatically in Update Manager) or upgraded to 10.10. If you're on 9.10 then less likely.

Anyway - you can access your root.disk from Windows using [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) 

But depending on what version you are on, it's likely you could repair your Ubuntu. (See the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for more info)

---

### Post by wep940 on 2011-03-06
Please correct me if I'm wrong, as I've never used WUBI, but I believe there is no Ubuntu partition when you are running WUBI.  Rather, the ubuntu file system is known as a regular file to Windows.  It may not help any in your recovery, but at least it's a file within Windows versus a partition.  Someone may have some software somewhere to repair/recover it.

---

### Post by bcbc on 2011-03-06
> **wep940 said:**
> Please correct me if I'm wrong, as I've never used WUBI, but I believe there is no Ubuntu partition when you are running WUBI.  Rather, the ubuntu file system is known as a regular file to Windows.  It may not help any in your recovery, but at least it's a file within Windows versus a partition.  Someone may have some software somewhere to repair/recover it.
You are right. Wubi installs Ubuntu in a virtual partition, the root.disk.

You can find it as \ubuntu\disks\root.disk in Windows on the 'drive' you installed it on. e.g. c:\ubuntu\disks\root.disk
That tool I linked to can view the root.disk contents.

---

### Post by wep940 on 2011-03-07
Cool!  Someday I may try WUBI just so I know what it's like to install, start and uninstall.  Wouldn't really want to use it since I already dual-boot, but it would give me a little more experience with something I do see questions about on the forum.
 
Thanks!

---

### Post by orejasdemurcielagoflaco on 2011-03-08
> **bcbc said:**
> 

Anyway - you can access your root.disk from Windows using [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) 


Thanks so much, I was able to access my files and save them...

The link was VERY helpful, thanks a lot.

---

