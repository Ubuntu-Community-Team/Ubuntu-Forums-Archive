---
title: "Ubuntu Boot Issues- Error 15"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by sirhceel23 on 2009-01-17
First off, thanks to everyone that has helped me in the past. Alright I'll just ask since I can't find the answer searching , and I managed to mess something up. Well I got Ubuntu and openSUSE installed on their partitions but I can't get Ubuntu to boot back up after the initial install after I installed openSUSE. When I click on Ubuntu to boot in the openSUSE bootloader program it pops up another selection screen asking which version of Ubuntu to boot up (which it contains 4 ubuntu options - 2 different kernals and safe modes and my windows vista) When I select the first ubuntu option I get:

kernal /boot/vmlinuz-2.6.27-9-generic root=UUID=d9d0d475-a8f3-4511-a06c-f457ed47bce4 ro quiet splash

Error 15: File not found

Press any key to continue..._

then when I press anything i brings me to the GRUB bootloader screen with all the ubuntu options and the windows options. None of the options work to boot in any of those options. It brings up an error 15 on all of them. Windows and openSUSE do boot up just fine from the openSUSE bootloader. SO it looks like to me, I just need to figure out a way to remove the Grub bootloader and fix the Ubuntu pathway in the openSUSE bootloader. (Sorry not sure if their is another name for it) So please, please just a little more help. I love my ubuntu!

Also if this helps at all this is what my partitions look like: Ubuntu is installed on /dev/sda6

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

Device Boot Start End Blocks Id System
/dev/sda1 1 22186 178207587 7 HPFS/NTFS
/dev/sda2 59655 60801 9213277+ 7 HPFS/NTFS
/dev/sda3 22187 28630 51761430 83 Linux
/dev/sda4 * 28631 59654 249200280 5 Extended
/dev/sda5 28631 29204 4610623+ 82 Linux swap / Solaris
/dev/sda6 29205 31762 20547103+ 83 Linux
/dev/sda7 31763 34328 20611363+ 83 Linux
/dev/sda8 34329 37570 26041333+ 83 Linux
/dev/sda9 37571 59654 177389698+ 83 Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4007 MB, 4007657472 bytes
16 heads, 32 sectors/track, 15288 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x0004ebe6

Device Boot Start End Blocks Id System
/dev/sdb1 * 16 15288 3909696 b W95 FAT32

---

### Post by caljohnsmith on 2009-01-17
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop (or your OpenSUSE desktop if you can boot OpenSUSE OK), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be

---

### Post by Truefire on 2009-01-17
Uh, his Ubuntu won't boot up - that won't work.

I'm afraid that your problem is a scary one - you may have nuked Ubuntu all together. The only way to really tell is to use a livecd to check the filesystem for Ubuntu.  If you do find it, use this cd in attempt to repair  grub:

