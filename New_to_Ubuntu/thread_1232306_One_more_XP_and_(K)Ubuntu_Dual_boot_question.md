---
title: "One more XP and (K)Ubuntu Dual boot question"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by djbushido on 2009-08-05
I currently have two IDE drives with one windows XP and one Kubuntu. I had installed Kubuntu on another computer, and just migrated the drive. Now trying to chainload to XP isn't working. I wanted to confirm that I needed to install GRUB to the mbr of the windows DRIVE (not partition) and didn't know if there was a way that I could back up said MBR should it need to be re-installed later. Also, the windows partition is a bit weird - part type W95 FAT32 (LBA). So says fdisk. Also, windows is at sdb, but I can figure out the drive letter/number stuff myself, I have a bit of experience. Thanks for the help!
Also, is there a way to run the grub livecd installation stuff (so ubuntu will auto-detect it) without re-partitioning and losing all my data?

---

### Post by djbushido on 2009-08-05
It should probably be noted that I am wanting to do an Ubuntu master drive and windows slave. I just don't know how to get Grub to boot the windows drive. Correctly. Currently it just hands control to XP and then nothing happens.

---

### Post by Ji Ruo on 2009-08-05
You may run into problems later with that transferred Kubuntu drive. 

So you have Kubuntu on your primary drive, and XP on your secondary? You will need to have GRUB on the MBR of the XP drive only if it is the primary drive. If you're keeping XP as the secondary drive, you will need to do a virtual swap [http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html]("http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html"). This might not work though, as stated. 

IMO you are better off physically swapping the drives around, putting XP as the primary (where it wants to be). Then, go into your boot options at startup and boot from the secondary drive and then into Kubuntu. For this way, go into Konsole and enter this:```
sudo grub
``` to get into the GRUB editor. Then```
find /boot/grub/stage1
```You should get (hd1,0).
```
root (hd1,0)
setup (hd0)
quit
```This will wipe the MBR on XP, but it will get both of them working. I don't know how you might decide to back up your MBR, but you can fix the partition later with the Windows disc or other recovery disk if you decide to go back to just XP. You might have to try a few different methods, but one of them will work. Plenty of advice on the net for this already. You will only need to fix the Windows MBR if you want to go back to just Windows.

Again IMO, your best option is physically swapping the drives, then reinstalling Kubuntu again. It will prevent any stability problems occurring with Kubuntu and will do the GRUB work automatically.

---

### Post by Dr. Moreau on 2009-08-05
Some drives need to be physically configured as slave/master, with jumpers across the terminals near the power connection.  You probably knew that, but it was news to me when I installed a second drive last week.  I put Ubuntu on the slave (1) drive and used GRUB to set up the boot options.  Ubuntu ended up being the default boot OS, which is nice.

Good luck!

---

### Post by djbushido on 2009-08-06
I guess that I can put Windows as master, I just don't want to re-install Kubuntu. How would I set up Grub to point to Ubuntu? Note: My BIOS doesn't have a start-up drive list so booting from slave is not possible at this point in time.

---

### Post by LewRockwell on 2009-08-06
learn the awesome power of Grub and the SuperGrubDisk at:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and here:

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

and here:

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

and here:

[http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB)

(of course, these are only a few of the many)

.

---

### Post by Dr. Moreau on 2009-08-06
"How would I set up Grub to point to Ubuntu?"

On mine it just fell out that way.  Grub gives me a countdown and a list of OS to select from, with the cursor at the top of the list.  Ubuntu is the OS that automatically loads when I push the "on" button and do nothing else.  Slick.

---

### Post by djbushido on 2009-08-06
you do realize that alphabetics have nothing to do with it, right?
there is a file called "menu.lst" that gives GRUB the menu. You can move stuff around in there, and that will change where it shows up. However, I recommend against this, as you could very easily screw something up.
On that note, I believe I can fix this by setting Windows as master and installing GRUB to the MBR, I just want to make sure of this before I screw up my Windows install.

---

### Post by LewRockwell on 2009-08-06
> **djbushido said:**
> you do realize that alphabetics have nothing to do with it, right?
there is a file called "menu.lst" that gives GRUB the menu. You can move stuff around in there, and that will change where it shows up. However, I recommend against this, as you could very easily screw something up.
On that note, I believe I can fix this by setting Windows as master and installing GRUB to the MBR, I just want to make sure of this before I screw up my Windows install.

once you understand the hardware settings, BIOS settings, and Grub settings you'll feel much more comfortable working with your equipment, operating system(s), and other assorted software, peripherals, and accessories

actually, many find it invigorating and empowering to master simple tasks such as editing the grub's menu.lst file

.

---

### Post by djbushido on 2009-08-06
So do I need to put GRUB in the windows MBR?

---

### Post by Ji Ruo on 2009-08-07
> **djbushido said:**
> So do I need to put GRUB in the windows MBR?

You could try physically swapping the drives (cable and jumpers) and then changing your boot options in BIOS to boot from the secondary (ie. slave) hard drive. I'm not sure if you need to remove the +1 in the Windows section of menu.lst this way (I've only done it the other way, GRUB stage1 in Windows MBR).

---

### Post by djbushido on 2009-08-07
Finally got up the nerve to put GRUB in windows MBR. It works fine now, although I have a saved copy of the original MBR should I need to restore it later.

---

### Post by Dr. Moreau on 2009-08-07
As I recall, that's what I did, put Grub on the master drive.  At boot, the IDE looks on the old (C) master drive first and finds Grub which directs it to the new drive and Ubuntu without involving or impinging upon Windows at all.

And, no, you're correct, the boot list is not alphabetical.  Ubuntu is at the top of my list and is the default OS; other OSs are at the bottom of the list under "other systems".

Mine's running great, I hope yours does too.

---

### Post by djbushido on 2009-08-08
No, it does infringe on windows. In fact, if you lose your linux drive, windows will not be able to boot.
Anyway, so far as I can see, that is the only problem with the system, otherwise everything is working fine. Thanks!

---

