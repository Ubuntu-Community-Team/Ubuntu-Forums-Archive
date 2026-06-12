---
title: "Unable to boot Windows 7 I/O error"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by notatheist on 2009-11-01
I'm completely new to Linux and needless to say the last couple of days have been a learning experience. It's taken me since 9.10 release just to get my wireless internet working well enough to not take 30 seconds to load every page. I'm trying to install Windows 7 on my machine but I get multiple I/O errors during the boot up process. I only get the errors on this PC that I'm running Karmic on. The install works fine on every other computer in my house. After the errors Ubuntu loads like normal and it doesn't recognize any discs in my drive.

---

### Post by rcayea on 2009-11-01
I am throwing some thoughts out there to get this guy some help from you more awesomer Ubuntu folks...

Question first: Do you have more than one hard drive with these installs?


If you can get into your BIOS I would disable any HD you may not be trying to install to.

---

### Post by notatheist on 2009-11-01
No, I'm running a single drive with Ubuntu 9.10 fresh install.

---

### Post by rcayea on 2009-11-01
Sounds to me that this is one of those, Microsoft-just-won't-let-you things happening. Any time I install a Windows on one of my other Hard drives, I have to disable my ubuntu or MS wont install. Sorry, I am at my limit of knowledge on this topic. Maybe someone else will come along and help. I am sure someone will. You are in the perfect distro community. :D

---

### Post by notatheist on 2009-11-01
I'm contemplating going into Disk Utility and deleting my linux partition. Then I'll try to boot with the Windows 7 CD. I'm just a little scared because If it doesn't work, I'll be kinda screwed. If anyone has any tips before I take that leap, I'm all ears.

---

### Post by ranch hand on 2009-11-01
Win JerryLewis Pro prefers to be the first install on the drive.  this is what you get when you install that kind of malware.

I believe that it is possible to hide the partition(s) that you have installed Ubuntu on from MS.  I am not sure how you do this but that may help.  Make sure that your partitions are as large as you want before trying to install MS as it will take all the rest of your drive.

You could also make your Ubuntu use the whole thing and install Virtual Box and install Win JerryLewis Pro there.  It will be safer there than it will be running loose.

Just for gigles run this in terminal;
```

sudo update-grub

```
I do not hold much hope for that as it is mainly useful when MS is not seen in the menu.

---

### Post by notatheist on 2009-11-01
Could anyone help me step by step? I need to completely remove Ubuntu from my machine so I can just run a fresh install of Windows 7.

Edit: When I try to install through Virtual Box I get a "FATAL: no bootable medium found! System Halted." error. The boot disc works fine on all other os's except Ubuntu.

---

### Post by ranch hand on 2009-11-01
I suspect that if you put in your MS disk and hit install, it will happily wipe your drive and install itself.

---

### Post by notatheist on 2009-11-01
When I put in my MS disc while in Ubuntu, nothing happens and the drives don't recognize any disc was inserted. When I boot from the CD it gives me I/O errors and then Ubuntu boots up like normal.

Now I booted Ubuntu from a disc and removed my linux partition. Starting up with my MS boot CD I get a grub partition not found error... I don't understand that at all. 

Once again the Win7 CD works fine on all my other machines that are running XP already.

---

### Post by ranch hand on 2009-11-01
Check your bios.  I do not think it is set to boot first from the CDrom.

---

### Post by notatheist on 2009-11-01
I just double checked and the CD drive is first priority when booting up. I've decided to try a full system recovery. I dug up my old xp discs and I still get a grub error when I attempt to boot my PC.

---

### Post by ranch hand on 2009-11-01
You better hit whatever key gets you to your bios boot menu when you are booting (should be right by the one that gets you into bios) because if you were really booting from the Cdrom you would not be getting error messages about your HDD.

---

