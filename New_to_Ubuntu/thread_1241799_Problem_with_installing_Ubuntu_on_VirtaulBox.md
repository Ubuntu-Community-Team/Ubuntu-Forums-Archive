---
title: "Problem with installing Ubuntu on VirtaulBox"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by kochaviy on 2009-08-16
Hello All,
 I am having troubles trying to install Ubuntu 9.0.4 On VirtualBox 3.0.4 running on Windows XP sp2. I have a p4 machine with 1GB of RAM. 
This is what I do:
In the VirtualBox I choose ***'New'  ***and then follow  the wizard steps according to the tutorial. I create a new virtual HD and mount a .ISO file of ubuntu installation,  now all is set. I start the VM. It Boots OK and starts the installation but when I choose '***Install Ubuntu***'in the startup Window nothing happens and the only thing I can do with the VM is close (stop) it.

I have 2 HD. 80GB and 40GB. The large one has 2 partitions: C:\ (20GB - for Windows XP only 1GB is free) and D:\ (~60GB  13GB is free).  The small HD is G:\ and is free. At first I located the .vdi file in g: (which I can see in BIOS) . It got stuck. Then I thought: should g: be bootable? I located the .vdi file on d:\ . That didn't help. I tried it on c:\ and nigher did this. 

any suggestions?

:confused:

---

### Post by kaptain0 on 2009-08-16
I also had problems installing Ubuntu on Qemu on Xp and Vista. It just stopped halfway through or never made it past the boot screen.
 
I know that doesn't help you, sorry

---

### Post by kochaviy on 2009-08-16
Thank you any way for replying. Did you find a different VM to install it on?

---

### Post by squenson on 2009-08-16
How much memory did you allocate to your guest Ubuntu? I think Ubuntu will not install itself if you have less than 256 MB. Also, what is the size of your virtual hard drive?

---

### Post by D3M0L1$H3® on 2009-08-16
You need your virtual hard drive to be at least 10gb, some more is preferrable.
You need to give your Ubuntu VM at least 300 MB of RAM, just to be safe.
And it's a good idea to not have much else running on windows while installing the Virtualbox/Ubuntu for various reasons.
Past that, it should work. For whatever reason, a fresh VirtualBox install could be slightly useful.

Good Luck

---

### Post by kochaviy on 2009-08-16
I allocated 384 MB of RAM in all tries.  On g:\ (37GB)  I created the .vdi file to be static allocated in the size of ~34GB . I also tried to dynamically allocate the .vdi file, and on all other tries I used the default wizard recommendations.

---

### Post by kochaviy on 2009-08-16
Actually, starting over never hurts... will try . Thanks for now

---

