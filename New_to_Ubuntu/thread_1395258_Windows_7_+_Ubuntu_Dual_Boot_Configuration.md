---
title: "Windows 7 + Ubuntu Dual Boot Configuration"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by nair on 2010-01-31
I want to learn more about a dualbooting configuration between a Windows 7 machine and basically any distro of Linux, which will definitely be Ubuntu this time around.  I have a work laptop that has two partitions on it, one for Windows XP and another for Windows 7.  Now that 7 has been out for a few months and has been very impressive, imo, I am certainly ready now to completely cut off from XP.  So, I've got a second partition now that I can wipe and put some other OS on it just for fun.  I've messed with Ubuntu 8.04 and 9.04, and I definitely want Ubuntu to be this new, fun OS.  Since I have Windows 7 already installed first, how do I now install Ubuntu on a second, already freed up partition so that I can freely switch between Windows 7 and Ubuntu?  What type of boot manager do I use?  I was under the impression that the Windows 7 boot manager will not detect any non-Microsoft OS.

Other relevant information: I'm not familiar with too many dual/multiboot configurations in general, and I am completely unfamiliar with any Linux boot manager(s).  I did a brief search on these forums and did not find what I sought regarding my specific task, although that could certainly be caused by my undeveloped sense of direction on these forums.  Also, I absolutely cannot afford to lose any information on my Windows 7 partition.  If I cannot boot back into that exact partition on that exact harddrive, that will be a huge problem.

---

### Post by M1ke on 2010-01-31
Have a poke around these forums for pointers; there's lots of advice on dual-booting the two. I set my machine up as a Windows 7/Ubuntu dual-boot very easily - I was impressed at how straightforward the whole process was!

It sounds like you're already in a good position to start. Common advice is to install Windows first, then pop in the Ubuntu Live CD and tell it to install in the empty partition you've got waiting, leaving Windows intact on the other. During the installation process you could set up another partition or two if you'd like separate areas for swap space, the home directory with all your configurations and settings etc.

Once installed Ubuntu's boot manager, grub, will take over the boot process. On starting your computer you'll be presented with a menu where you can decide which OS to boot.

You probably won't be able to "see" Ubuntu's partition from within Windows, but Ubuntu will be able to read the NTFS-format Windows partition just fine. You won't lose any data on the Windows partition installing Ubuntu in to its own one, but it never hurts to backup critical data before starting anything.

Good luck!

---

### Post by listerdl on 2010-01-31
I have a dual boot set-up, latest windows 7 and latest ubuntu that share the same 'media' storage so you can access folders from whichever OS you are in.

Very simple process.

Follow this tutorial it works very well: [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

ENJOY!

PS I prefer to use linux but windows is better for me personally b/c it has very good auto text programs that i use since i type hundreds of emails per day and graphic programs are basically easier to use, (according to me!)

---

### Post by nair on 2010-01-31
How do you get to choose between boot managers?  If you somehow get stuck with the Windows boot manager, you would never get to use Ubuntu.

---

### Post by corncob on 2010-01-31
Will you be removing XP prior to installing Ubuntu?  I don't know how this limitation comes about but they tell me you can't have more than 4 bootable partitions on a hard drive.  According to GRUB when I installed Ubuntu, Win7 uses 3 of them -- one for recovery, another for restoration, and the third was win7 itself.  I installed Karmic with no problem.  I then went on to install Ubuntu Ultimate.  I ended up not being able to boot the hard drive and used the live CD to restore GRUB.  When I got things working again, the partition where I installed Ubuntu Ultimate had disappeared into "unallocated space".  I understand I could delete the first partition since I've made recovery disks but I'm leaving things as they are for now.

---

### Post by corncob on 2010-01-31
> **nair said:**
> How do you get to choose between boot managers?  If you somehow get stuck with the Windows boot manager, you would never get to use Ubuntu.

The Ubuntu boot manager, GRUB (GRand Unified Boot-manager), is installed.  On startup it gives you a menu where you can choose windows or let it default to Ubuntu.

---

### Post by Fire$torm on 2010-01-31
Here is another how-to for dual booting: [COLOR=Red]||[/COLOR]  [Dual-Boot Windows 7 and Ubuntu in Perfect Harmony]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lifehacker%2Ffull+%28Lifehacker%29") [COLOR=Red]||[/COLOR]

If link above does not work copy and paste this:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lifehacker%2Ffull+(Lifehacker]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lifehacker%2Ffull+%28Lifehacker"))

---

### Post by nair on 2010-02-02
Just wanted to first say I successfully got my dual boot configuration setup correctly.  I've booted into both OSs several times now over the past couple days.  Thanks all for the links and the tips.

One thing I'm still not sure about: Clearly the Ubuntu boot manager has now taken over my entire harddrive to then give me the choice of selecting booting into Ubuntu, in its many different forms, or Windows 7.  If I were to uninstall Ubuntu at any point from now on, what parts of the Ubuntu boot manager are left over exactly, or is anything left over?  If I were to delete the Ubuntu boot manager, is the harddrive smart enough to then go back to the Windows 7 boot manager as the default boot manager?

---

### Post by corncob on 2010-02-02
> **nair said:**
> Just wanted to first say I successfully got my dual boot configuration setup correctly.  I've booted into both OSs several times now over the past couple days.  Thanks all for the links and the tips.

One thing I'm still not sure about: Clearly the Ubuntu boot manager has now taken over my entire harddrive to then give me the choice of selecting booting into Ubuntu, in its many different forms, or Windows 7.  If I were to uninstall Ubuntu at any point from now on, what parts of the Ubuntu boot manager are left over exactly, or is anything left over?  If I were to delete the Ubuntu boot manager, is the harddrive smart enough to then go back to the Windows 7 boot manager as the default boot manager?

In the past I have restored the Windows boot record by booting from a windows recovery disk and typing 'fdisk /MBR' at the command prompt (There was something like 'fixmbr' somewhere also).  This might be ancient history as far as win7 is concerned.  If somebody doesn't come up with something here you might ask at [http://www.WindowsBBS.com](http://www.WindowsBBS.com)

---

### Post by oldfred on 2010-02-02
Useful to have these instructions handy and a Ubuntu liveCD. If windows have a windows repair CD.  If you want to go back to windows boot you should first install the windows boot loader into the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

