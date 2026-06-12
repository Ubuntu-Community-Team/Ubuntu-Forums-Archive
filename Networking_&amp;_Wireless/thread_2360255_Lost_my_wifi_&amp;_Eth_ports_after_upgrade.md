---
title: "Lost my wifi &amp; Eth ports after upgrade"
date: 2017-05-02
forum: Networking &amp; Wireless
---

### Post by slowerthanyou on 2017-05-02
I allowed the latest upgrade (4.4.0-77.98) as usual, and now my wifi & Eth have disappeared.  Not sure what to look for now.

---

### Post by paul_h on 2017-05-02
I also installed the latest upgrade to 16.04 and have lost wifi, ethernet, sound and wireless (USB) mouse. Fortunately I dual-boot with Windows 8.1 and all functions are working with Windows, indicating that the hardware is not the problem. I assume a later update will repair the problem but I will now have to work out how to install an update without network connection.

---

### Post by techbot2 on 2017-05-03
Same issue here, upgraded an hour ago and lost wifi and wired on work machine (Acer laptop).


I tried installing an external usb wifi it was not recognised.
My external monitor is also no longer recognised.

usb mouse works (oddly enough)

---

### Post by slickymaster on 2017-05-03
*Thread moved to **Networking & Wireless**.*

---

### Post by slickymaster on 2017-05-03
It seems [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623)

---

### Post by techbot2 on 2017-05-03
Thank you slickymonster, reverting did indeed work.

I second marking this solved. :-)

---

### Post by leof2 on 2017-05-03
Great, this was exactly what happened to me!
The only problem is that I am still figuring out how to use Linux and I am not sure how to revert to an older kernel. Could someone give me a hint? That would be great!
Also, I have another update lined up. I can't download that one  right now obviously (no internet connection) but would you recommend downloading and installing it after reverting to the old kernel? Or would it be wiser to wait a day or so to get an update that has already dealt with this bug? Sorry if that's a foolish question; I'm really not very good with computers, but trying to learn...

---

### Post by slickymaster on 2017-05-03
Holding down the shift key while booting, will display the Grub menu enabling you to select an older kernel version.

---

### Post by leof2 on 2017-05-03
I actually found that out already and was very proud of myself for that. Only thing is: it doesn't work -.- No matter whether I hold shift, press it in short intervals, or hammer away on it like a monkey - no GRUB menu. I even tried both shift keys.... is there another way to enter GRUB?

---

### Post by slickymaster on 2017-05-03
> **leof2 said:**
> I actually found that out already and was very proud of myself for that. Only thing is: it doesn't work -.- No matter whether I hold shift, press it in short intervals, or hammer away on it like a monkey - no GRUB menu. I even tried both shift keys.... is there another way to enter GRUB?

See this thread: [Set “older” kernel as default grub entry]("https://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry")

---

### Post by ajgreeny on 2017-05-03
If you have a UEFI machine you probably need to keep repeatedly pressing Esc when you boot to get the grub menu.
That should work but I had big problems when I had the need to get to the grub menu on my machine using UEFI; no key press seemed to work so I edited the /etc/default/grub file to make sure it always appeared for 2 seconds.

This is what mine looked like at that time.
```
GRUB_DEFAULT=0
#Next line will make the countdown time show menu by default
GRUB_TIMEOUT_STYLE=menu
#Next line changed from 0 to x for x second delay
GRUB_HIDDEN_TIMEOUT=2
#Next line changed from true to false to allow delay countdown to show
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR="Xubuntu-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```Run **sudo update-grub** after editing then reboot and you should see grub.

---

### Post by leof2 on 2017-05-03
Thank you both, slickymaster and ajgreeny. That last post really helped, my computer runs normally again now :) And now I know how to enter GRUB, so: Yay! :D

---

### Post by ajgreeny on 2017-05-03
As you have now got back your wifi, try running ```
sudo apt update
sudo apt upgrade
``` and you may see a few kernel additions such as header packages that for some reason were missed by the update-manager.

Then boot again to the new 4.4.0-77 and with luck all will be well.

---

