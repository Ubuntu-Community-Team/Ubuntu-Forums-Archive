---
title: "adding 3rd OS"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by manny43 on 2010-06-20
Hello friends

I have two hard drives in one pc.1st hd im running Ubuntu 9.10
2nd hd im running LinuxMInt 9.I would like to add Fedora 13 to existing 1st hd.
Do i have to edit GRUB after installing Fedora 13 or that will be done automatically
by Fedora at time of installation of new OS?If have to do any editing to GRUB then
i wont install Fedora(i'm a affraid to mess up things)Thanks for your tutorial.

---

### Post by Windows Nerd on 2010-06-20
Most Linux systems should play nice with your existing bootloader: the only OS that forcibly changes stuff is Windows (it overwrites Grub with it's own bootloader). It should be pretty safe, just make sure you don't delete your Ubuntu partition on your first drive by accident (This is where I am assuming you installed Grub; unless you changed it it defaults to that location. 

If you do mess up Grub it is quite simple to reinstall and Grub auto detects most all OSes (Linux OSes for sure). But since you don't want to edit Grub this is a last-ditch option. 

It should be fine.

Scott

Edit: According to [this]("http://forums.fedoraforum.org/showthread.php?t=196517") thread on Linuxforums Fedora will auto-install it's own GRUB and you will have to add Ubuntu manually. I'm not sure if this is true now (The thread was posted in '08 and things may have changed since then).

---

### Post by manny43 on 2010-06-20
Thank you very much for your help.

---

### Post by PPPilot on 2010-06-20
I'm running Karmic and Lucid on one drive each in there own partition and openSUSE 11.2 on another drive in it's own partition. All I had to do to make GRUB see them was to run
```
sudo update-grub
``` from the terminal, enter my password, reboot and all was well... I also noted that each version sees and uses all three swap partitions across the two drives...

---

### Post by -kg- on 2010-06-20
I'm quad booting Ubuntu, Fed 12, OpenSUSE and Vista on my laptop.  Ubuntu owns GRUB in the MBR.

I'm not sure how Fed 13's installation procedure goes, but there should be an option to install it's GRUB in it's own partition rather than the MBR.  That way, whatever installation currently owns GRUB in the MBR will retain that ownership, and all you have to do is boot into that installation and run the command;

```
sudo update-grub
```

...in the terminal.  If OpenSUSE has control, I don't know that SUSE has the "sudo" command, so in that case you would have to become Super User.  If Fedora has control, then just install as normal...GRUB will be updated for the other OSes automatically during the installation process. (I'm going to have to download and install F13 so I'm better able to answer these issues! :p )

> **PPPilot said:**
> I'm running Karmic and Lucid on one drive each in there own partition and openSUSE 11.2 on another drive in it's own partition. All I had to do to make GRUB see them was to run
```
sudo update-grub
``` from the terminal, enter my password, reboot and all was well... I also noted that each version sees and uses all three swap partitions across the two drives...

A note for you, PPPilot:

Unless you're doing it for a specific reason, you don't need 3 swap partitions.  All you need is one, and all three installations will use it.

---

### Post by PPPilot on 2010-06-20
Yes, I know that all three can use the same swap. I just thought it was interesting that all three versions add the three swaps together and use them as one even though they are on different drives....

---

### Post by manny43 on 2010-06-21
i messed up and now can only boot fedora,can not see ubuntu or linux.could you  help me please i need to learn how to reinstall grub so i can have the options to boot ubuntu linuxmint and fedora.thanks.

---

### Post by Windows Nerd on 2010-06-22
Boot up the Ubuntu LiveCD and run:

```
sudo update-grub
```

It will add all the OS entries back to Grub. 

I'm not sure if this will work, given that Fedora has now installed it's own Grub, but it's worth a try.

---

### Post by -kg- on 2010-06-22
> **Windows Nerd said:**
> Boot up the Ubuntu LiveCD and run:

sudo update-grub

It will add all the OS entries back to Grub. 

I'm not sure if this will work, given that Fedora has now installed it's own Grub, but it's worth a try.

It won't.  Ubuntu no longer owns GRUB Stage One in the MBR.  You would have to boot into Fedora and run the command in Fedora's terminal, and since Fedora didn't detect the other OSes on installation, I doubt even that would do any good.

As of Fedora 12 (which I have), its (Legacy) GRUB was not patched to detect subsequent GRUB stages on ext4 partitions.  In order to use it, you would have to make a special /boot partition formatted to ext3 in order for it to boot properly.  Why they had it set up that way, when there were versions of GRUB that would (like Ubuntu's) is beyond me.

I would have thought that subsequent releases would have this corrected, but that's the only reason I can think of that Fedora's installer would have not detected your other installations.  Did the installation instructions tell you that you needed a special ext3 /boot partition?  If so, that may be the reason, especially if your other OSes are installed in partitions formatted to ext4.

If "sudo update-grub" from the Fedora installation doesn't work (or if you had to have an ext3 /boot partition for it) (BTW, I can't remember whether "sudo" is supported under Fedora...you may have to become "superuser", then issue the command "update-grub"), you'll have to install GRUB from one of the other OSes that supports ext4 partitions.  A good guide to follow in this procedure is at the following page:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

This should hold true for Linux Mint as well as Karmic, since Mint is based on Ubuntu.  It all depends on which you want to have control over GRUB in the MBR.

I'm going to ***_have_*** to check out and install F13!  I need to find out things like this so I can give more informed advice in situations like this. :p

---

### Post by QIII on 2010-06-22
You have to "su" in Fedora.

I have Fedora 13 in a virtual machine, and I think it still uses legacy GRUB.  Unfortunately, I'm not at home to check right now.  I don't think the installation gives you the option to leave GRUB where it is, but arrogantly takes it on itself to muck around with it for you.  I may be wrong.

Anyway, take a look here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

There is a section on "Reinstalling from LiveCD" that should help.  I hope!

---

### Post by -kg- on 2010-06-22
> I have Fedora 13 in a virtual machine, and I think it still uses legacy GRUB.

It most certainly does, fer cryin' out loud!

[http://forums.fedoraforum.org/showthread.php?t=246005]("http://forums.fedoraforum.org/showthread.php?t=246005")

And it seems that the default install still requires a separate /boot partition!  Not too "technologically advanced," considering that other distribution's GRUBs have been doing it for what...a year or so now?

By the information I've gleaned, though, I believe that GRUB2 is an installable option from their repositories.  And that might be an option for you.

Boot into Fedora and search their repositories for GRUB2.  Upon finding it, install it, and it will likely detect your other OSes, saving you the problem of installing the GRUB from one of your other OSes.

If not, nothing lost...it's back to installing GRUB from one of your other installations.

---

