---
title: "List of important files in Ubuntu Linux"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by akelsall on 2010-06-21
I'm trying to delve deeper into Linux and starting to pick up things here and there about which files are the important ones to know. I've started a list, and I'm hoping others can add to it. 

If you feel there are files that users should know about (whether beginner, intermediate, or advanced), please add to the list. When it's all said and done, I'll compile them into an Open Office doc and post a link to it. 

Here's a start:

=======================

 ~/.bash_aliases  (store your personal aliases here. You can also put aliases in .bashrc, but some say it's best to keep aliases in a separate file. If you look in .bashrc, you'll see a few  lines that will look for and read the .bash_aliases file)

 ~/.bashrc (from what I've read about this file, it is a script, located in your home directory, that gets executed every time you start a shell. "It is sourced by the bash shell environment upon login/startup. The contents are read and the variables, functions and scripts are loaded that are contained within." (taken from [http://www.slackstuff.com/2009/08/bashrc-did-you-know-that-you-could-do-this/](http://www.slackstuff.com/2009/08/bashrc-did-you-know-that-you-could-do-this/))

/etc/resolv.conf (allows you to specify your own domain servers. Instead of using my ISPs domain servers, I use domain servers from OpenDNS). 

/etc/fstab (File System Table - a configuration file that contains information of all the partitions and storage devices in your computer. It's to by Linux to determine where to mount partitions on boot. It needs this because it can't guess what the partitions are and what to mount them to.

/etc/apt/sources.list  (a file Ubuntu Linux uses to determine where it may download programs for installation or upgrade). 

/etc/X11/xorg.conf (file used to store your video settings). 

/boot/grub/grub.cfg (NEVER modify this file. Make changes to this file via the files containted in /etc/grub)

/etc/default/grub   (this is where you modify settings related to grub. For example, whether or not the grub menu is displayed during boot, how long it is displayed before booting to the first item in the menu, etc)

/etc/grub.d/40_custom (this is where you can create custom menu entries for grub)

---

### Post by Paqman on 2010-06-21
> **akelsall said:**
> 
/etc/X11/xorg.conf (file used to store your video settings). 


This one's become a bit of a relic. It's not used by default on Ubuntu any more, although if you create one it will be used. So it's really only useful in the case of obscure display faults.

---

