---
title: "Disappointed ...."
date: 2009-07-28
forum: New to Ubuntu
---

### Post by m-v-p on 2009-07-28
This is a rather long story and it's far from being a positive one.
  I did want to "get the feeling" of Ubuntu before choosing it later on my new computer-to-be as it's only operating system and I just downloaded the latest version to try it out.
  For the record, I was running Windows. In goes the CD and a nice menu comes up with the options "Demo and install ... as dual boot" or "install inside windows".
  As I didn't want a double boot option yet, I choose "install inside windows"
  Installation runs fine and when finished, it ejects the CD. Then it asked me to reboot.
  I did so and what comes up ? A dual boot choice - and I didn't ask for that.
  But OK, let's try it and I choose Ubuntu.
  Up comes a kind of DOS, called GRUB. So perhaps I had to start something using the command line and I tried to find that. I DO know the usual DOS commands, but a simple DIR doesn't work as one might expect. Computer was stuck there.
  Then I thought it needed the CD to start. Rebooted with the CD inserted and up comes the installation screen again. Choose Install inside windows again - perhaps there was something wrong - but Lo ! Configuring possibilities ! Checked them all, such as keyboard. And yes, it started and showed some autoconfig screen.
  And when it's finished with that, my display turns black, there is no more keyboard or mouse and I had to switch of my computer manually.
  After rebooting in Windows I checked what had been installed. There is no trace of Ubuntu in Windows/ProgramFiles, there is no Desktop Icon. I checked the directories and all the exe files I can find are uninstall-wubi.exe and in /winboot : wubildr.exe. No wubi.exe as there is an uninstall for it - whatever wubi is or does.
  Not encouraging for a first experience I should say.:confused:
  Anyone knows a solution ?

---

### Post by nothingspecial on 2009-07-28
Dos commands are not going to work in linux.

So if you choose ubuntu, after the grub dialogue, what happens. Do you go to a command prompt?

Did you install the server or minimal version?

If you installed the full version log in with your username and password then type```


startx
``` 

If that doesn`t work try

```
sudo /etc/init.d/gdm start
```

Do you get a desktop now?

---

### Post by lisati on 2009-07-28
Hmmmm.... No offense intended, but wouldn't it have been better to choose the "demo" option?

---

### Post by 3rdalbum on 2009-07-28
Please read the documentation and release notes! They tell you that the "Install inside Windows" option will install Ubuntu as a dual-boot, of sorts. And they will also tell you that you can remove that dual-boot by using the "Add and Remove Applications" control panel in Windows, and choosing Ubuntu as the thing to remove.

Try removing Ubuntu using that method, and then boot up from the CD to try it out. If you want to install Ubuntu for real, double-click the Install icon on the Ubuntu desktop.

I don't know why you were stuck at the GRUB bootloader, or what the "autoconfig screen" was, but the most stable and most mature installation method is the one where you boot up from the CD and install it that way.

---

### Post by MelDJ on 2009-07-28
Try  scanning your disk in windows. boot into windows and go to my computer.  Right click the disk you installed ubuntu in. Click properties and go to tools. under error checking, press check now. After it has finished, restart your computer and then boot into ubuntu. :KS

---

### Post by Troll_the_Great on 2009-07-28
> **m-v-p said:**
> This is a rather long story and it's far from being a positive one.
  I did want to "get the feeling" of Ubuntu before choosing it later on my new computer-to-be as it's only operating system and I just downloaded the latest version to try it out.
  For the record, I was running Windows. In goes the CD and a nice menu comes up with the options "Demo and install ... as dual boot" or "install inside windows".
  As I didn't want a double boot option yet, I choose "install inside windows"
  Installation runs fine and when finished, it ejects the CD. Then it asked me to reboot.
  I did so and what comes up ? A dual boot choice - and I didn't ask for that.
  But OK, let's try it and I choose Ubuntu.
  Up comes a kind of DOS, called GRUB. So perhaps I had to start something using the command line and I tried to find that. I DO know the usual DOS commands, but a simple DIR doesn't work as one might expect. Computer was stuck there.
  Then I thought it needed the CD to start. Rebooted with the CD inserted and up comes the installation screen again. Choose Install inside windows again - perhaps there was something wrong - but Lo ! Configuring possibilities ! Checked them all, such as keyboard. And yes, it started and showed some autoconfig screen.
  And when it's finished with that, my display turns black, there is no more keyboard or mouse and I had to switch of my computer manually.
  After rebooting in Windows I checked what had been installed. There is no trace of Ubuntu in Windows/ProgramFiles, there is no Desktop Icon. I checked the directories and all the exe files I can find are uninstall-wubi.exe and in /winboot : wubildr.exe. No wubi.exe as there is an uninstall for it - whatever wubi is or does.
  Not encouraging for a first experience I should say.:confused:
  Anyone knows a solution ?

        For the first part of your problem, if you installed Ubuntu _inside_ Windows, it is not logical that you will have _both_ operating systems? "Wubi" means Windows Ubuntu Installer, so what you found was your Ubuntu installation. If you want Ubuntu to be your only operating system, choose "Install" and when you get to the partitioning part choose Guided - Use entire disk. But be careful that this option will erase your windows installation, along with your data. So better do a backup first.
       Depending on what version of Ubuntu do you use (I presume 9.04 Jaunty Jackalope) the GRUB should show the current kernel version, the current kernel version in recovery mode and memory test. Mine looks like this (I use 8.04 Hardy Heron)
Ubuntu 8.04 2.6.24-24-generic
Ubuntu 8.04 2.6.24-24-generic recovery mode
Memtest86
Just select first entry (is selected by default anyway) and press enter. Your Ubuntu should boot up. Hope this is helpful and you will manage to solve your problems.
Cheers!

---

### Post by m-v-p on 2009-07-28
Hi everybody, thanks for the replies. Unfortunately I don't have the time to dig further now. I thought all this was going to be easy and swift. But I'll be back because I like the look of Ubuntu - and getting rid of Windows.
  So I uninstalled Ubuntu the Windows way and that should be it. Wrong ! When I reboot my computer, there is the dual boot screen again ! :twisted:

  Honestly, this isn't funny any more. When you remove something, it should be removed completely, no ?
  At least I hope I can get rid of the dual boot for the time being.
  Help ! (Tasukete kudasai ! - that’s "help" in Japanese)


Greetings


Michel

---

### Post by Troll_the_Great on 2009-07-28
I think you have to edit your GRUB for that. Boot into the live CD, open a terminal (Applications - Accessories - Terminal), type:
```
sudo cat /boot/grub/menu.lst
``` and post the output.
Cheers!

---

### Post by nhasian on 2009-07-28
actually it means Please Help in japanese ;)
anyway what exactly is uninstalling Ubuntu 'the windows way?'  you mean through the add/remove programs from the control panel?  Can you please be bit more descriptive to help us help you?

just out of curiosity, did you try booting off the LiveCD and seeing if all of your hardware was supported before installing ubuntu?

> **m-v-p said:**
> So I uninstalled Ubuntu the Windows way and that should be it.....
  Help ! (Tasukete kudasai ! - that’s "help" in Japanese)


---

### Post by hibliss on 2009-07-28
Is this Windows XP or Windows Vista? When you use Wubi to "install inside Windows", it uses the Windows bootloader, and creates a virtual partition, fooling Ubuntu in to thinking it is installed on EXT and not NTFS.

Now, to fix your boot issue, you need to fix the Windows bootloader. If it is XP, go to Start>Run> type msconfig. Go to the boot.ini tab and remove Ubuntu.

---

