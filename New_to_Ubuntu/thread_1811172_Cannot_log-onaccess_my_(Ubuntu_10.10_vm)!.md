---
title: "Cannot log-on/access my (Ubuntu 10.10 vm)!"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by CharmQuark on 2011-07-24
I have Ubuntu on virtualbox. When I first start it, it boots normally and takes me to my log-in page. However when I type my password, the screen states a message, and then takes me to the log-in page AGAIN. Therefore, I cannot get access to my virtual machine! If I type my password again, it will once again take me to the same message and then take me back to the log-in page. 

The message is: "
Ubuntu 10.10

Starting VirtualBox Guest Addition Service ..done.-dispatcher
*PulseAudio configured for per-user sessions
saned disabled; edit/etc/default/saned
*Enabling additions executable binary formats binfmt-support [OK]
*Checking battery state... [OK] "

While booting, my GRUB menu doesn't show up. (Usually for me, the grub menu doesn't show up every time I boot, but I was hoping to use it to access recovery mode). Please help me get access to my files!!! If you have a solution, can you please be detailed as you can? I do not know that much as everyone does on these forums. Thank you!!

*
*
More information that might help: 
- I think this might be related. Someone had plugged a USB flash drive, which contained the new Ubuntu 11.4, into my computer. I was planning to create a dual boot system with Ubuntu and Windows Vista but I first wanted to tar my files on the guest OS. To tar my files, I booted my guest os, but then this problem occurred. I then ejected the flash drive because I thought it was causing problems, but I still couldn't log on to my guest. os. 
- When I type the wrong password in, it states "authentication failure" which is normal. It only repeats itself when I type in the right password.

---

### Post by Too Late on 2011-07-24
Hi

I think it's possible to mount the virtual hard disk (i.e. the .vdi file) to your host OS, at least in read-only mode. I don't know more about that, though.

However, the easiest way, in my opinion, to get access to your files is to use a live CD. I mean, "insert" a CD/DVD image to your virtual machine and boot from that (and make sure you don't install anything, just boot to live OS). The same disc (image) from which you installed your 10.10 should be fine, but any other live Linux should also work. To insert a disc while the virtual machine is off, go to vm's settings and to Storage section and click on the disc icon and then on the another disc icon on the right side. Alternatively you can start the vm first and then put the disc with the Devices menu and then restart the vm.

Your virtual hard disk should be accessible from the live operating system's file browser. However, I'm not sure if VirtualBox's guest additions can be installed to live OS, so copying the files between live guest and host may be tricky.

If you have multiple virtual machines (which support Linux filesystems), you could also try to add that virtual hard disk (where your files are) to those machines which work fine.

Of course, these are just emergency workarounds to get quick access to your files. I have no idea how to fix that login problem, but surely it can be fixed somehow.

---

### Post by CharmQuark on 2011-07-24
Nvm I fixed the problem. I had edited my .profile file before, and was missing an "fi" keyword. I can't believe a little mistake like that would cause so much trouble!

---

### Post by CharmQuark on 2011-07-24
Sorry "Too Late". I didn't see your reply. Thanks for responding! I was able to access my files and edit .profile after I logged on through command line with recovery mode. I could access the grub menu while pressing shift during boot-up. 

Thanks! It seems very oddd that such a little mistake would do so much.

---

