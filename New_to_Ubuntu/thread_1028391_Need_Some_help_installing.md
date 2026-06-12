---
title: "Need Some help installing"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Platyrunner on 2009-01-02
Ok heres the deal:

I got a free cd from canonical with 8.10 ubuntu iso and I really want to get this into my new Asus notebook (Centrino 2, 4 GB RAM, 320 GB disk)

I had to use the "help me boo from CD" option in the autorun menu of the CD, and I got to boot the live cd. However, I was never taken into the pre-boot ubuntu menu asking me to "install or run". I was taken directly into the OS (GUI worked fine).

Here's the major problem: I can't do anythin in the OS. No application load, I can't use anything. Worse of all, I CAN'T INSTALL UBUNTU. Since it won't load it, I am just stuck looking at the killer GUI. Unfortunately, that's not gonna get me ubuntu or write my term papers :|.

I tried the disk on my XP desktop, and everything worked (slow, sure, but it worked). On my XP, the splash screen also showed up and it asked me pre-boot if I wanted to run it. Bottom line, the CD is fine.

Basically, I need some help installing.

---

### Post by donkyhotay on 2009-01-02
I've occasionally had issues installing from the liveCD myself. I don't know what causes it specifically but I work around it by installing with the alternate installer. Unfortunately it's a seperate download.

---

### Post by Law506 on 2009-01-02
It is possible your cd is messed up.  I usually burn my own and have had one or two go bad.  If that cd won't work I would recommend going to [www.ubuntu.com](www.ubuntu.com) and download a copy there and burn it yourself and see what happens.

---

### Post by Platyrunner on 2009-01-02
Well, the CD ran fine in my desktop.

Either way, I am currently trying to make a 64 bit 8.10 CD. 

Would it be possible for the Cd to work in one computer and not another?

---

### Post by sadaruwan12 on 2009-01-02
could u just tell me what is the CPU you have in the notebook

---

### Post by abn91c on 2009-01-02
you are supposed to make sure your cdrom is the first boot drive, put in the live cdrom start PC then select **[COLOR="Red"]"try ubuntu without installin[/COLOR]**g". Any other "help me Boot option" may not work with your laptop

---

### Post by Platyrunner on 2009-01-02
So I have to access BIOS to get to run CDROM before disk, then?

I am using an Intel Centrino 2 CPU, btw.

---

### Post by Platyrunner on 2009-01-02
Now that you mention it the "help me boot from CD" may be the problem. I never used that on my desktop and it worked like a charm. Then again, my desktop always read CD, floppy, then disk for an OS.

---

### Post by abn91c on 2009-01-02
> **Platyrunner said:**
> So I have to access BIOS to get to run CDROM before disk, then?

I am using an Intel Centrino 2 CPU, btw.
Yes change the boot order to cdrom then HDD, then "try ubuntu without installing:" When you get to the desktop, make sure all your hardware works, like sound, screen resolutions,etc.. if the laptop "likes" ubuntu then just click on the installation icon :D

---

### Post by Coder543 on 2009-01-02
make sure you are using the correct number of bits when you selected the download for the Ubuntu desktop (non-server) cd.

---

### Post by xiaomahe on 2009-01-02
hi there..

i hope i can help a bit here, although i am still noobie..

If all the booting device is already setup and you can't install the OS, there are might be some defects on your disk. You can try to check the defects from the Ubuntu's boot menu.

Today i want to install ubuntu 8.10, and i just can't install it. I checked the defect and found 3 defects. So, i guess the CD itself it's not good.

Hope can help you..

---

### Post by Platyrunner on 2009-01-02
Now, does the 32 bit OS allow 4gb RAM?

I am not sure which OS was loaded in the canonical disk. I was never prompted to choose.

---

### Post by abn91c on 2009-01-02
> **Platyrunner said:**
> Now, does the 32 bit OS allow 4gb RAM?

I am not sure which OS was loaded in the canonical disk. I was never prompted to choose.
I have nowhere near that much ram, but from what I seen in the forums by other users the answer is no, it probably will detect 3.2 or 3.6 Ram as reported by other users.

---

### Post by snova on 2009-01-02
> **Platyrunner said:**
> Now, does the 32 bit OS allow 4gb RAM?

I am not sure which OS was loaded in the canonical disk. I was never prompted to choose.

All your memory will work.

---

### Post by Platyrunner on 2009-01-02
Ok, so if all ram is allowed, then why even bother getting 64 bit?

I mean, I know my processor is 64 bit, but it is backwards compatible...

---

### Post by snova on 2009-01-02
> **Platyrunner said:**
> Ok, so if all ram is allowed, then why even bother getting 64 bit?

I mean, I know my processor is 64 bit, but it is backwards compatible...

On second thought: [http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

---

### Post by Platyrunner on 2009-01-02
Ok, so i guess it's 64 bit for me then :)

I got the image anyway, I'll just put it on a disk.

---

### Post by Coder543 on 2009-01-03
A 32-bit OS mathematically should get 4gb ram. I have no clue on the planet as to why people are only able to detect something like 3.6gb ram. 32-bit means that the OS is using 32-bits to find a region in memory. The maximum value a 32-bit variable can hold is 4.2949673E9.
4.2949673E9 / 1024 = 4194304 kb
4194304 / 1024 = 4096 mb
4096 / 1024 = 4 gb

Please, correct me if I am wrong. But it is stupid for an OS not to be able to handle 4 gigs if it is 32 bit. You should be given access to just as much memory (technically, more) as if you had 64 bit. 64-bit shouldn't make usb devices take up less room. Doubling the size of a memory address means it takes up more room in memory. So... do you really get more memory in 64bit?

---

### Post by handydan918 on 2009-01-03
> **Coder543 said:**
> A 32-bit OS mathematically should get 4gb ram. I have no clue on the planet as to why people are only able to detect something like 3.6gb ram. 32-bit means that the OS is using 32-bits to find a region in memory. The maximum value a 32-bit variable can hold is 4.2949673E9.
4.2949673E9 / 1024 = 4194304 kb
4194304 / 1024 = 4096 mb
4096 / 1024 = 4 gb

Please, correct me if I am wrong. But it is stupid for an OS not to be able to handle 4 gigs if it is 32 bit. You should be given access to just as much memory (technically, more) as if you had 64 bit. 64-bit shouldn't make usb devices take up less room. Doubling the size of a memory address means it takes up more room in memory. So... do you really get more memory in 64bit?

I believe the issue is that there is other memory that gets addressed besides ram, i.e., video memory, etc.

---

