---
title: "Can't boot ubuntu 10.04.1"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by peepot on 2011-07-17
Can anyone help me? I can't boot my ubuntu 10.04.1 after installing it. It just jumps to my windows 7 without asking what OS will I be running.

---

### Post by SkippoGuangiacomo on 2011-07-17
Did it ever boot in ubuntu? If it didn't it seems to me that you might need to reinstal it because something went wrong in writing the boot manager... Unless some other smart guy out there has an alternative solution

---

### Post by Madras on 2011-07-17
Hi! Try this.
Go Win 7, next install EasyBCD and select partition which You installed Ubuntu. Select Linux from the list too.
I got same situation with Win7 and WinXP.

---

### Post by peepot on 2011-07-17
Still can't boot ubuntu :-(

---

### Post by peepot on 2011-07-17
The easyBCD didn't work even though I made the ubuntu the default OS. Other ideas there?

---

### Post by amjjawad on 2011-07-17
> **peepot said:**
> Can anyone help me? I can't boot my ubuntu 10.04.1 after installing it. It just jumps to my windows 7 without asking what OS will I be running.

Hello and Welcome :)

Please make sure to provide more details as we can NOT help you with just few words from you. You need to explain how did you install Ubuntu, what exactly the issue and what did you do to fix it? etc.
Also, it's good to mention your machine hardware details.

Rather than that, people will make a guess and help you based on that. It's a bad idea.

:)

---

### Post by peepot on 2011-07-17
Ok. I tried installing ubuntu 10.04.1 via wubi. After installing, I reboot it for further installations but it didn't went there. It went directly to my default OS which is windows 7. Can anyone help me how to go to ubuntu boot install. Thanks:D

---

### Post by beew on 2011-07-18
Just get rid of WUBI an do a real dual boot or install Ubuntu in an external drive.

[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

I suggest an external hard drive instead of a flash drive because it is a lot faster and gives you the identical operation conditions as an internal install,--except boot time may be slower depending on your BIOS,--but the steps are the same. Just remember to make sure you install the bootloader in the drive where you install Ubuntu (say if external drive is sdc, then choose install bootloader in sdc)

To get rid of WUBI, use Add/Remove in Windows. WUBI is buggy, unstable and it doesn't give you a real picture of what Ubuntu can do. If you are going to test drive Linux, you may as well give it its due instead of imprisoning it in Windows.

Edit: Just notice amjjawad  already has this guide in his signature (aptly called "how to avoid WUBI" :))

---

