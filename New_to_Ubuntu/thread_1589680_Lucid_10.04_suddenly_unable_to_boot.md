---
title: "Lucid 10.04 suddenly unable to boot"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by swarup on 2010-10-06
My colleague is running Lucid 10.04 (dual boot with Vista) on his Dell desktop, and Lucid has been working beautifully since we installed it a month ago. Now all off a sudden, it won't boot. When we get to the Grub menu and select Lucid, it gives a bunch of computer code and then stops at the following code, which I am typing by hand using my own laptop:

```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built in shell (ash)
Enter 'help' for a list of built-in commands.
```

Beneath the above lines of code, there are several more lines where various attached devices are being identified. It is too much code to type here, but I see that for example the Dell USB Keyboard, the Logitech USB Mouse, and some other items are identified. At the bottom of the screen is a cursor. 

His Vista partition still boots up fine. And in Grub, even if I select Lucid in recovery mode, the boot process still gets stuck up and arrives at the same code which I typed here above.

---

### Post by jtarin on 2010-10-06
A quick fix is to use the Ubuntu CD to boot in to the "Try" mode and get to the Gnome desktop and using a terminal mount your installed Ubuntu partition and use the command ```
sudo update-grub
```failing that you will have to [reinstall Grub2.]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by swarup on 2010-10-06
> **jtarin said:**
> A quick fix is to use the Ubuntu CD to boot in to the "Try" mode and get to the Gnome desktop and using a terminal mount your installed Ubuntu partition and use the command ```
sudo update-grub
```failing that you will have to [reinstall Grub2.]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

I've been googling around and yes, it sounds like the problem is likely that grub needs to be updated or reinstalled.

I should probably know this :confused:, but could you please tell me what is the terminal command to mount my installed Ubuntu partition? Then I should be able to manage what you've suggested.

Once booted into the liveCD, there is probably also a way to mount the installed Ubuntu partition using gparted (the partition editor), isn't there?

---

### Post by drs305 on 2010-10-06
The commands are in the following post I created this week due to the large number of boot failures recently.

You may be able to get by with just reinstalling Grub2, but if not the full purge/reinstall instructions are there as well:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by swarup on 2010-10-06
I booted up into the liveCD, and identified the Ubuntu partition as being /dev/sda5 using gparted. In a terminal window, I then mounted the partition by doing

```
sudo mount /dev/sda5 /mnt
```

And confirmed in gparted that sda5 was successfully mounted.

When I then did 

```
sudo update-grub
```

I got the following output:

```
error: cannot find a device for / (is /dev mounted?)
```

I tried:

```
sudo grub-install --root-directory=/mnt /dev/sdX
```

And got the following message:

```
warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged. If you really want blocklists, use --force.
```

I do not think anything serious happened to the computer, and probably all that is need is somehow realignin GRUB to be able to identify the sda5 partition. For some reason, the above has not worked. Further steps? Is there still a short-cut way for me to get this solved simply, or do I need to do the full purge/reinstall?

---

### Post by drs305 on 2010-10-06
swarup,

If your Ubuntu installation is on sda5, these are the commands you would run from the LiveCD:

```
sudo mount /dev/sd**a5** /mnt
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

You can't update-grub from the LiveCD without using the 'chroot' procedure, as the command would be trying to update the CD's files, which isn't possible.

If the grub-install doesn't work, you will have to use the full chroot procedure in the guide I linked to in the previous post.

---

### Post by jtarin on 2010-10-06
Or you can find the #3 CHROOT method forreinstalling Grub2 from the link I provided. If you have Grub installed anywhere but the MBR it will complain ```
warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged. If you really want blocklists, use --force.
``` I use this method as I have Grub2 installed at /dev/sda5 and not my MBR.I use the Win7 loader to load Grub on /dev/sda5. If you use this method and want to install Grub to any other partition other than MBR skip step #10 as it will automatically install Grub to the MBR.

---

### Post by swarup on 2010-10-06
> **drs305 said:**
> swarup,

If your Ubuntu installation is on sda5, these are the commands you would run from the LiveCD:

```
sudo mount /dev/sd**a5** /mnt
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

You can't update-grub from the LiveCD without using the 'chroot' procedure, as the command would be trying to update the CD's files, which isn't possible.

If the grub-install doesn't work, you will have to use the full chroot procedure in the guide I linked to in the previous post.

Yes, I think I did what you say here (I didn't just leave the second line as "X"). But I might have put "a5" on the second line of code, instead of just "a". I'll try it again and see. 

If that doesn't work, then I think it'll be easier to just reinstall Ubuntu on the system, than to try to type in all those lengthy terminal commands for the full purge/reinstall. It is quite daunting, when you have to type all that and can't copy/paste anything. In 30 minutes there can be a fresh version of Lucid install and updated, and I can do other work in the meantime.

---

### Post by jtarin on 2010-10-06
Yes but then you would miss the fun experience if repairing your system  from the command line. :)

---

### Post by swarup on 2010-10-07
No doubt it is thrilling :)-- I'll see what sort of energy I have for it in the morning.

In terms of pure time though, I think it'll probably be faster just to reinstall Lucid.

---

### Post by swarup on 2010-10-07
> **drs305 said:**
> swarup,

If your Ubuntu installation is on sda5, these are the commands you would run from the LiveCD:

```
sudo mount /dev/sd**a5** /mnt
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

You can't update-grub from the LiveCD without using the 'chroot' procedure, as the command would be trying to update the CD's files, which isn't possible.

If the grub-install doesn't work, you will have to use the full chroot procedure in the guide I linked to in the previous post.

I did this again today, and it worked like a charm. Within two minutes the computer was up and running again. It is obvious now that I must have typed in incorrectly yesterday. Thank you. :)

---

### Post by drs305 on 2010-10-07
> **swarup said:**
> I did this again today, and it worked like a charm. Within two minutes the computer was up and running again. It is obvious now that I must have typed in incorrectly yesterday. Thank you. :)

You are most welcome. 

Hopefully the rash of recent boot failures as a result of upgrades will slow down. I don't think anyone has identified the specific reason for all the failures, but at least the forum members are getting quicker at being able to 'fix' things.

Happy Ubuntu-ing !

---

