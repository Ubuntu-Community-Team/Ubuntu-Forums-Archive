---
title: "Using different hard drives for different OS"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by ||Z0di4C|| on 2009-01-10
well i just built a computer it has 8gb of ram 1 terabyte of hard drive intel core 2 quad and vista 64 bit OS 

well that is a lot of power lol but you see Ubuntu just out performs vista in everything period

so i have an 80gb harddrive that i want to add into that computer and i want to have ubuntu loaded onto it so i have a couple of questions 

one what version of ubuntu will i need to run for 64 bit or does it matter

two how can i switch between the drives

three will these even work???

---

### Post by oldos2er on 2009-01-10
Go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and tick the box in front of 64bit version. When you install Ubuntu, it will also install a bootloader program called grub, which you can use to boot either operating system (Win* or Ubuntu).

---

### Post by RealPSL on 2009-01-10
Question 1:

Supporting 64-bit systems is not a problem for Ubuntu. I would recommend at least 8.04.1 or higher. You can access the download links below.

[http://releases.ubuntu.com/]("http://releases.ubuntu.com/")

---

### Post by ||Z0di4C|| on 2009-01-10
not sure i understand that grub program 

but couldnt i just go to my computer and click one hard drive or the other???

---

### Post by avtolle on 2009-01-10
By "switch between the drives" I presume you are talking about switching OS "on the fly". To my knowledge, to boot Ubuntu (while you are in Windows) or vice versa can only be done by a restart of the system. If you use a VM, you could go back and forth, as I understand it, but as I don't do this, my understanding may well be wrong.

---

### Post by avtolle on 2009-01-10
Grub allows you to select which OS to boot when starting your system.

---

### Post by oldos2er on 2009-01-10
> **||Z0di4C|| said:**
> not sure i understand that grub program 

but couldnt i just go to my computer and click one hard drive or the other???

 Here's info on grub: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

 I don't really understand your second question, are you asking if you can access one hard drive while booted from the other? If so, the answer's yes.

---

### Post by -kg- on 2009-01-10
I think he might be talking about switching the boot hard drive in BIOS.  The answer is yes...you can set each hard drive up separately with their own OS and their own boot loader, then depending on what OS you want to boot into, select that drive in the booting sequence in BIOS for the drive (and OS) you want to boot to.

Much easier, though, to just go ahead and install GRUB in the MBR of your bootable hard drive.  Upon booting, GRUB will present you with a list of bootable OSes, including Vista, that you can select and boot into.

---

### Post by anewguy on 2009-01-10
One thing to keep in mind also, since this is a new build.  If you plan on using wireless, be sure you can get the wireless driver and have it work in the 64-bit version.  From what I've read here on the forums, depending on the chipset in the wireless, it may be a challenge.  You might want to check the forums and ask here if you plan on using wireless to find a recommended wireless adapter that will work with little or no extra work.

Dave :)

---

### Post by ||Z0di4C|| on 2009-01-10
yeah like you can change drives in the my computer folder so what would be the best way to switch between operating systems and wat i mean is that i do not want any of the information from one OS get onto the hard drive that has the other OS

---

### Post by ||Z0di4C|| on 2009-01-10
so what your about the logging in and then swithcing to a different OS via GRUB wouldnt all the information be on one hard drive then opposed to two

---

### Post by avtolle on 2009-01-10
If I understand your question, the files used with the Ubuntu boot will be on the hard disk from where Ubuntu is booted; same with Windows. You could mandate under Ubuntu a file be stored on the Windows drive, if you mount it in the Ubuntu session, have the correct permissions, etc. to do so. There will not be any mixing of data files unless you cause it to be done. Is this what you are asking?

---

### Post by oopsdude on 2009-01-10
When you go to "My Computer", you're already in Windows. You might be able to see your Ubuntu hard drive from My Computer (although Windows tends to have trouble reading foreign filesystem formats), but you cannot switch to Ubuntu once you're already in Windows. You would have to restart your computer.

Grub is a bootloader - it's like a tiny, tiny OS that allows you to choose which regular OS to boot with. You would install Grub to a small portion of one of your hard drives, but Grub will be able to boot an OS from either drive. Each operating system does not need to know the other exists.

No information would be shared between the hard drives that contain each operating system, unless you do something on purpose. I think I see your misunderstanding - when you boot into, say, Ubuntu, Windows is not running. It is just dead files on a hard drive until you restart and choose to boot into Windows. Therefore, the operating systems do not "share data".

Also, please check the grammar of your posts. I can hardly understand your last one. Complete sentences help a lot.

Mike

---

### Post by osquid on 2009-01-10
You should have no problem with the two interacting if you put them on separate hard drives. They won't interact on one hard drive if they are partitioned separately. :KS

---

### Post by ||Z0di4C|| on 2009-01-10
yes see this may sound dumb because i do have a terabyte but i want all my linux stuff on one hard drive and vice versa for the windows

---

### Post by ||Z0di4C|| on 2009-01-10
okay so to finish everything im just going to double check

so i have ubuntu on my designated hard drive all right

now the over all decision here is that i use GRUB to switch between each OS is this correct???

---

### Post by osquid on 2009-01-10
Yes, and you can change the default boot order through ubuntu; see this page [http://ubuntuforums.org/showthread.php?t=186385]("http://ubuntuforums.org/showthread.php?t=186385")

---

### Post by anewguy on 2009-01-10
And, just for clarification as stated earlier, only 1 OS will be running at a time.  Unless you use a virtual machine, you cannot be in Windows and start or switch to Ubuntu, or vice versa.  Grub is used at boot, and while simplified here in this cheesy example, it gives you the option of choosing which operating system you want to start up:

- you boot your system (power on, reset, ctl-alt-del, whatever)

- in a little period of time you will be presented with a menu somewhat like the following:

(1) Ubuntu ........ kernel......

(2) Ubuntu recovery ......kernel.......

(3) Windows XP (or you might have Vista)

which operating system to you want to run: 1 <-default

will use default in xx seconds


Again, this is a cheesy example because I don't know if there is a way to do a screen capture at boot (I doubt it unless you are starting a virtual machine).

Also, as already stated, Windows would be on your drive "x", and Ubuntu would be on your drive "z".  Windows probably won't even show your Ubuntu drive.  Ubuntu might - but it will still be a completely different disk - you won't get mixing of files unless you purposefully move or write a file to it.

Dave :)

---

