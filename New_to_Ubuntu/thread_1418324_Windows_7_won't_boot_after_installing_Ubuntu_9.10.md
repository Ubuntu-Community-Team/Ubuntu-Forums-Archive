---
title: "Windows 7 won't boot after installing Ubuntu 9.10"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by jmoran19 on 2010-02-28
Hi, hopefully someone can help me with this, since there seems to be dozens of threads similar to my situation yet unintelligible to me.

So I recently did a fresh install of Windows 7 Professional x64, and in the process decided I would install Ubuntu to dual boot on the computer. The machine uses two 250GB drives in a RAID 0 configuration, so during the Windows 7 install I gave it a 400 GB partition, leaving about 70 GB free space to install Ubuntu. Got Windows up and running, no problems, had all my data back in place and was ready to tackle Ubuntu.

I didn't have any major issues on the Ubuntu installation, either. I picked the free partition for the OS and proceeded to install. I was up and running soon after, and assumed everything was a-o-k.

However, when I rebooted I noticed that the boot manager was different that what I'd seen when dual booting two Microsoft OS'es, which worried me. (I now understand that this is GRUB) Far more frightening was when I selected the W7 OS from the list, only to have the computer crash in the middle of booting up. During the loading MS logo, I catch a brief glimpse of a BSOD, followed by my monitor going to sleep and my computer's fan continuing to run but otherwise remaining inert. Safe Mode does the same thing, crashing without a visible error on boot and with a brief flash of BSOD.

Startup Repair was no help, since this was a new installation, and I stupidly assumed that I always had the out of reformatting and doing it all again, I didn't make any kind of system backup disk. If I choose automatic repair, it simply fails, with the details making it look like the process was a complete non starter. Finally, the program itself tells me that it can't find any hard drive in my computer.

The invisible hard drive has also prevented me from reinstalling Vista (I have a W7 upgrade disk, Vista full version) from scratch, as well as from using the repair feature on my W7 upgrade disk. To remedy this, I tried pointing to the original manufacturer's driver disk for hard drive drivers (it says it cannot find signed drivers) and I tried downloading the SATA drivers directly from the same website and pointing to that .exe (same error, says they are not valid signed drivers).

At this point, I'd love to find out I need to modify GRUB in some way, as I've seen suggested in one thread found via google. I know the data is all there, I can see it from the working-fine Ubuntu install. On the flip side, I'm not opposed to doing a complete reformat and fresh install of W7, which is my priority OS since this is a gaming computer for the most part and I just want to learn Linux for fun. However, without knowing how to make Windows Installer detect my hdd, I don't even know how to do that.

If anyone has any advice, I'm incredibly desperate. Step by step instructions would be best, to be safe, but at this point I'll take anything I can get. Please offer any suggestion and I'll reply with requested info asap.

---

### Post by jmoran19 on 2010-02-28
Just a few updates for anyone who wants to chime in...

GParted says that the Windows partition still has the boot flag attached to it.

When booting W7 in safe mode, the file it appears to hang on when loading is C:\Windows\system32\DRIVERS\disk.sys.

Any thoughts would be much appreciated!

---

### Post by linuxman94 on 2010-02-28
Sounds to me like installing ubuntu did something to your windows partition.

---

### Post by jmoran19 on 2010-02-28
Could be, but then why isn't the hard drive visible to the windows vista/windows 7 install? I could try formatting with Gparted Live and then reinstalling if I knew that Ubuntu is creating a conflict, but I'm worried that windows still won't see the hard drive after that, and then I'll have a problem installing Ubuntu, and then I will be truly fubared.

---

### Post by rixtr66 on 2010-02-28
probably not what you want to hear,but i had the same prob w/win7
and ubuntu.and i had to reinstall 7.for the most part i have installed ubuntu w/win7 successfully,as ive been testing ubuntu 10.4,but there was that odd one time that i got the bsod,and like you i tried everything to repair it to no avail,so i reinstalled.
and had no problems afterward.although i had to restore the grub to 
mbr,theres plenty of how to's on that.so the bad news is youll have to reinstall vista,then go through the upgrade to win7,and reset 
grub to the mbr.sounds like alot but i did it.
hope this helps.
Rick
edit;formatting with g-parted live is also what i use,just reformat the partition to ntfs,and you should be good to go,just leave the ubuntu partition alone,and after just restore the mbr to grub.

---

### Post by rahulerai on 2010-06-24
@jmoran19
helo friend...i am also facing this [COLOR="DarkRed"][SIZE="4"]exact[/SIZE][/COLOR] same problem!!did u manage to solve it??if u did,please explain how..That would be a great help..
thank you

---

### Post by wilee-nilee on 2010-06-24
> **rahulerai said:**
> @jmoran19
helo friend...i am also facing this [COLOR="DarkRed"][SIZE="4"]exact[/SIZE][/COLOR] same problem!!did u manage to solve it??if u did,please explain how..That would be a great help..
thank you

If you want some help start a thread and post the bootscript in my signature. When you copy and paste the readout from running it, to the thread highlight the text and click on the # in the posting/reply panel. This will put it in code tags and make it easier to read.

---

### Post by jsulem on 2010-08-06
I was also getting a BSOD and immediate reboot on Windows 7 startup after installing Ubuntu 10.04 (netbook remix).

The problem was that the c: drive was corrupt, but this was fixable by using 'chkdsk'.

I solved this by starting up a recovery/restore console (on my Toshiba NB255 Netbook this was done by booting the 'Windows Vista' partition in grub), starting a command line within the recovery console and then running 'chkdsk c: /f'.  Chkdsk found and fixed some errors on the drive and afterwards Windows 7 booted.

I've seen the recovery/restore partition installed by the manufacturer as standard on a few new computers, so you may well have one.  On one particular computer this had to be accessed by typing a magic set of keys during BIOS load (this was documented in the computer manual - search online for it).

---

### Post by JPWhite on 2010-11-13
> **rahulerai said:**
> @jmoran19
helo friend...i am also facing this [COLOR="DarkRed"][SIZE="4"]exact[/SIZE][/COLOR] same problem!!did u manage to solve it??if u did,please explain how..That would be a great help..
thank you

I had a very similar issue as well. Check out the last of my fixes at
[http://wp.me/pCOs1-cL](http://wp.me/pCOs1-cL)

---

### Post by gridleaf on 2010-11-20
I have the same problem, only when I try to boot anything, it just comes up with a blank screen. I've tried removing ubuntu and chkdsk on the hard drive, yet anything i try to do or boot or display from the hard disk just comes up with a blank screen.
Ubuntu was installed on an SD card, which I have tried everything with it in and out. Same result every time.
I also tried fixing the mbr, but that won't work either. I don't know how to get back any of the files, and i need in there.

---

### Post by wilee-nilee on 2010-11-20
> **gridleaf said:**
> I have the same problem, only when I try to boot anything, it just comes up with a blank screen. I've tried removing ubuntu and chkdsk on the hard drive, yet anything i try to do or boot or display from the hard disk just comes up with a blank screen.
Ubuntu was installed on an SD card, which I have tried everything with it in and out. Same result every time.
I also tried fixing the mbr, but that won't work either. I don't know how to get back any of the files, and i need in there.

Take a look at post #7 and follow the instructions including a personal thread and send me a PM if needed.;)

---

