---
title: "Dual Boot Woes"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by BJones007 on 2011-01-07
I'm dual booting with Windows 7, but I just turned my computer off for a minute just to switch over from Ubuntu when I got this error message: 

> BOOTMGR is compressed. Press Ctrl+Alt+Del to restart  


Is there anyway I'd be able to fix this, without losing my information off of the partition?

---

### Post by Megaptera on 2011-01-07
I found this possible solution 
Issue

After compressing your drive C: you get this message:

bootmgr is compressed 





ctrl + alt + del to restart the computer. 


Solution

    * Insert the installation DVD in your system and start the pc above.
    * Click Repair your computer.
    * Then click on Load Driver.
    * Go to Computer.
    * Right click on the partition your installation previously compressed> Properties.
    * Then uncheck "Compress drive to increase space available".
    * Then close all windows to restart the computer.

Here:[http://social.technet.microsoft.com/Forums/en/w7itproinstall/thread/6cdac18d-2110-4eb1-b66e-73aef83fbc48](http://social.technet.microsoft.com/Forums/en/w7itproinstall/thread/6cdac18d-2110-4eb1-b66e-73aef83fbc48)

---

### Post by audiomick on 2011-01-07
The solution above will almost certainly remove your Ubuntu install. If this doesn't bother you, go ahead.

If you can't save files by booting into you Ubuntu install, you should be able to boot into a Live CD session and save anything off  to an external drive or something that you want to keep. I would suggest doing this with important files before trying anything at all. Just in case... ;)

What happens when you do ctrl + alt + del as the error message suggests?

---

### Post by BJones007 on 2011-01-07
Thanks guys for that, but the thing is I'm using a netbook. No CD/DVD drive o.O

---

### Post by BJones007 on 2011-01-07
Thanks guys for that, but the thing is I'm using a netbook. No CD/DVD drive o.O

---

### Post by BJones007 on 2011-01-07
Thanks guys for that, but the thing is I'm using a netbook. No CD/DVD drive o.O

---

### Post by BJones007 on 2011-01-07
Thanks guys for that, but the thing is I'm using a netbook. No CD/DVD drive o.O

---

