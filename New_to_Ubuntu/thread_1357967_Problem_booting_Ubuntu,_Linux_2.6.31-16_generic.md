---
title: "Problem booting Ubuntu, Linux 2.6.31-16 generic"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by bamim2 on 2009-12-17
I have been using Ubuntu, Linux 2.6.31-16 generic, but for some reason when I try to boot up now, I get an error about it being unmountable. If I reboot and choose Ubuntu, Linux 2.6.31-14 generic, my system boots fine. What do I need to do get my system to boot from or reinstall Ubuntu, Linux 2.6.31-16 generic? 

It would also help if somebody would explain this to me. Does Ubuntu keep a backup filesystem to boot from or something? 

I'm currently booted into Ubuntu, Linux 2.6.31-14 generic.

---

### Post by Temposs on 2009-12-17
Is it necessary for you to boot from 2.6.31-16? If you want, you could just boot from the other one until another new one comes out. There shouldn't be any noticeable difference.

---

### Post by Skidbladniir on 2009-12-17
When you open the OS, and the checks are preformed, wait for them to finish, press Esc, then type, "fsck";

---

### Post by theozzlives on 2009-12-17
> **Temposs said:**
> Is it necessary for you to boot from 2.6.31-16? If you want, you could just boot from the other one until another new one comes out. There shouldn't be any noticeable difference.

I tend to agree, install Startup Manager and set your default to 14. You probably won't know the dif.

---

### Post by bamim2 on 2009-12-17
Pardon my complete boneheadednes, but is there a way to just replace 16? It was working, but I must of corrupted it somehow. Can I just get another copy of 16 somehow? If so, where?

---

### Post by Temposs on 2009-12-17
> **bamim2 said:**
> Pardon my complete boneheadednes, but is there a way to just replace 16? It was working, but I must of corrupted it somehow. Can I just get another copy of 16 somehow? If so, where?

To do that, go to System->Administration->Synaptic Package Manager, do a search for linux-image-2.6.31-16-generic. It should be checked, or colored green. If it is, right click it and choose Reinstall. Click Apply a couple times and it should install once again. You'll need to restart after it's done and see if it works :-)

---

### Post by bamim2 on 2009-12-18
I tried that & now when I boot it dumps me at an sh> prompt. It looks like the Linux version of the Solaris ok> prompt. It would appear that I've blown out the OS. 

Any suggestions now? Is there any way to boot up from the sh> prompt? Is the any way to undo this by booting from a CD? Or do I reinstall & consider this a learning experience?

---

### Post by Temposs on 2009-12-18
I would just set the linux-image-2.6.31-14-generic kernel as your default boot kernel for now, like I said before. Wait for the next kernel update and try that one.

---

### Post by bamim2 on 2009-12-18
I'd love to be able to get that far. Unfortunately, now my system just boots to the sh> prompt & that's it. It doesn't load the kernel. Is there a way to manually load the kernel?

---

### Post by jamieleshaw on 2009-12-18
Just select a different kernel in the grub(bootloader) screen

---

### Post by Temposs on 2009-12-18
When you turn on the computer, it'll say something like "Loading GRUB stage 2" or something similar...at that point press Escape, and it will give you a list of boot options. Choose the appropriate working kernel with the arrow keys and press Enter. That should do it.

---

### Post by bamim2 on 2009-12-18
I think it's crashing when it tries to start the grub loader. It dumps me to a command line with header that says something like, "Grub version xxx. You have limited Bash shell capabilities..." & I believe the command line says "grub:sh>" or something similar. I can type "ls -alh", but there's only one file called "boot0" or something like that. There are no directories or anything. I can type help & get a list of commands like "lsmod" & "insmod" for loading modules. 

Am I dead? or is there a way to boot the boot file up & load the kernel?

---

### Post by jamieleshaw on 2009-12-18
You'll need to recover GRUB from the a LiveCD.
If you are using Karmic this might be useful
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
Good luck

---

### Post by Temposs on 2009-12-18
Maybe someone else knows, but I'm stumped if you can't get grub going. At that point I would probably be reinstalling the OS.

---

### Post by Temposs on 2009-12-18
> **jamieleshaw said:**
> You'll need to recover GRUB from the a LiveCD.
If you are using Karmic this might be useful
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
Good luck

Yeah, try this first if you'd like. If that doesn't work, time to reinstall the OS :-)

---

### Post by jamieleshaw on 2009-12-18
Just follow the instructions in the link I gave you (if you are using karmic)
to re-instate grub.

---

### Post by bamim2 on 2009-12-18
I doesn't get that far.

---

### Post by lidex on 2009-12-18
You're using Karmic? Try holding down the shift key after bios screen to bring up grub menu. If you can do that, choose the kernel option that boots. If it boots, then run these commands in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

[Grub 2]("http://ubuntuforums.org/showthread.php?t=1195275")

BTW is this a wubi install?

---

### Post by jamieleshaw on 2009-12-18
> **bamim2 said:**
> I doesn't get that far.
To boot from the cd you need to bring up your bios boot menu, for me it's the F8 key at the Bios screen.

---

### Post by bamim2 on 2009-12-18
Thank you to all who tried to help me on this. I messed it up too badly & had to reinstall.

---

