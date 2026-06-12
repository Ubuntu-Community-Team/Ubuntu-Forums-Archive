---
title: "Will reinstalling Vista on a dual boot system screw up Ubuntu/GRUB?"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by hoverX on 2009-03-31
Hi There,

I have a Dell XPS 1530 dual booting Vista and Unbuntu 8.04.  Vista might need to be reinstalled if I cannot fix a problem i've been having.  My question is this, will Grub and Ubuntu get screwed up if i try to reinstall Vista?  Keep in mind that this isn't a regular reinstall of Vista but on done with the Dell System Restore.

---

### Post by sonu 1807 on 2009-03-31
Yes, I restored Vista once with the Restore DVDs and Grub was erased (HP restore). But you can reinstall grub- 

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition nr is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.

---

### Post by maheshasolkar on 2009-03-31
Yes. And for times like these, I always keep a copy of Super Grub Disk handy. You can obtain one from:

  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Hope this helps.

---

### Post by hoverX on 2009-04-02
So i did the DELL image restore on my machine and as it turns out it does preserve GRUB and my Ubuntu install.  I didn't need to do anything special :) :)

---

### Post by raymondh on 2009-04-02
> **hoverX said:**
> So i did the DELL image restore on my machine and as it turns out it does preserve GRUB and my Ubuntu install.  I didn't need to do anything special :) :)

well done hoverx :)

---

### Post by Tschortscho on 2009-10-08
> **hoverX said:**
> Hi There,

I have a Dell XPS 1530 dual booting Vista and Unbuntu 8.04.  Vista might need to be reinstalled if I cannot fix a problem i've been having.  My question is this, will Grub and Ubuntu get screwed up if i try to reinstall Vista?  Keep in mind that this isn't a regular reinstall of Vista but on done with the Dell System Restore.

Hi hoverx,

Can I ask you about your set up? I have a Dell Studio 1537 running on Vista and I'm planning to install Ubuntu in a dual boot configuration. Before I do this, I would like to make sure I understand how the Dell Factory Image Restore behaves under these conditions; unfortunately I'm unable to find the answers I'm looking for, and a related inquiry on the Dell Community Forums is going unanswered... Are you still here? Can I ask you some specific questions? I assume that the hard disk configuration of the Dell XPS 1530 is not too different from the one of the Dell Studio 1537...

PS: I already had quite some experience with setting up dual boot configurations with Ubuntu (although this is my first time with Vista); in other words, I'm not a total newbie...

---

