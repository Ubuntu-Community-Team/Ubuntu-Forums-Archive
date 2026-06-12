---
title: "Dual Boot  on two hard drives (Vista and 8.10) -- how to configure"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by nitroguy on 2009-03-05
I have done quite a few searches on dual boots (in fact, I successfully did one already), but I could only find help in regards to a dual boot system with one hdd.

I just got a a laptop that has two hard drive slots in it (dv9000), and want to put Vista on one, and Ubuntu 8.10 on the other. I want Ubuntu to be the primary, and Vista to just boot into occasionally. 

Does anyone have any suggestions on how to configure this, or a tutorial on what I do, and what order I do it in? I'll be starting fresh on both hard drives, wiping them both clean, so preserving data is not an issue.

Thanks.

---

### Post by Somiac on 2009-03-05
Well since they are both internal, all you need to do is install Ubuntu onto the second Harddrive.

Once installed then no matter what when you turn on your computer it will ask you which Operating system you would like to boot.

If Ubuntu isn't on the top of the list of your install file you can edit the order by going into Ubuntu opening the shell and typing

sudo vi /boot/grub/menu.lst

to be able to edit menu.lst

find the line that says
Default 0

and change the 0 to the line number ubuntu is on on the boot sequence.

Mine shows boot sequence as

Ubuntu
Ubuntu Recovery
Windows Vista

if I wanted to boot Vista I would change the line to default 3, this way the arrow on boot is automatically on Windows Vista so if I happen to leave my computer when it's turning on I don't accidentally boot into ubuntu when I want it defaulted at Vista.

I just dealt with all this all night last night LOL so hopefully thats a good answer if not just ask, Good luck.

---

### Post by wannadumpwindows on 2009-03-05
Just remember to keep in mind that Ubuntu, as most computer related things do, starts counting from 0 (zero) not 1 (one). So if you want your third entry to boot, it would be #2, not #3.

---

### Post by lindsay7 on 2009-03-05
you could also install "Startup Manager" from Synatic.  You can change or set up what os will be the default start. You can do this anytime and it is no harm no foul, ie you are not making any perminent changes and there is no way you can mess things up.

---

### Post by tsali on 2009-03-06
Here's a helpful tutorial...

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

You'll always want to make Vista the primary hard drive (hd0). That's ok, because you can set your BIOS to default boot the second drive which has grub on it (hd1)

I would suggest that you avoid putting the grub bootloader on the same drive as Vista. The Ubuntu installer will want to do this by default.

You don't have to manually partition as shown (just don't format your Vista disk!), but when it asks if you want to install grub to the MBR of the first disk, answer "no" and it should them let you specify where. You should select the drive with Ubuntu on it.

**READ THE "ARE YOU SURE?" PROMPTS CLOSELY**

Now, all you need to do is reboot and set your BIOS hard disk boot priority to try the Ubuntu drive FIRST.

After this, it is likely that Ubuntu will boot from grub just fine, but Windows Vista will not. 

**DON'T PANIC!** Vista is still there on the first disk and it's just fine. The grub *menu.lst* often does not correctly identify the Windows drive. You will either need to follow the prompts to open grub's boot options editor, boot with the live CD to edit the \boot\grub\menu.lst file on the Ubuntu drive, or, if you can, boot into Ubuntu and edit from there.

If you're really worried if you've borked your Vista install, just reboot and use your BIOS boot options to select the Vista drive directly...it should start fine.

Make sure menu.lst refers to the Windows drive as "hd0,0" (first drive, first partition)

If you are installing hardy, you may need to change the ubuntu entries to "hd1,0".
If you are installing ibex, I believe the entries will look weird but will be right.

You said you wanted ubuntu to boot by default. It should do this itself, however you can set which entry is the default boot in this file. I won't go into that.

---

