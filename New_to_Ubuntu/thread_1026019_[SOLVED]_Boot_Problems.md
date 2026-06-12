---
title: "[SOLVED] Boot Problems"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by amor0fati on 2008-12-30
I run Windows XP off of a sata drive and wanted to give Ubuntu a try, so I made the mistake of trying to install Ubuntu on an external hard drive and found out that my BIOS wouldn't allow me to boot from an external when I got a GRUB error 22.  The strange thing about this was that even with the external hard-drive disconnected, I still got error--grub error 17.

My first attempt to remedy the situation was to try and reinstall ubuntu as a dual-boot from my internal hard-drive.  The installer told me that it had failed to resize the partition, and I was never able to see that option ever again.  All it would allow me to do after that was manual install or full-disk install or largest available space (which doesn't seem to work anyway).

My last attempt remedied the situation somewhat.  I took the external I had planned to install ubuntu on and hooked it up internally as an ide drive.  I formatted the disc by booting from the install disc, then I reinstalled ubuntu on that.  I still got the grub error, so I entered my BIOS and set the ide drive as the first boot drive with the sata as the second.  This allowed me to finally see the grub and boot with ubuntu from my ide drive.

Windows XP was listed on the boot list, but I get error 13 when I try to boot with it.

Where have I gone wrong?

---

### Post by caljohnsmith on 2008-12-30
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by slammed87d21 on 2008-12-30
I had the same issue on my laptop. Download GParted, run it to resize your Windows partition, then do a manual install of Ubuntu. That should have everything fixed.

---

### Post by RealG187 on 2008-12-30
How did you get an IDE and SATA drive in the same machine?

---

### Post by amor0fati on 2008-12-31
It should also be said that I don't have an internet connection, because ubuntu doesn't seem to be able to readily connect using my wireless card (linksys wireless-g WMP54G).  That's another problem I'm trying to overcome.

I could potentially find a way to get GParted, if you think that would help, but would that only help with installing ubuntu on my sata?  If I did install it on my sata, would that fix my grub errors?

Also, I may not have ready access to an XP installation disc.  I hope this won't be too much of a problem.  Maybe the SuperGRUB Disc would help?

This is my first time trying to install a linux OS, so I didn't foresee any of these problems.  They seem like fairly common problems, but I'm having a hell of a time trying to find a solution.

In the grub, the commands for booting Windows XP Home Edition look something like this:
root (hd0,0)
savedefault
chainloader +1

By the way, my sata is sda and my ide is sdb, and my sata has only one partition for windows and some unused space.  When I check in the partition manager while running ubuntu off the installation disc, it can't tell me how much space is used on sda; it just says unknown.  I do know that all of my original files are still in the disc, because I can see them when I mount the disc in ubuntu.

On my first attempt to install ubuntu on an external, I didn't fiddle with the bootloader at all, on a subsequent attempt, I believe I chose HD0.  On my succesful install on sdb, I installed the bootloader to sdb.

Also, my motherboard happens to have both sata and ide ports.  I don't think this is uncommon.

I really need some help on this, I'm having to walk around town to use computers at labs and at friends' houses just to get connected and get help (since I can't seem to connect at home).  I'll go ahead and work on getting GParted and SuperGRUB, but any other solutions would be highly appreciated.  If anyone could point me in the right direction to get connected over ubuntu, that would also be a big help.

---

### Post by caljohnsmith on 2008-12-31
So can you boot into Ubuntu OK now? If so, I think I know what might be causing your problems booting Windows. How about opening a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And change your current Windows entry to:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, select XP from the Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by amor0fati on 2008-12-31
Alright, I'll give that a try.  Hopefully it works so that I can at least figure out my connection issue from home on XP.

---

### Post by amor0fati on 2008-12-31
Thank you so much for your help!  I figured something like that must've been the problem, but I didn't know quite how to fix it.  I tried other variations of that, but had no luck.

I booted from the grub, and windows booted, performed a CHKDSK, restarted, then allowed me to successfully bootup from the grub.

Now I've just got to figure out how to connect with ubuntu.

---

### Post by caljohnsmith on 2008-12-31
Glad to hear that worked OK; good luck getting your connection issues sorted out, but if you need any help, there are some knowledgeable people who are regulars in the "networking" forum section. If you post there I'm sure someone will lend a hand. :)

---

