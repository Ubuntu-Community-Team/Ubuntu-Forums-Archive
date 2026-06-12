---
title: "Windows/Ubuntu Dual Boot File Permission Management"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by Intrepid27 on 2011-02-18
Hi everyone,

I'm new here... and brand new to Ubuntu (and Linux, for that matter) as well. I actually just installed a few hours ago, I'm now running both Windows XP and Ubuntu on my laptop.

One of the big reasons I wanted to get Ubuntu is to maintain a safe environment for my schoolwork. Over the past few months I got hit really hard with some big viruses on my windows OS, and it cost me a lot of trouble as far as my schoolwork goes (couldn't turn in assignments mostly). And the big thing is, I have no idea how I got those viruses. I'm a computer savvy person as far as I can tell, and I wasn't doing anything to warrant viruses... So to save myself future trouble, I thought it'd be a good time to try Linux.

Sorry for the long introduction, here's my question: From my understanding, and from what I can see just clicking around in Ubuntu, while running Ubuntu I have full access to all of my files/folders on the Windows partition. Now I know that Linux doesn't often get viruses, but that doesn't mean that while doing something on Ubuntu I won't download a windows virus. And if Ubuntu has access to my windows partition, that virus can go infect that partition. So then next time I boot up XP, i'm screwed. Can anybody tell me if this is true or not? And assuming that it is true, I'd really like to adjust the folder permissions for my windows partition. Specifically, while running Ubuntu, I want that there is no way I can access my windows partition. Essentially I'm looking for complete isolation between the two operating systems, so that if I want to transfer a file for example I have to use external media (thumb drive, cd, etc..).

I've been reading up on how to do this, both using the terminal, and just using folder permissions, but I can't seem to figure it out. Any help would be greatly appreciated, thank you!

/sorry for the huge post/

---

### Post by fabricator4 on 2011-02-18
> **Intrepid27 said:**
>  Now I know that Linux doesn't often get viruses, but that doesn't mean that while doing something on Ubuntu I won't download a windows virus. And if Ubuntu has access to my windows partition, that virus can go infect that partition. So then next time I boot up XP, i'm screwed. Can anybody tell me if this is true or not? And assuming that it is true, I'd really like to adjust the folder permissions for my windows partition. Specifically, while running Ubuntu, I want that there is no way I can access my windows partition. 

Not exactly true.  It's possible to download an infected file while running under Ubuntu, but it can't do anything except sit there until you delete it - it won't run under Linux.  The danger would come when you boot windows and then try to use that file.

You need to check everything and should have some anti-virus software on your windows installation.  You also need to have a firewall in place.

If you don't mount the windows partition nothing will be able to write to it.

Chris

---

### Post by Intrepid27 on 2011-02-19
Ok sweet. So then how do I make sure that I do not mount the windows partition?

Because then theoretically, when I run windows, I won't try to execute any files that are on my Linux partition, because it boots from an entirely different directory right?

I mean I'll still use virus scanners and firewalls and such, but it seems that if I don't mount the windows partition I should be pretty safe...

---

### Post by misterbiskits on 2011-02-19
> when I run windows, I won't try to execute any files that are on my  Linux partition, because it boots from an entirely different directory  right?I am not an expert but just wanted to say that my windows 7 doesn't even see and can't access the ubuntu (ext4) partitions.  So your safe from executing anything that might be on the ubuntu drives if you used a filesystem that windows doesn't recognize.

> how do I make sure that I do not mount the windows partition?Is the partition mounting itself at boot?  If not then it isn't mounted and all you have to do is ... not mount it. 
Of course, if you never mount your windows drives you won't have access to your windows files and folders from within ubuntu...
[this link]("http://ubuntuforums.org/showthread.php?t=1663329&highlight=prevent+partition+mounting") might be what you are looking for.

---

### Post by fabricator4 on 2011-02-19
> **Intrepid27 said:**
> Ok sweet. So then how do I make sure that I do not mount the windows partition?

Under Computer you'll probably see something like "xxx.x GB filesystem" and maybe the volume name.  This is the windows partition.  If you click on it, it will mount and open a window in Nautilus.  Don't click on it.  It may also appear under "Places"

If it's automounting at boot then it will appear under "/media/xxx.x filesystem" or similar.  If this is happening you can go into the file /etc/fstab and comment out the line that is mounting it.

> 
Because then theoretically, when I run windows, I won't try to execute any files that are on my Linux partition, because it boots from an entirely different directory right?


Correct, as long as the Linux partition is ext2/3/4 or something else that windows doesn't understand out of the box.  It's possible to get windows to see any ext partition as an ext2 partition by running ext2.exe, which is a filesystem driver.

> 
I mean I'll still use virus scanners and firewalls and such, but it seems that if I don't mount the windows partition I should be pretty safe...

More or less, though there's lots of other things you can do such as make your normal Ubuntu login a desktop only user.  That would mean you'd need to keep your current login as an admin user to get updates and install programs etc.  A desktop user also has limited ability to mount other filesystems.  By default I think it cannot mount another HDD (sda1 for example) but can mount USB drives, and even this can be disabled.



Similarly, you can make a normal user under windows and mostly use that.  Most windows users seem to make the one main administrator user and never bother further, relying on the firewall and the "a program is trying to install... Y/N" dialog boxes that pop up.

If your logged in user doesn't have the power to install and run rogue programs and get access to boot files, you reduce your chances of damage dramatically.

Also, as you've found out, it's important to have all your critical documents backed up regardless.  It might not be a virus next time: you could drop the PC and damage the hard drive for example, or it may just fail unexpectedly.

Chris

---

### Post by grahammechanical on 2011-02-19
Have you noticed that under Ubuntu you have to enter your password when you want to do certain things? This is one of the ways in which Linux stops trojans and worms from making unauthorized use of the computer. Internally, the Linux operating systems assigns processes certain levels of permission that will prevent a rogue process getting access outside of its own level.

A Windows program will not run on Linux. And a Linux program will not run on Windows. So, if you copied a rogue program from Windows to Ubuntu it will not run.

Imagine, in Windows you open an email which has an attachment that is a disguised exe file. You open the attachment and the exe file activates and sends a copy of itself to every email address in your address book. This has happened. Now, open that email in Linux and the exe file will not run because it is not complied to run on Linux. You will most certainly get a warning that the file cannot be run.

No one is saying that we can let our guard down but there is less to worry about.

Regards.

---

