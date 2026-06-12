---
title: "Backing up GRUB, dual-booting"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by psychx on 2010-08-16
I am going to dual-boot, with XP as the secondary operating system. In case you're wondering why, it's just to play a few games that have had trouble on Ubuntu. I have just a few questions, then I'll be on my way.

1. How do I backup my GRUB loader? I went to /boot/grub/menu.lst which I found from a tutorial on a website. But, there is nothing in there.

2. What can I use to make the partition for XP?

3. How do I restore the GRUB boot loader? I have heard that XP will take over the system and only boot into XP, and that I would have to restore GRUB in order to boot into either.

I have Linux installed first. I'm running Ubuntu 10.04 LTS, and have Gnome and KDE installed. Thank you for any help.

---

### Post by Cavsfan on 2010-08-16
/etc/grub.d/ is where a lot of stuff is.
/usr/share/images/desktop-base/ is where any custom wallpaper/pictures would be.

/etc/default/grub contains default line, timeout and resolution.

You might like the customized grub2 tutorial in my signature.

At the bottom of it is an example of how it will look.
I dual boot Windows 7 64bit and Ubuntu 64bit.

Let me know if you have any questions.

---

### Post by Cavsfan on 2010-08-16
There is usually a problem when you install Ubuntu first as Windows like to rule everything.
After you load Windows XP, you can probably use the Ubuntu CD/DVD to recover your ability to boot into Ubuntu.

And my tutorial should fix you up after that.

---

### Post by psychx on 2010-08-16
> **Cavsfan said:**
> /etc/grub.d/ is where a lot of stuff is.
/usr/share/images/desktop-base/ is where any custom wallpaper/pictures would be.

/etc/default/grub contains default line, timeout and resolution.

You might like the customized grub2 tutorial in my signature.

At the bottom of it is an example of how it will look.
I dual boot Windows 7 64bit and Ubuntu 64bit.

Let me know if you have any questions.

I do like that grub tutorial that you provided. Now, I'm just wondering - what should I use to partition the space for the windows xp install? And, will I have problems with the loader when I first install XP? For example, having to run the live-cd for Ubuntu to get back into it, and restoring grub?

I don't mind having to format everything if it comes down to it - I would just like to avoid that. I have everything backed up on an external hard drive.

---

### Post by dagdeniz on 2010-08-16
1. [http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm) --> MBR backup
2. gparted on your live cd
3. [http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm) --> MBR restore (end of the page)

---

### Post by psychx on 2010-08-16
> **dagdeniz said:**
> 1. [http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm) --> MBR backup
2. gparted on your live cd
3. [http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm) --> MBR restore (end of the page)

Just two more questions: Where it says, hdx - is that x supposed to be a number? And, what is the "count=1 bs=512" or "bs=446" part of the command? I'm just wondering. It says that 446 will exclude the partition table from being written to disk.

I don't see any hdx (or hd0,1,etc) in /dev/.

---

### Post by dagdeniz on 2010-08-16
anywhere. just keep in mind that /home/username will not still be /home/username when backing it up as you'll be doing it with the help of the live cd.

edit: sorry, for my absent-mindedness, i didn't carefully read the last part of your post: 

512 and 446 seems to be partition tables included and excluded. you may want to add 446 if you change the partition tables (and in your case this is going to occur). 
and, try with sdx and with root privileges (sudo as usual or su if you have root user), generally like this:
```
dd if=/dev/sda of=/home/username/image count=1 bs=512
```the other command in the same manner, too. Try backing it up it now, if it doesn't work, group shell generally works with everyone 

(in live cd install grub then run in terminal 
# grub 
# grub > root (hdx,y)
# grub > setup (hd0)
# grub > quit
and reboot.)

---

### Post by oldfred on 2010-08-16
While you should have good backups anytime  you are editing partitions, you do not have to back up grub2 separately. You just reinstall from the liveCD. Boot liveCD and run these commands.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

or:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Be sure to install windows to a primary partition. It will not work from an extended partition unless you have another copy of windows in a primary partition.

---

