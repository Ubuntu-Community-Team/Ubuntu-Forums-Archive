---
title: "GRUB 1.5 error 17"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by NvizioN on 2009-06-13
I've seen plenty of threads about this, none of them were able to help me.
In my Win7 RC, I tried to remove the partition that had Ubuntu on it, and that wouldn't allow me to boot into any OS.  I'm currently loading off of my Ubuntu disc, not sure of what to do in order to be back on Win7 without any Ubuntu on here.
When my disc isn't in the tray, I get the error 17 from GRUB.  Can anyone help me with a solution for this?
Many thanks
-

---

### Post by presence1960 on 2009-06-13
I believe 7 is like vista. So boot your 7 install media and follow the instructions for vista here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

you just need to restore windows bootloader to MBR.

---

### Post by QIII on 2009-06-13
You may have damaged your master boot record (MBR) in the process.

Do you have the "restore" disks from your OEM?

Do they have an option to rebuild your MBR?

Can you use the LiveCD to mount your Windows partition and back up any important files, just in case the worst-case scenario happens?

---

### Post by NvizioN on 2009-06-13
find /boot/grub/stage1
Error 15: File not found

And I'm also working on grabbing all my important stuff from my Win7, just for that exact reason also.

---

### Post by synapsys on 2009-06-13
Merry Christmas

[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

---

### Post by NvizioN on 2009-06-13
And a happy new year to you, sir.

---

### Post by NvizioN on 2009-06-14
Doing the bootsect didn't work in Command Prompt for me.
I'll try it again, until then, any other ideas?

---

### Post by presence1960 on 2009-06-14
here is a link. try this except for the part of restoring GRUB which obviously you don't need. [http://social.technet.microsoft.com/Forums/en-US/w7itproinstall/thread/87fc9a1c-d13a-49f6-8bae-de79cb3f632c](http://social.technet.microsoft.com/Forums/en-US/w7itproinstall/thread/87fc9a1c-d13a-49f6-8bae-de79cb3f632c)

Again it is just like repairing the vista bootloader in the other link I gave you.

---

