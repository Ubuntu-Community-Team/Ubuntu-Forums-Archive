---
title: "Adding new Hard Drives gives me Grub 22"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Operator8 on 2008-12-02
I read through this post:
[http://ubuntuforums.org/showthread.php?t=960528&highlight=grub](http://ubuntuforums.org/showthread.php?t=960528&highlight=grub)


Well I have a slightly different (I think) problem if anyone can assist.  I've been dual booting Ubuntu and Vista for months now with no problems.The other day I added 2 new hard drives (just for storage) bringing my total to 4. And that's when it stopped booting up and catching on the Grub 22.  Once I disconnect my 2 new SATA drives and reset my PC it boots up just fine.  If I try to reconnect them and reboot Grub 22 comes back up. I can usually yahoo or google search my way to an solution but can't seem to find what I need.

---

### Post by Moop on 2008-12-02
Adding the new hdd's probably changes the hdd that gets booted first in the bios. Add the hdd's and then go into your bios and select the correct hdd to boot from. If your not sure which one it is you can check the bios before adding the extra hdd's.

---

### Post by caljohnsmith on 2008-12-02
Your problem is most likely because you have Grub installed to the MBR (Master Boot Record) of a drive other than the drive where Grub's boot files are (i.e. the Ubuntu partition). When you connect your other drives, that changes the BIOS boot order, so Grub in the MBR looks on the wrong drive for its boot files and can't find them. I think the most ideal solution to your situation is if you can change your BIOS to boot the Ubuntu drive on start up; in other words, make the Ubuntu the first drive in the BIOS boot order. You'll need to install Grub to the MBR of the Ubuntu drive to make it bootable, and you can do that by first opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. Then if you reboot and set your BIOS to boot the Ubuntu drive, you should at least get the Grub menu. See if you can get that far or let me know if you run into problems; we can work from there if you want. :)

---

### Post by Operator8 on 2008-12-03
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd1,1)
 


grub> setup (hd1)  
setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

---

### Post by Operator8 on 2008-12-04
I've gone into the bios but can't seem to change the order of the drives there.

---

### Post by Operator8 on 2008-12-06
Any new advice?

---

### Post by masterofthemelee on 2008-12-06
It should definetly have an option to choose which hard drive to boot from.

---

### Post by nwadams on 2008-12-07
does the grub menu show up before it gives the error?
If so in the grub menu hit e, e, and edit the line that says root (hdx,#) play around with the x until it boots. And when you get it to boot edit your grub file so it permenantly is set to boot off the drive that boots ubuntu

Note: the above may be entirely irrelevant if I screwed up on which error you are having

But use the advice caljohnsmith, it will work

---

### Post by bumanie on 2008-12-07
I have never come across a bios on a desktop that doesn't have multiple options to choose from - laptops are a different matter, but to have that many hard drives, you must be using a desktop. Post the output of > sudo fdisk -luThis will need to be done from a live cd seeing you can't boot into ubuntu. Another option would be to try [supergrub disk]("http://www.supergrubdisk.org/").

---

### Post by Operator8 on 2008-12-07
I'll give the new advice a try.  Oh and I can boot to Unbuntu, just not with my 2 new drives connected.

---

### Post by Operator8 on 2008-12-09
When the new drives are unplugged the pc boots:

GRUB Loading stage1.5.

Then it goes to the screen that lets me choose to boot to Vista or Unbuntu. 

I then press "e" and it shows 

[B]root (hd0,0)
savedefault
makeactive 
chainloader +1[/B]

When I plug the new drives back in Grub Loading stage1.5. then immediately:
 
GRUB loading, please wait......
Error 22


Like I've stated, the pc runs like normal when the new drives (which have nothing on them) are disconnected.  I can boot into Vista or Unbuntu with no problems.  SO I'm not sure why the system gets confused when I plug them in.

nwadams, do i just need to add (hd1,1) on the edit screen?

---

