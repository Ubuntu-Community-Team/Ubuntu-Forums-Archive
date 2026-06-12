---
title: "Grub/External HD problems"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by cheph on 2009-11-28
Hi all,

So I have installed Ubuntu 9.04 on my external HD (my internal does not have space for it), windows (vista) on my internal. when I detach my external HD from my laptop and I try to run windows Grub runs and gives me a Error 21 message. Sometimes when i try to run Ubuntu I get error 5 and have to force a restart untill the grub menu will load. Last time i tried to install Grub on my internal but that messed up my MBR and I couldn't load Windows at all, I fixed that but still have my original problem of not being able to boot windows when I detatch my external HD.

[SIZE=2][COLOR=#000000][FONT=Segoe UI]"sudo fdisk -l" gives this result

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6914ecfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       14201   114021337+   7  HPFS/NTFS
/dev/sda3           14202       14593     3148740    f  W95 Ext'd (LBA)
/dev/sda5           14202       14593     3148708+  dd  Unknown

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00038216

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3891    31250000   82  Linux swap / Solaris
/dev/sdb2            3892       91201   701317575   83  Linux


The 750GB one is the external

Any help would be much appretiated

cheph

P.S.
other schemes i have tried that did not work:
-using an ubuntu live cd when the external is detatched to boot grub
-using a 'Super Grub' CD to load grub when external is detatched
[/FONT][/COLOR][/SIZE]

---

### Post by namok on 2009-11-28
You have an *'Grub error 21'* because Grub is installed i internal HD MBR. You need to install Grub on external HD. So:
1. Boot to Ubuntu.
2. Install Grub on external HD (Ubuntu is on sdb2 -Yes?):
```
sudo grub
find /boot/grub/menu.lst - to be sure
     (hd1,1)
root (hd1,1)
setup [COLOR=Red](hd1)[/COLOR]
quit
```3. Restore Vista bootloader to internal MBR: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by cheph on 2009-11-28
(accidentally posted twice, sorry)

---

### Post by cheph on 2009-11-28
hey,

So I tried those commands and got this results in grub:

```
grub> find /boot/grub/menu.lst 
 (hd1,1)

grub> root (hd1,1)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

I then I shut down and tried to run windows with my external HD detached from my laptop but still got Grub Error 21. I reattached my external HD and I could still boot windows and Ubuntu but I still cant boot windows with my external HD detached.

---

### Post by ed-koala on 2009-11-28
Personally, I would always keep OS files on my internal hdd and use the external for storage only, makes for less problems.

If you want to go to the trouble, make a new partition on your external drive and move all your movies, documents, etc, etc, etc, over to it (also serves as a backup).

Then, once all your stuff is "saved" to the new partition, reconfigure all the other partitions, install the OS'es to the internal drive, and you're set.

A true p.i.t.a., and probably not necessary, but I gave the advice anyway.

---

### Post by cheph on 2009-11-28
You see I want to avoid installing Ubuntu on internal HD because it is my main OS and when I do run windows (I would lose it but I need a program called Scratch Live for my DJ equipment to work and it only runs on windows) it crashes a lot (about once an hour lately). I'm not sure if thats the Internal HD or vista that causes the crashes but I have had problems with my internal HD befor.

I had the idea of making a small partition on my internal HD and putting Xubuntu or Ubuntulight on it just so grub will load on my internal HD with the external HD detatched. So I would still use my Ubuntu on the external HD as my main OS. The problem is that this seems ineffecent as I am installing a whole OS just so grub will work. Anyone know of a way to lets say make a partition on my internal just for grub? or just a more effecent workaround of my problem?

---

### Post by presence1960 on 2009-11-28
> **cheph said:**
> hey,

So I tried those commands and got this results in grub:

```
grub> find /boot/grub/menu.lst 
 (hd1,1)

grub> root (hd1,1)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

I then I shut down and tried to run windows with my external HD detached from my laptop but still got Grub Error 21. I reattached my external HD and I could still boot windows and Ubuntu but I still cant boot windows with my external HD detached.

You now need to restore windows to MBR of internal disk. Follow the link after the instructions you used to put GRUB on MBR of external drive from namok in post #2.

You will need a Vista install DVD. If you don't have one you can download an iso and burn it to CD as an image to boot into Vista Recovery Console. Get it [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). Boot either that CD or your Vista installation DVD and follow the instructions in the link namok gave you.

This will put Vista on MBR of your internal disk. When you boot without external HD you will boot right to Vista. When you boot with the external plugged in you will get GRUB and can boot into Ubuntu. Currently GRUB is on MBR of your internal disk and looks to your external HD for files needed to boot. When external disk is unplugged you get the error because it can't find those files.

---

### Post by Bartender on 2009-11-28
Have a friend go to this website and download the appropriate version of the Vista Recovery tool, then burn it to a CD so that it's bootable.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Then go back to your PC, unplug the external, boot from the CD, and fix the Vista MBR.  I guarantee you Vista will work again.

Now, you've got nothing to lose by reinstalling Ubuntu to the external, right?  Unplug the internal HDD (you can just pull the power plug) and boot up with the Ubuntu installer CD.  Ubuntu should only see the one external HDD.  Make sure by trying to scroll thru the little window upper right corner of the partitioner page that there are no other disks.

Install Ubuntu to the external HDD.  As long as no other HDD's are recognized by the installer, the part of GRUB that's tripping you up will be installed to the external instead of the internal.

When you're done, plug the internal back in.

Then you can do a couple of things.  One is to go into BIOS and set USB first as boot device, before the internal HDD.  With the external plugged in, Ubuntu will boot up.  With the external unplugged, Windows will start.

Must type faster.  presence beat me to it with the Vista fixer!

---

### Post by presence1960 on 2009-11-28
> **Bartender said:**
> Have a friend go to this website and download the appropriate version of the Vista Recovery tool, then burn it to a CD so that it's bootable.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Then go back to your PC, unplug the external, boot from the CD, and fix the Vista MBR.  I guarantee you Vista will work again.

Now, you've got nothing to lose by reinstalling Ubuntu to the external, right?  Unplug the internal HDD (you can just pull the power plug) and boot up with the Ubuntu installer CD.  Ubuntu should only see the one external HDD.  Make sure by trying to scroll thru the little window upper right corner of the partitioner page that there are no other disks.

Install Ubuntu to the external HDD.  As long as no other HDD's are recognized by the installer, the part of GRUB that's tripping you up will be installed to the external instead of the internal.

When you're done, plug the internal back in.

Then you can do a couple of things.  One is to go into BIOS and set USB first as boot device, before the internal HDD.  With the external plugged in, Ubuntu will boot up.  With the external unplugged, Windows will start.

Must type faster.  presence beat me to it with the Vista fixer!

Your opinion counts too! Op now hears the same thing  again.

---

### Post by cheph on 2009-11-28
OK so I did the Vista repair command prompt thing and that much worked, I can now boot windows without my external HD detatched. However now when I try to boot Ubuntu from the grub menu list (external now attatched) I get Error 17 cannot mount partition.

I booted my Ubuntu live cd and in the command prompt i wrote ```
sudo grub
``` whitch it did not recognize and then ```
grub
``` witch it said was not installed.

Were getting close guys I can feel it, thank you for your help so far, just one last issue to solve.

---

### Post by presence1960 on 2009-11-28
> **cheph said:**
> OK so I did the Vista repair command prompt thing and that much worked, I can now boot windows without my external HD detatched. However now when I try to boot Ubuntu from the grub menu list (external now attatched) I get Error 17 cannot mount partition.

I booted my Ubuntu live cd and in the command prompt i wrote ```
sudo grub
``` whitch it did not recognize and then ```
grub
``` witch it said was not installed.

Were getting close guys I can feel it, thank you for your help so far, just one last issue to solve.

This may be a dumb question but did you boot the Live CD/USB with the external plugged in? Did you boot a 9.04 Live CD/USB?

---

### Post by cheph on 2009-11-28
It was a 9.10 live CD, I am not sure if I forgot to plug in the external when I booted the Live CD though. I will try again now real quick and see.

---

### Post by presence1960 on 2009-11-28
> **cheph said:**
> It was a 9.10 live CD, I am not sure if I forgot to plug in the external when I booted the Live CD though. I will try again now real quick and see.

I am not sure if a 9.10 Live CD will do it. I am not sure only because I never tried it. You have 9.04 installed so I would use a 9.04 Live CD. But then again if the external isn't plugged in there is no grub for the command to locate.

---

### Post by cheph on 2009-11-28
Ok I just tried again with The external attached (this time I am sure) and got the same result, I will download a 9.04 live CD and try with that.

---

### Post by presence1960 on 2009-11-28
> **cheph said:**
> Ok I just tried again with The external attached (this time I am sure) and got the same result, I will download a 9.04 live CD and try with that.

something is amiss. you ran that command before and here is your result you posted:

```
grub> find /boot/grub/menu.lst 
 (hd1,1)

grub> root (hd1,1)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

Do me a favor and with the external HD plugged in from a Live Cd post the output of this command ```
sudo fdisk -l
```

---

### Post by cheph on 2009-11-28
Ok so to clarify I got that result when I was on the Ubuntu on my External HD, which I can not access now, not on my Ubuntu Live CD.

I ran that command on my live CD and got this result:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6914ecfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       14201   114021337+   7  HPFS/NTFS
/dev/sda3           14202       14593     3148740    f  W95 Ext'd (LBA)
/dev/sda5           14202       14593     3148708+  dd  Unknown

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00038216

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3891    31250000   82  Linux swap / Solaris
/dev/sdb2   *        3892       91201   701317575   83  Linux


```

---

### Post by presence1960 on 2009-11-28
> **cheph said:**
> Ok so to clarify I got that result when I was on the Ubuntu on my External HD, which I can not access now, not on my Ubuntu Live CD.

I ran that command on my live CD and got this result:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6914ecfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       14201   114021337+   7  HPFS/NTFS
/dev/sda3           14202       14593     3148740    f  W95 Ext'd (LBA)
/dev/sda5           14202       14593     3148708+  dd  Unknown

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00038216

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3891    31250000   82  Linux swap / Solaris
/dev/sdb2   *        3892       91201   701317575   83  Linux


```

Two things, do both from Live CD.

Open a terminal and run ```
gksu gparted
``` Select your sdb (external disk) top right. Highlight sdb2 and right click. Choose manage Flags. Untick the boot flag as linux does not need one. Click the green check mark (Apply).

From terminal run ```
sudo grub
```
From this prompt grub> type ```
find /boot/grub/stage1
```
Next type ```
root (hd1,1)
```
Next type ```
setup (hd1)
```
Then type quit

of course after typing each command hit Enter.
This should put GRUB back on MBR of sdb.
Reboot.

P.S. I just noticed that you ran a different command earlier. You ran ```
find /boot/grub/menu.lst
```
The commands to restore GRUB are :
sudo grub

at the grub>
find /boot/grub/stage1

root (hdx,y)     in your case (hd1,1)
setup (hd1)
quit

---

### Post by presence1960 on 2009-11-29
If you fail at the find /boot/grub/stage1 command, you will have to install GRUB from a 9.04 Live CD. See [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") for instructions. Obviously you are going to do this with your external plugged in. Your root device will be /dev/sdb2

---

### Post by cheph on 2009-11-29
Hey

That fixed it man! that was awesome thanks a lot. Everything works now and I boot Windows wile my external is detached.

Thanks again

---

### Post by presence1960 on 2009-11-29
> **cheph said:**
> Hey

That fixed it man! that was awesome thanks a lot. Everything works now and I boot Windows wile my external is detached.

Thanks again

Excellent! Glad you got it working. Enjoy Ubuntu. it rocks!

---

### Post by Toxicink on 2009-11-29
while attempting a dual boot I got this message  

Grub loading
error: unknown filesystem
grub rescue>

what do I do?

---

### Post by presence1960 on 2009-11-29
> **Toxicink said:**
> while attempting a dual boot I got this message  

Grub loading
error: unknown filesystem
grub rescue>

what do I do?

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

