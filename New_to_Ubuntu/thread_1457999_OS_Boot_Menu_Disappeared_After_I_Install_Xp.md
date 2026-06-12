---
title: "OS Boot Menu Disappeared After I Install Xp"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by Experimental on 2010-04-19
I installed xp right now and the OS boot screen disappeared and the grub is also not loading at the startup . How can I get it back

---

### Post by cosine352 on 2010-04-19
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Crazedpsyc on 2010-04-19
hopefully you backed everything up before you installed XP? you have to know exactly what you are doing with windows to install it next to anything else because Microsoft doesnt want you to use anything else, so they trie to make it hard to. if that link up there doesn't work, download gparted from the synaptic, using your live CD for ubuntu if you have one. run it from a terminal with the command "gparted" and look at the partitions at the top. if it shows your ubuntu partiton at all, look for how much of it is yellowish. If it is empty, or completely 100% full, XP probably ruined it. If you can access your ubuntu partiton from the live CD, great! copy everything of importance onto an external device and reinstall ubuntu completely, taking care to use the side by side option in the installer, and making sure XP will still have enough room.

---

### Post by drs305 on 2010-04-19
This is fairly common. You can probably restore Grub/Ubuntu using the instructions found here:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Experimental on 2010-04-19
Ok guys new problem here. I used update manager and i think it has upgraded ubuntu . But now in my grub I see lots and lots of choices . i have ubuntu.....-20 and ubuntu.....-14
memory test ect. ect. 

How can I edit this menu . Or just remove the older ubuntu version . I tried to use grubed but when I say direct edit the file that grubed opens is empty

And I dont have a menu.lst in boot/grub

---

### Post by drs305 on 2010-04-19
> **Experimental said:**
> Ok guys new problem here. I used update manager and i think it has upgraded ubuntu . But now in my grub I see lots and lots of choices . i have ubuntu.....-20 and ubuntu.....-14
memory test ect. ect. 

How can I edit this menu . Or just remove the older ubuntu version . I tried to use grubed but when I say direct edit the file that grubed opens is empty

And I dont have a menu.lst in boot/grub

You are probably seeing many older kernels. You can remove older ones from your system and when you do they will disappear from the Grub menu as well. 

You can remove them via Synaptic but a very easy way is to install and use Ubuntu-Tweak. The instructions on how to install and run Ubuntu Tweak are located in the "Removing Older Kernels" near the bottom of this post: [http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

You may be using Grub 1.98, which no longer uses menu.list.  You can read about Grub 2 from the links in my signature line. For removing the "Memtest86+" option and/or Recovery modes from the Grub2 menu, click the link to "G2 Tasks".

---

### Post by Experimental on 2010-04-19
I see some documents and I see that I have grub2 . I figured that it's normal not to have menu.lst :P . Thanks for your help . I will have more questions i think :P

---

