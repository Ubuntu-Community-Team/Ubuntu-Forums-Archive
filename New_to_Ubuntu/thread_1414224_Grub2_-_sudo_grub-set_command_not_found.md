---
title: "Grub2 - sudo: grub-set: command not found"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Swerve1000 on 2010-02-23
Hi,

I am trying to alter Grub2 on my dual boot machine so that windows is the first/default OS.

I'm using the following command from my home directory:

> 
sudo grub-set default 4


But it says:

> sudo: grub-set: command not found

I tried to execute the same command from within the /boot/grub directory, but the same happened.

It's a default install of Ubuntu Server 9.10 alongside XP.

Thanks for any help!

---

### Post by philinux on 2010-02-23
> **Swerve1000 said:**
> Hi,

I am trying to alter Grub2 on my dual boot machine so that windows is the first/default OS.

Thanks for any help!

Edit the file /etc/default/grub


GRUB_DEFAULT=**X** where x is your choice.

Save the file then run

```
sudo update-grub
```

---

### Post by 101011010010 on 2010-02-23
Hello, I think that you missed out the hyphen between set and default.
> sudo grub-set-default 4I hope this helps.

---

### Post by oldfred on 2010-02-23
The Grub 2 Guide (formerly Grub 2 Basics) - see #5 on default settings
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry 
gedit /boot/grub/grub.cfg
and copy here
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by Swerve1000 on 2010-02-23
Worked perfectly.

At first I didn't "sudo update-grub" thinking it would whem I rebooted, but it didn't, so I Nano'd the file again, the changes I had made previously were still there, so I exited, ran "sudo update-grub", rebooted and it worked just perfect.

Thanks philinux

And everyone else. 

:D

EDIT - The docs say not to edit grub.cfg directly, but it worked fine for me here. I'm guessing my PATH maybe the reason my first "sudo: grub-set: command not found" may of been en-counted.

How could I fix that?

---

