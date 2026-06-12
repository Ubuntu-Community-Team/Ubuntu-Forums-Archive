---
title: "Reinstalling Windows"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by Guigwime on 2009-10-03
I installed Xubuntu a while ago to see if I could get better battery life from my netbook then Windows did. Unfortunately, it didn't :(
In my rush, I installed Xubuntu over the entire hard drive, so nothing remains of the previous Windows install. I've been trying to install xp or win7 from my usb and external hdd, but my netbook doesn't register either of them and all I get is "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key"
Now, everytime I boot my netbook I press esc so that I can boot from my usb but it still gives the error above.
Maybe it's a sign Ubuntu doesn't want me to leave, but I do.

Anyway, I've used win2flash, petousb, cmd prompt with no success.
I'm wondering now if there is any way to install windows while running ubuntu. Like wubi when you transfer from windows to ubuntu. I don't want some vmware because I want my better battery life back.

Can anyone help?

---

### Post by diablo75 on 2009-10-03
So you're trying to install Windows from a USB flash drive, right?  How was this flash drive created?  (I'm assuming that because you said "netbook" that this device doesn't have a CD-ROM attached).

---

### Post by Paddy Landau on 2009-10-03
I think that for better battery life, you'll need a new battery!

Ubuntu has Wubi to install Ubuntu in Windows, but guess what, Microsoft hasn't created an "Ubwi" to install Windows in Ubuntu (gee, I wonder why not!).

Ubuntu won't prevent you from installing Windows over it. Usually, there's some key you need to press (e.g. F12) while booting to tell the computer to boot from something other than the internal hard drive. Check your computer's documentation to find out.

Try the original installation disks that came with your netbook and follow the instructions carefully.

How old is your netbook?

---

### Post by ajgreeny on 2009-10-03
The problem is more likely that you are trying to install Windows into a disk formatted with ext3, which means that the install disk can not see there is a disk there to install to.  Use gparted on the Live CD eqivalent on a flash drive to delete the partition on which xubuntu was installed and then the unallocated space should be available.

---

### Post by Guigwime on 2009-10-03
Thx for the tips guys, I just bought a new 4gb flash drive so I didn't have to figure out my external hard drives troubles. And it seems to have worked. Read on:

> **diablo75 said:**
> So you're trying to install Windows from a USB flash drive, right?  How was this flash drive created?  (I'm assuming that because you said "netbook" that this device doesn't have a CD-ROM attached).

At first I tried formatting an external hard drive(Fantom G-Force) to FAT32 and putting the iso files (so, extracted and moved) into it. That didn't work. I also tried formatted with NTFS. I then found out I needed the bootsect and used a command line call. Something like BOOTSECT.EXE/NT60 H:. Anyway, that didn't work either. I tried a couple different approaches and it still didn't work. 

So I started to suspect that it was actually the external hard drive that wasn't being detected on boot, though it could detect it fine in ubuntu(netbook) and my pc(hp laptop). So after trying to and failing to install Windows XP with just a 2gb flash, I went ahead and bought a 4gb flash so that I could put in windows 7. Using [this](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/) method(or in url below), I was able to install wipe ubuntu and install Windows7 on the whole hard drive.

[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/]("http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/")

> **Paddy Landau said:**
> I think that for better battery life, you'll need a new battery!

Ubuntu has Wubi to install Ubuntu in Windows, but guess what, Microsoft hasn't created an "Ubwi" to install Windows in Ubuntu (gee, I wonder why not!).

Ubuntu won't prevent you from installing Windows over it. Usually, there's some key you need to press (e.g. F12) while booting to tell the computer to boot from something other than the internal hard drive. Check your computer's documentation to find out.

Try the original installation disks that came with your netbook and follow the instructions carefully.

How old is your netbook?

Haha, yes well, I'm not exactly thrilled to go back to Windows either.

As for what you mentioned about the battery, well, I'm hoping I don't a new one cause I just bought this netbook less then a year ago(Asus EEEPC 1008HA)(Great model btw) :P

With Windows7, I've been able to clock about 9.5 hours of battery life. Unfortunately, with Xubuntu, it could only reach about 7.5. I tried tons of different power management tools, but it just didn't seem to make it any better(Which was odd).

As for the boot, to get to the boot select, I press escape.
No CD/DVD drive(Should have mentionned it earlier, sorry) :P

> **ajgreeny said:**
> The problem is more likely that you are trying to install Windows into a disk formatted with ext3, which means that the install disk can not see there is a disk there to install to.  Use gparted on the Live CD eqivalent on a flash drive to delete the partition on which xubuntu was installed and then the unallocated space should be available.

Actually, the installer was able to "detect" it and name is at unknown I believe so I was able to reformat and install.

On an unrelated note about gparted. When I opened it up, I couldn't resize my main partition. If I right-clicked it would just be grayed out. Do I need to start it with sudo(ie privileges)? Or

---

### Post by tom66 on 2009-10-03
AFAIK, Windows won't install from a USB device (because Microsoft won't allow you, and it makes it easier to install a non-genuine version)... Ubuntu will, but only with some persuasion, it takes a lot of messing around, it's not as easy as extracting an ISO on to a drive.

---

### Post by Paddy Landau on 2009-10-04
> **Guigwime said:**
> On an unrelated note about gparted. When I opened it up, I couldn't resize my main partition. If I right-clicked it would just be grayed out. Do I need to start it with sudo(ie privileges)?
GParted can resize a partition only if the partition is not mounted, and it is in a format that GParted recognises. So, first check that the partition is not mounted. Second, if it's NTFS, you may need to install ntfsprogs first.

BTW, it's *strongly* recommended to *not* use GParted to resize or move NTFS partitions; it seems to be buggy. While some people have never had a problem, other people have lost their data. Use Windows's utilities, if possible, to resize or move NTFS partitions. (Not that Windows's utility is terribly good.)

---

