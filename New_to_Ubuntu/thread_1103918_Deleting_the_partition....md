---
title: "Deleting the partition..."
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Stupidnoob on 2009-03-23
Hi guys, I'm in dire need of help.

Last night I got hyper and temporarily insane, so I figured I'd delete my xubuntu partition. I went into the administrative tools on windows and cleaned the xubuntu partition. When I then tried to delete it, I got some error that I no longer remember.

At some point here my brain lost interest in what I was doing and I turned the laptop off to try and get some sleep. This morning when I started it I keep getting grub error 17, and it doesn't let me boot any further.

Any pointers on how to remove/edit grub so I can remove the empty partition and go back to single windows boot?

Oh and... please don't point out my stupidity, I'm very aware of that now.

---

### Post by yeats on 2009-03-23
What version of Windows are you using?  Do you have the Windows disk?

---

### Post by Stupidnoob on 2009-03-23
Windows Vista 32 bit that came with the laptop when I bought it. The only other Windows I have on CD is a Vista 64 bit that I got for my stationary...

---

### Post by jakupl on 2009-03-23
download the Super Grub live cd. [http://forjamari.linex.org/projects/supergrub/](http://forjamari.linex.org/projects/supergrub/) and burn it to a cd as an image. "on windows use poweriso or such." [http://www.poweriso.com/](http://www.poweriso.com/) (free for download)

It will do all sorts of stuff, including repairing the windows boot. I did it a few days ago. However it is not very user friendly. But just read what it says. It works really well.

---

### Post by Stupidnoob on 2009-03-23
Thank jakupl, but which one do I download? The first one that says CD?

---

### Post by Stupidnoob on 2009-03-23
Alright, I've just tried the super grub thing on cd and that failed. The computer doesn't try to boot the cd even if it's set to primary boot, and I'm still stuck with error 17.

---

### Post by Stupidnoob on 2009-03-23
Forgot to mention which version I tried.

super_grub_disk_0.9774.iso is the one I downloaded, burned to a disk and then tried to boot.

---

### Post by gn2 on 2009-03-23
The Error 17 is because to start the OS, Grub needs to read the contents of /boot/grub which you have removed.

You should be able to use the SuperGrub CD to re-instate the Windows native bootloader, over-writing Grub in the MBR.

If you have Vista you might also need to use [this Recovery CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") to get things back to normal.

Lots more useful info concerning booting issues in the Hermanzone link in my sig.

The Supergrub CD must be burned "as an image" in the same way as an .iso of Ubuntu, and you'll need to make sure that the CD drive is before the hard drive in the BIOS boot device order.

---

### Post by jakupl on 2009-03-23
> **Stupidnoob said:**
> Forgot to mention which version I tried.

super_grub_disk_0.9774.iso is the one I downloaded, burned to a disk and then tried to boot.

Good. Are you sure that you burned it as an image? e.g. using power iso in windows.

---

### Post by Stupidnoob on 2009-03-25
Finally made a bootable supergrub cd, but now I'm lost in all the menu options. I tried restoring windows but it boots my acer erecovery, there I'm faced with 2 options: default restore (wipe everything) or cd restore which is the same.

Is there anything I can do from the command prompt?

---

### Post by Stupidnoob on 2009-03-25
Woo! Made it:P

I ran the supergrub one last time, and this time I went through the Windows part, where I only had to press Restore Windows MBR.

---

### Post by jakupl on 2009-03-26
> **Stupidnoob said:**
> Woo! Made it:P

I ran the supergrub one last time, and this time I went through the Windows part, where I only had to press Restore Windows MBR.

Congratulations :) Supergrub can be pretty confusing, but it really works if you see through it.

---

