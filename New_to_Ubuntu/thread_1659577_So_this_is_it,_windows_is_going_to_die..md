---
title: "So this is it, windows is going to die."
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Rick Savant on 2011-01-04
Well hopefully not.  Ok a couple quick things before I explain the problem.  A)  I'm a moron.  I really know very, very little about any of this so you may have to be (very) patient with me.  B) This might not even be a Linux issue.  It might be windows.  BUT!  I trust you guys more than Microsoft so I'll try here first.

Brief sysnopsys:  This is long so the short of it is that Windows is not appearing on my screen when I select between it and Ubuntu when I load up my computer and I would like it to do that again.

Ok let's start with the specs so I don't forget and get flamed.  Do people still say that on the internet?  Am I showing my age?  I'll stop now.

So my computer is a Gateway.  The cheapest gateway money can (or could at the time) buy.  Intel Pentium processor 14400, 250 GB HDD, 4 GB Memory I feel like it's dual core but that could be ********.  Not sure how to check that either.

Now I am (was?) dual booting Windows 7 and Ubuntu 10.04 up until New Years Eve when I came home and found that windows had disappeared from my boot screen.  I think I am using GRUB 2 Bootloader if that's even a thing I can use.  I'm not sure how to check that.

At any rate the list of options on the bootloader had slowly gotten longer with more and more (what I assume are) Ubuntu recovery options and now is only them.  The bootloader screen looks something like this:

Ubuntu, with Linux 2.6.32-26
Ubuntu, with Linux 2.6.32-26 (recovery)
Ubuntu, with Linux 2.6.32-24
Ubuntu, with Linux 2.6.32-24 (recovery)
Ubuntu, with Linux 2.6.32-23
Ubuntu, with Linux 2.6.32-23 (recovery)
Ubuntu, with Linux 2.6.32-22
Ubuntu, with Linux 2.6.32-22 (recovery)
Ubuntu, with Linux 2.6.32-21
Ubuntu, with Linux 2.6.32-21 (recovery)
Memory Test (memtest86+)
Memory Test (memtest86+, Serial Console 115200)
Windows Vista (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)

Ok so this creates the illusion that Windows got bumped off of the bootloader but that doesn't seem like it should be possible and there's no way of verifying it that I know of.  As you can see the windows installer CD is on my computer as a separate partition and has it's own entry in the boot loader and that is still there.

Now, I think windows is still on my computer because I can go into the partition that has it via Ubuntu and see all the files.  Well I actually can't see all the files but I'm under the impression you're not supposed to be able to see the .exes etc that aren't Linux files.  But I can def see SOME of the files and all of the folders so it looks like it's still there.  My third partition which has music and professional wrestling videos is untouched proving that God really does love Tully Blanchard after all.

When I tried to run the Windows 7 loader thinking that Windows might have collapsed in on it's self it started going through a set up process (but not installing files) and then asked me to restart.  I did and at that point the computer stopped being able to get past the first screen.  You know the one where you can press F2 to get into setup.  It would show a status bar loading up (quickly) and get to varying points of closeness to full before going black and restarting.  I booted off my Ubunutu CD and reinstalled the bootloader into dev/sda as part of the Restore Broken System option.  Now it works, as in as well as it did before I tried to reinstall windows, but I still don't have the options to access windows from my loading screen.

Help?

---

### Post by Bucky Ball on 2011-01-04
Open a terminal in Ubuntu (Applications->Accessories->Terminal) and type this:

```
sudo update-grub
```

Tell us how you went.

---

### Post by Rick Savant on 2011-01-04
Thanks for the reply!

Ok I ran sudo update-grub and entered my password and it did this:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done

Which appears to be the screen I see when I boot.  I restarted and windows was still not on the list.  Any ideas?

---

### Post by psusi on 2011-01-04
You aren't making sense.  You said that is the list you get at boot time, but Windows is not on the list.  Both of the last two items are Windows.

---

### Post by Paqman on 2011-01-04
Every time you install an updated kernel (which is fairly often) it will generate a new entry in Grub, just in case for some bizarre reason you wanted to boot an older kernel. This will obviously push Windows down the list.

You can still boot Windows though. If you want to shorten up your Grub list, just open Synaptic, filter for installed packages only and "linux-image-2.6" and uninstall all but the latest kernel. It'll automatically remove the old entries from your Grub list.

---

### Post by Rick Savant on 2011-01-04
Yeah, sadly that's not windows.  I know, I know... it *says* windows but it's actually the Windows 7 (loader).  Which is basically the Win 7 Installation disk that Future Shop was kind enough to put onto a partition of my hard drive and eat up a bunch of space.  I guess the upside of that is I can't lose my Win 7 disc, which with me is always a possibility.

But it isn't Windows in the same way that the top selection is Ubuntu.  When I select the Windows 7 (loader) from my bootloader screen it does a setup for windows then tells me to restart my computer.  When I do that it goes into an eternal loop of the first screen that says Gateway > black screen > Gateway > black screen > ad nauseum and I have to F12 to boot from my Ubuntu CD to be able to reinstall GRUB on /dev/sda before I can even get back to the defective bootloader again.  Windows Vista also has it's installer CD appear in this bootloader list.

> **Paqman said:**
> Every time you install an updated kernel (which is fairly often) it will generate a new entry in Grub, just in case for some bizarre reason you wanted to boot an older kernel. This will obviously push Windows down the list.

You can still boot Windows though. If you want to shorten up your Grub list, just open Synaptic, filter for installed packages only and "linux-image-2.6" and uninstall all but the latest kernel. It'll automatically remove the old entries from your Grub list.

Hrm.  So why isn't windows appearing on the list?  Is it possible that these older kernels have removed it?  If not why might it have disappeared?

---

### Post by uRock on 2011-01-04
The Windows 7 restore partitions normally show up as being Vista, which is listed as well in your list.

To remove kernels, free up space, and clean up your boot screen, go to **System> Administration> Synaptic Package Manager** in your menus, then in the left pane, click the **Status** button, then click **Installed** above where the status button was. Next, in the search pane, type **2.6.32**, then highlight and click to **Mark for Complete Removal** all three instances of **2.6.32-21**, **2.6.32-22**, **2.6.32-23**, and **2.6.32-24**. [SIZE=2][COLOR=Red]Do not uninstall any of the 2.6.32-26 kernels.[/COLOR][/SIZE]

---

### Post by stalkier on 2011-01-04
It sounds like the Win7 loader got messed up somehow. This happens from time to time when running Win7 or Vista in some cases. I personally have never had this happen but I have just been lucky. I am sorry I cannot tell you how to fix this problem at the moment.

---

### Post by uRock on 2011-01-04
> **stalkier said:**
> It sounds like the Win7 loader got messed up somehow. This happens from time to time when running Win7 or Vista in some cases. I personally have never had this happen but I have just been lucky. I am sorry I cannot tell you how to fix this problem at the moment.
I would think that the Windows repair disk would be able to fix this, if the OP created the repair disk when doing the first backup.

---

