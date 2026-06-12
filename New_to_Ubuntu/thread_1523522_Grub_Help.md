---
title: "Grub Help"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by Automag05 on 2010-07-03
Hi guys, I am new to Ubuntu (as well as any Linux OS) and I have recently done a couple of updates to my OS. unfortunately that resulted in Grub becoming very messy and showing previous kernels. I have been looking on line to find a good beginner guide on fixing this, except I haven't gotten very far. I tried running "gksu gedit/boot/grub/menu.lst" because I read that it can allow you to go in and edit Grub, except when ever I run it, nothing happens (not to mention nothing I have tried to run so far has worked :/) 

I am running Ubuntu version 10.04 with Gnome interface.

If anyone has an idea on another option to clean up Grub, or perhaps even my "run" issue, it would be greatly appreciated!

Thanks,
Auto

---

### Post by oldfred on 2010-07-03
Menu.lst is part of grub legacy. If you upgraded from 9.04 or before you likely have grub legacy otherwise new installs have grub2.

General info:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
/etc/default/grub
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

You should keep two kernels, just incase there is an issue with the newest. Be sure not to delete your current kernel as you will not be able to reboot.
Uninstall extra kernels:-------------------------
In synaptic search for linux-image to choose to delete old ones
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by warfacegod on 2010-07-03
You have a few options. Ubuntu Tweak is an excellent tool and will help you remove kernels among other things. [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Another way is to: System> Admin.> Synaptic Package Manager. Search for kernels and remove all but the ones with the highest version number.

---

### Post by Automag05 on 2010-07-03
Oh really? I must have Grub2 then. Mine was a fresh install.

---

### Post by warfacegod on 2010-07-03
Yeah, GRUB v1.98 is called GRUB2.

---

### Post by SoFl W on 2010-07-03
To update the grub menu after removing kernels type:
sudo update-grub2

But using the update manager does not remove old kernels.

---

### Post by Automag05 on 2010-07-03
Thank you, I will begin searching for how to clean Grub2, have you had any experience with that?

---

### Post by wilee-nilee on 2010-07-03
Short of removing kernels from the terminal or synaptic follow post #3 with the Ubuntu tweak install, it has a kernel remover that has never failed me, and many other options.

Generally keeping two sets of kernels is suggested the latest that works and a backup.

---

### Post by SoFl W on 2010-07-03
I usually remove old kernels by manually deleting them, and then running "sudo update-grub2".  

I would recommend what warfacegod said.

---

### Post by warfacegod on 2010-07-03
Yep, should have mentioned keeping an extra kernel in case of emergencies. I forgot because I don't usually do it. I court *disaster!*

---

### Post by Automag05 on 2010-07-03
Thanks guys! How exactly would I manually go in and delete the kernels?

---

### Post by warfacegod on 2010-07-03
You can use Synaptic like I described in my first post or you can use the Terminal if you know the name of the package.

```
sudo apt-get remove package-name
```

---

### Post by Automag05 on 2010-07-03
I am actually unsure what the Kernels are named. Is there a generic name for them? Or a way to find out? If not, how would I go about finding them in synaptic?

Thanks

---

### Post by warfacegod on 2010-07-03
Put linux-generic into the search bar in Synaptic. Your results should look something like this:

---

### Post by Automag05 on 2010-07-04
Alright, so I went into Synaptic and did the search, except my result list was huge! So I decided that I should delete the ones with the same name that are un-selected? But when I tried so, "mark for removal" was unclickable. Here is a picture of my Synaptic result. Maybe you know what to do.

---

### Post by warfacegod on 2010-07-04
In Synaptic the packages with green boxes are installed the white ones are not. On the left click Status and then, higher up, click Installed. That will show you only packages that are installed in your computer.

---

### Post by oldfred on 2010-07-04
Be sure not to delete the one your are using:

uname -r

Older command line version.
[http://www.go2linux.org/clean-linux-kernel-images-grub-menu](http://www.go2linux.org/clean-linux-kernel-images-grub-menu)

list versions:
    cd /boot
    ls vmlinuz*
You can have more than one per command:
sudo apt-get remove linux-image-[version]-generic linux-image-[version]-generic

---

### Post by Automag05 on 2010-07-04
Fantastic, I used uname-r to find my current Kernel set up, and I deleted the others in synaptic once I organized all my installed components together. Thanks a lot guys! My Grub2 is now clean.

---

