---
title: "only 1 hard disk"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by ~The~Killer~ on 2009-08-20
Hello. 

I've received my CD ubuntu 9.04 , I am currently using vista and I have only 1 hard disk "C:/" 231GB I have 150GB Free. 

I want to install ubuntu How can i do that and I have only 1 partition ? and How to make vista/ubuntu on my laptop. I don't want to delete Vista. 

Thanks for help

---

### Post by drs305 on 2009-08-20
Welcome to Ubuntu and the Ubuntu forums. :-)

During the installation from the LiveCD, in Step 4 you can choose "side by side will Windows". The installation with take some of the Windows space to create the necessary partition(s). You can also make the partitions before using the installation disk and select manual partitioning.

Here is an important point. If you select the "side by side partitioning", you need to use the 'partitioning bar' at the bottom of the page and use the slider to set the size of the Ubuntu partition. Otherwise it defaults to a partition size of 2.3GB, which is not large enough. Make the Ubuntu partition at least 10GB. If you want to split the space with Windows, you could safely split the free space between Windows and Ubuntu.

Refer to this post for an explanation of how to avoid the common mistake which results in a 2.3GB partition:
[http://ubuntuforums.org/showthread.php?p=7658271#post7658271]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

Here is a link to the Jaunty installation guide:
[https://help.ubuntu.com/9.04/installation-guide/i386/index.html]("https://help.ubuntu.com/9.04/installation-guide/i386/index.html")

---

### Post by Cheezespread on 2009-08-20
Hi ,

You can try [Wubi ]("http://wubi-installer.org/")

Or

You can free some space using the Disk Management within Vista; which you can do with the following steps.

1. Right click on your My computer icon.
2. Click on Manage. This will give you the Computer Management screen with the options available.
3.Under Storage you will find " Disk Management "( Doing this from Xp , i believe the same would be there in Vista ).
4. You can shrink the disc space by selecting your current C drive and leave the free space as unallocated.
5.If you are not allowed to do so , you can always defrag once and try again.

You can continue with the Ubuntu installation and use the free space available.

---

### Post by ~The~Killer~ on 2009-08-20
WOW You guys Rock :guitar: Great help from Great members . 
Gonna use that Thank you . Ubuntu i am coming wait for me :guitar:

---

### Post by ~The~Killer~ on 2009-08-20
Hi guys,

I've installed ubuntu. 

I have some questions : 
- when I start there are 4 options ;
ubuntu-kernel 
ubuntu-kernel (mode)
-ubuntu - dunno what :p
and vista

I want to choose ubuntu so I went with ubuntu - kernel is that good ? or shall i go with the 3rd option ?

-when I install something where I have to put it in C? or in the ubuntu hard disk ? 

Thanks - please if i need to know anything help me

---

### Post by philinux on 2009-08-20
The top option is normally the default. It will boot this if you leave it. I think the countdown timer is set to 10 seconds. 

At this grub screen if you just hit enter it will boot the top one.

Have a read of this 
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
and read System>Help and support.
Thirdly the stickies on this forum are really useful.

---

### Post by tarps87 on 2009-08-20
The entires should be something like:
Ubuntu *version*, kernel *version*
Ubuntu *version*, kernel *version* (recovery mode)
Ubuntu *version* memtest86+
Vista *(don't now what this look like)*

1) This should be used to boot Ubuntu
2) This should be used to recover a broken install
3) This can be used to test you computers memory
4) Vista

Note: When Ubuntu updates and there is a kernel updated included this list will grow, basically just select the highest version number. You can uninstall older versions to remove them from the list using synaptic.

---

### Post by jrox717 on 2009-08-20
>  when I install something where I have to put it in C? or in the ubuntu hard disk ? 

When you installed "side by side with Windows", what the computer actually did was shrink your Vista partition and create an Ubuntu partition. Basically having multiple partitions makes your computer think they are different harddrives, even though they are on the same disk. It's very common for Linux (and sometimes Windows) users to have multiple partitions so they can have multiple operating systems on one computer. 

So, when you're working on Ubuntu, you will save files to your Ubuntu partition by default. However, you can also access the files in your Vista partition by going to Places > xxxGB Media (where xxx is the size of your Windows partition). You can even save files there if you want, though you don't have to, and you shouldn't install your Ubuntu applications there.

---

