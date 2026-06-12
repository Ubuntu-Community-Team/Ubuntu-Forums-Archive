---
title: "partition error after installing 10.04"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by lupulin on 2010-10-21
So I was having problems starting my computer after a failed update. I took the computer to a knowlegeable friend and he partitioned the drive and installed 10.04. Now when I start the computer it takes me to a linux menu that says GNU GRUB with 9 options (like ubuntu 10.04 LTS, kernel 2.6.32-25-generic (on /dev/sd1)) which when selected says 

error: no such device (then a long serial number) 
error: no such partition
error: you need to load the kernel first

I also have the option to hit c from the gnu grub menu for a command line.

I summise that its booting from the wrong partition or somethinng. Are there any commands I can use from the grub> command line to fix this?

---

### Post by drs305 on 2010-10-21
First, this may be a simple fix (may be...). 

At the Grub menu, highlight the top entry, then press "e" to edit the menu entry.
Use the cursor keys to move to the "search" line and hold the DEL key down to delete the entire line.

Move to the Linux line.  At the **root=UUID=<alphanumeric>** portion, change it to **root=/dev/[COLOR="DarkRed"]sda1[/COLOR]** Use whatever was in the titles (sda1, sdb5, whatever). If Ubuntu is the only OS on the system, it should be sda1. If you don't know, you'll have to come back and tell us.

After you have made those changes, press CTRL-x and see if it now boots. If it does, then open a terminal (Applications, Accessories, Terminal) and type in "sudo update-grub". It will ask for your password. Type it in and press ENTER. You won't see it as you type.

If that doesn't work...

Take a very deep breath, then venture to this thread.
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

If you have questions you can post them here. If you need help, run the boot info script and post the results. The script link is in the "Rules for Posting" section. ;-)

---

### Post by lupulin on 2010-10-22
Thanks. I tried that and it seemed like it was going through the boot procedure but then it says 
ALERT! /dev/sda1 does not exist. returning to a shell
im going to take a look at that thread right now too although I dont think I can run the boot script in my current internetless state

---

### Post by AoSteve on 2010-10-22
Remember, you HAVE to select the right partition on the option.   the /dev/sda1 could end up being a windows partition or even a swap space.

The easiest way I've fixed similar problems is with :

```
sudo update-grub
```

From a live CD   Applications -> Terminal       :)

---

### Post by drs305 on 2010-10-22
> **lupulin said:**
> Thanks. I tried that and it seemed like it was going through the boot procedure but then it says 
ALERT! /dev/sda1 does not exist. returning to a shell
im going to take a look at that thread right now too although I dont think I can run the boot script in my current internetless state

If you aren't sure you used the correct designation, you can figure it out from the Grub menu. Instead of pressing "e", press "c" to get to the grub prompt. When you type "ls" you will get a list of partitions (hdX,Y).

You can see the contents by typing the command "ls (hdX,Y)/". When you find the linux partition it will list the linux / contents, and will probably start with "lost+found". Once you find the correct (hdX,Y) value, go back to the menu edit mode. 

To translate X,Y into device names: X 0 is sda, X 1 is sdb, etc.  Y is the same numeral Y 1 is 1, Y2 is 2 ...   So (hd2,4) would be sdc4.

---

### Post by lupulin on 2010-10-22
Well fellas, thanks for the help. I feel a bit silly. I took my computer back in to a friend and it booted perfectly. It seems that the problem was a hardware issue which manifested right after updating the system. The monitor cable is glitchy. I was able to see the GNU GRUB menu, but when I tried to boot normally the monitor would go dead which I interpreted as the computer going dead. :oops:

I was sort of having fun poking around with the grub settings, though. I did find out that my drive is (hd0,6) which makes it sda6 that I would have needed to use.

---

### Post by Quackers on 2010-10-22
Sometimes circumstances conspire against you :-)

---