[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

Good luck, sirhceel23.

---

### Post by sirhceel23 on 2009-01-17
OK I tries that command with no avail from the live ubuntu cd and openSUSE which does boot up just fine. I wonder if it would just be easier to wipe the Ubuntu partition and reinstall it without grub and add it into the openSUSE bootloader. Since that one works just fine. As for checking the filesystem using the live cd, how do I do that? Or possibly is there an alternate way to boot that partition to check if the filesystem is shot, or just grub? Its funny when I looked at repairing Grub, like say if it got overwritten, it comes back saying it cannot find it. Anyways let me know! I appreciate all the help!

---

### Post by sirhceel23 on 2009-01-17
OK I used SuperGRUB to repair the boot on /SDA6 and repaired grub to their and rebooted to GRUB which let me select Ubuntu. Ubuntu then begins to boot up but during boot up it pops up a cmd after awhile saying that the check system failed. It wrote it to this log: 

```
og of fsck -C3 -R -A -a 
Sat Jan 17 21:52:10 2009

fsck 1.41.3 (12-Oct-2008)
/home: clean, 1456/11091968 files, 764565/44347424 blocks
/: clean, 11/1630208 files, 146368/6510333 blocks
fsck.ext3: Unable to resolve 'UUID=222e2869-b653-4912-b623-2adef0d2aff8'

fsck died with exit status 8

Sat Jan 17 21:52:11 2009
```

Also this log as well: 
```
Log of fsck -C3 -a -t ext3 /dev/sda6 
Sat Jan 17 21:52:10 2009

fsck 1.41.3 (12-Oct-2008)
/: clean, 126520/1286144 files, 742749/5136775 blocks

Sat Jan 17 21:52:10 2009
----------------
```

It then allows me boot continue to boot up Ubuntu by pressing Ctrl+D. Then Ubuntu boots up normal so. Also, note that my openSUSE is not coming up in GRUB. I guess thats sorta a step in the right direction that I got Ubuntu to boot but see what you think.

---

### Post by Bezmotivnik on 2009-01-17
No, there's an installation bug at work:  I've repeatedly installed 8.10 to an older AMD/ASUS computer here with a single hard drive and a CD-ROM, allowing Ubuntu to completely format/use the single drive as it wishes.  No other OSs, the entire drive and computer dedicated to Ubuntu, no dual-boots, no nothing.  Totally plain installation.

I get Grub error 15 every single time I try to boot.

---

### Post by sirhceel23 on 2009-01-17
Nah, I'm pretty sure its related to the openSUSE install because it booted just fine before I installed it. Did you get it the Error 15 fixed or did you do a reinstall??? Also, after I get past the checksys error Ubuntu boots up.

---

### Post by sirhceel23 on 2009-01-17
Found an interesting post that may be sorta related.. Maybe its a name bug with Grub? If that is the case then its going to as simple as fixing the entries in grub. Not a clue how to do that but check this one out and see if you can draw what they did to fix almost the same problem. 
[http://ubuntuforums.org/showthread.php?t=240614](http://ubuntuforums.org/showthread.php?t=240614)

---

### Post by Bezmotivnik on 2009-01-17
> **sirhceel23 said:**
> Nah, I'm pretty sure its related to the openSUSE install because it booted just fine before I installed it. 
Certainly not here.
> Did you get it the Error 15 fixed or did you do a reinstall???
Ubuntu 8.10 freshly installs the Error 15 each time.  I've reinstalled four times now.

Still won't run.

---

### Post by sirhceel23 on 2009-01-18
Well if it does give you any help I managed to get Ubuntu to boot by repairing the GRUB on the partition I had Ubuntu on. It popped up an error checking system files when loading but then booted up fine after I left that prompt. Hope something helps, but it does appear that its a grub error and not a system problem. So if anyone can figure out what that link'd post tells us above, you'd be a lifesaver!

---

### Post by rahimveron on 2009-01-18
> **Bezmotivnik said:**
> No, there's an installation bug at work:  I've repeatedly installed 8.10 to an older AMD/ASUS computer here with a single hard drive and a CD-ROM, allowing Ubuntu to completely format/use the single drive as it wishes.  No other OSs, the entire drive and computer dedicated to Ubuntu, no dual-boots, no nothing.  Totally plain installation.

I get Grub error 15 every single time I try to boot.
Read below :D

The problem is with Grub entry. Open a terminal and first backup your menu.lst file by enetring ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkup
```
Eeter ```
sudo gedit /boot/grub/menu.lst
```. Give your password.
this is whats there in menu.lst file > title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		435a7b84-d824-4df2-a3ea-92b3f5c91497
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=435a7b84-d824-4df2-a3ea-92b3f5c91497 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

Now add a line to that > root		(hd0,4) to look like this > title		Ubuntu 8.10, kernel 2.6.27-9-generic
[highlight]root		(hd0,4)[/highlight]
uuid		435a7b84-d824-4df2-a3ea-92b3f5c91497
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=435a7b84-d824-4df2-a3ea-92b3f5c91497 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet


Change root (hd0,4) as per your desire. mine is installed in the 5th partition,hence (hd0,4), so if you have installed in the 1st partition yours will be **root (hd0,0)**

After doing it update your grub mbr
sudo grub  #this will give you  the grub prompt
find /boot/grub/stage1 #this will give you an output like hd0,4)
root (hd0,4) #Change this value with the output of previous command
setup (hd0)


I wonder why this bug has not been resolved yet.

@sirhceel23: Follow the above steps, if that doesnt work then use opensuse bootloader and make an Ubuntu boot entry in suse's /boot/grub/menu.lst file
This is how you do it.
Boot with a Live CD
Open a terminal and enter the following 

sudo grub  #this will give you  the grub prompt
find /boot/grub/stage1 #this will give you 2 outputs like (hd0,5) and say hd0,2)
root (hd0,2) #Change this value with with the partition where opensuse is installed(see the oputput)
setup (hd0)

This will restore opensuse bootloader in the mbr. Now just make an entry for Ubuntu in suse's menu.lst. Boot in suse and open /boot/grub/menu.lst file and add an entry down below
> [quote]title		Ubuntu 8.10, kernel 2.6.27-9-generic
[highlight]root		(hd0,5)[/highlight]
kernel		/boot/vmlinuz-2.6.27-9-generic root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
Save the file and when you reboot there would be an entry to boot into your beloved Ubuntu !

---

### Post by sirhceel23 on 2009-01-18
Will try it! THANK YOU!!!

---

### Post by rahimveron on 2009-01-18
^You are welcome :)

---

