---
title: "Tried to install network driver and completely locked the PC in the progress."
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by redbytex on 2008-10-17
Once upon a time I spent nearly 2 hours installing the onboard network card (Atheros(R) AR8121/AR8113 PCI-E) before finally getting it working. 

That was 1 month ago. Last night Ubuntu said it had some updates to install, so I said Okay and let it reboot itself.

When it booted back up again, the network was completely broken! A little icon sat in the taskbar saying "No network cable connected" (there was). So cnce I finished swearing and yelling about "Stupid Linux updates that uninstall drivers", I decided to fall back to the instructions I had followed originally to install it.

Which is this post: [http://ubuntuforums.org/showpost.php?p=4825848&postcount=7]("http://ubuntuforums.org/showpost.php?p=4825848&postcount=7")

Now here's the frustrating part, as soon as I completed the last step (cd into /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/ and ran sudo insmod ./atl1e.ko) I hit enter and the machine instantly froze. I couldn't move the mouse, I couldn't type on the keyboard. Great. So I turned the machine off by holding down the power button and then turned it back on. But then at the "Type in your username" screen it freezes again. All it shows is the cursor with the Busy symbol.

So looks like I'm completely locked out.

1. How do I access the terminal without fully loading the system?
2. What do I type into the terminal to reverse the damage I previously did?
3. Any idea what I should do to get the network to work from here? Or even better, revert the PC back to it's previous settings from a day ago?

Also I'm a complete Linux noob so if you can break it down in laymans terms that would be greatly appreciated. :)

Thanks for your help guys!

---

### Post by pytheas22 on 2008-10-17
Probably the updates gave you a more recent kernel, which would have broken your wireless because the driver that you installed previously can only work on the particular kernel that it's installed on--this happens when you compile drivers manually from source instead of using packages (although in your case compiling was the only option).

First of all, at your grub boot screen (the one that you see immediately after BIOS), you should see a list of available kernels as well as recovery mode options.  At the top of the list is the most recent kernel.  See if you can boot into an older normal kernel without freezing.

If that doesn't help, boot normally.  At the graphical login screen, instead of logging in, press control-alt-F2.  This will bring you to a command prompt where you can log in.  Once logged in, run these commands, which should remove the kernel module that seems to be triggering the lock up:
```

cd /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/
sudo rm atl1e.ko
```

Then press control-alt-F7, which will bring you back to the graphical login.  See if you can log in now.

If all this works and you're able to get back to your desktop, we can figure out a way to get the wireless working again without a freeze.

Also, do you have an ethernet connection available on this computer (just so that we can factor that in when figuring out the best way to get new wireless drivers installed...it's of course easier if you have a connection available to install the drivers with)?

---

### Post by redbytex on 2008-10-20
Hey thanks for your help pytheas22.

I pressed Esc at the boot to Kernel screen and chose 2.6.24-19 instead of the recently installed 2.6.24-21 and it worked! Even the network driver was working when I logged in!

Only problem is I now have to do this everytime I boot up. Is there a way to make ubuntu boot to that kernel by default?

Thanks

BTW, are these Linux updates really necessary? Because I seriously don't want them. If it already works why fix it?

---

### Post by pytheas22 on 2008-10-20
I'm glad the older kernel still works.  If you want to just continue to use that one, you can remove the newer kernel entry from your grub menu.  First, backup your current grub by typing:

```
cp /boot/grub/menu.lst ~/menu.lst.backup
```

Then open up the menu for editing:

```
sudo gedit /boot/grub/menu.lst
```

Scroll down towards the bottom and you should see a section that looks similar to this:
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash
initrd		/boot/initrd.img-**2.6.24-21**-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro single
initrd		/boot/initrd.img-**2.6.24-21**-generic


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash
initrd		/boot/initrd.img-**2.6.24-19**-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro single
initrd		/boot/initrd.img-**2.6.24-19**-generic
```

As you can see from the information in bold above, each entry corresponds to a different kernel (or recovery-mode kernel).  To prevent the 2.6.24-21 kernel from appearing any more as an option, you can either delete the sections related to it, or comment it out by placing a # in the front of all of its lines.  This should cause it to no longer be an option when you boot.  If you wanted, you could also simply move the 2.6.24-21 paragraphs to the bottom of the list, in which case they would remain options, but 2.6.24-19 would become the default.

When you're done, save and close the file.  Reboot, and you should automatically be booted into the working kernel.  If not, let me know.
> 
BTW, are these Linux updates really necessary? Because I seriously don't want them. If it already works why fix it? 

The updates fix bugs and security vulnerabilities, but if you're just a desktop user, there's probably nothing too gravely important that you're missing by using an older build of the kernel.

Also, if you upgrade to Intrepid, your wireless driver should be built into the kernel, meaning that you would no longer have to install it manually, and that when you update your kernel, the wireless driver will also be updated.  Intrepid will be released officially on 30 October and will appear as an upgrade option in the Ubuntu updates box then, but if you want to upgrade now, you can do so by typing:
```

sudo update-manager -d
```

and click the appropriate button.

---

### Post by redbytex on 2008-10-21
You rock pytheas22! I did what you did, and it worked perfectly! The computer now boots to the old kernel and all is great once again. :D

It's refreshing to meet a linux user who knows his stuff, and is willing to explain the solution as clearly and precisely as you have.
Keep doing what you're doing! You're a big help to the community :)

---

### Post by pytheas22 on 2008-10-21
Well, I don't know all of my stuff that well, but I try to help people when they have problems that I understand.  I hope you'll do the same when you have time; that's why Ubuntu works.

I'm glad to hear the problem is solved; have fun with Ubuntu :)

---

