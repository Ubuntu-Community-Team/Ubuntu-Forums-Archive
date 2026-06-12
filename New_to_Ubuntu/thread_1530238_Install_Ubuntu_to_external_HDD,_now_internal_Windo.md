---
title: "Install Ubuntu to external HDD, now internal Windows won't boot"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by legendeveryone on 2010-07-13
So I wanted to install Ubuntu to an external HDD so I could dual boot between that and Windows XP installed on the internal drive. I removed the internal drive when doing the install, and at the last step I made sure to install the MBR to the external drive.  That much went well and I could boot and run Ubuntu from the drive.
 
I then tried installing Ubuntu to a larger external drive (using the Live CD again), but it was having errors so I gave up on that. 
 
Now I can't boot to the original (good) external drive, nor Windows on the internal.
 
I don't have admin rights to Windows (hence the initial need for Ubuntu) so any troubleshooting / fixing I need to do will have to be through the Live CD. 
 
Any suggestions on where I can begin troubleshooting? It's imperative that I keep the Windows drive intact, but the external I have no problem wiping and reinstalling.

---

### Post by mrbiggbrain on 2010-07-13
Can you answer a few quick questions for me so i can help you solve your issue?

When you say the pc will not boot up, what errors are you getting? Is it trying to boot windows or trying to boot ubuntu?

What version of windows are you using?

Did you make the proper changes to the boot loader for the external drive (Using the uuid of the drive instead of the sda address)

Did you try unplugging the external? Any change?

Did you try unplugging the internal again?

Did you ensure the cables for the internal are back where they are suppose to be.

---

### Post by legendeveryone on 2010-07-13
> When you say the pc will not boot up, what errors are you getting? Is it trying to boot windows or trying to boot ubuntu?
I believe it is looking for a connection to the USB external drive, so I would guess Ubuntu. Here are the messages I get when I boot with the USB unplugged (or plugged in the wrong port):
```
Intel Boot Agent GE v 1.3.36
Intel Boot Agent PXE Base Code
Initializing and est. link
Media test failure, check cable
Exiting Intel boot agent
```
Followed by:
```
Cannot boot from any device
Current boot order and device status
 1: ATAPI CD0: Model HL-DT-ST DVDRAM GU10N-(S2  -> No valid operating system
 2: ATA HDD0: Model WDC WD2500BEVS-08VAT2-(S1   -> No valid operating system
  .
  .
  .
```
 
However, when I changed the USB port, it started loading Ubuntu, albeit with errors:
```
grub-editenv: error: cannot open the file /boot/grub/grubenv
EXT4-fs error (device sdb1): ext4_iget: bogus i_mode (0) for inode = ###
```
It kept spitting out those EXT4-fs errors so I powered down. I can try that again fully when I'm at home.
 
> What version of windows are you using?
Windows XP, SP2 I believe. 
 
> Did you make the proper changes to the boot loader for the external drive (Using the uuid of the drive instead of the sda address)
I highly doubt it. Most places I read about doing this only mentioned that during the last step of the install you have to tell it to install the MBR to the external drive, which I did. During the install I had the internal drive unplugged to avoid anything being written there.
 
> Did you try unplugging the external? Any change?
I did, and still nothing. I get the errors above when the USB is not present (or in the wrong port).
 
> Did you try unplugging the internal again?
I did not try booting with the internal unplugged.
 
> Did you ensure the cables for the internal are back where they are suppose to be.
It's a laptop, so I just slid it in as far as it would go. The BIOS finds the drive, but says that there is no valid OS.
 
I'm beginning to wonder at this point if when I tried the 2nd install to a different external drive, if I had accidentally left the internal in and started installing there. I'm fairly certain I did not, but I guess it's a possibility.

---

### Post by YesWeCan on 2010-07-13
Physically disconnecting the XP disk while doing Ubuntu installs is a very, very good idea.

I'd remove all disks except the XP and try to boot it. XP gets pissy if it is not told by the bios that it is the first boot device. If it won't boot you'll need your XP CD to repair the bootloader. If it does boot, then shut down and remove the disk and put it somewhere safe while you get the Ubuntu USB disk booter working again. Once you can boot Ubuntu USB ok plug the XP disk back in. Tell the bios to boot off the USB disk and when in Ubuntu do a update-grub command to add XP to the grub menu. Then it oughta work, assuming you are using grub2. Make sure you use Grub2 (standard in 10.04).

---

### Post by legendeveryone on 2010-07-13
Thanks for the advice, I'll give that a shot when I get home today. 
 
> **YesWeCan said:**
> If it won't boot you'll need your XP CD to repair the bootloader. 
Let's say I don't have an XP CD to boot from, is there a way to download and burn one myself? Or can I fix it with the Live CD?

---

### Post by mlentink on 2010-07-13
> **legendeveryone said:**
>  I removed the internal drive when doing the install, and at the last step I made sure to install the MBR to the external drive. 
Could you please clarify this? How exactly did you install the MBR to this external drive?
> **YesWeCan said:**
> Physically disconnecting the XP disk while doing Ubuntu installs is a very, very good idea.
I respectfully disagree. In my opinion, the Ubuntu install script is actually quite savvy, well thought out. Just install to the medium desired, but make sure that before making definitive changes to hit the 'Advanced' button and install the GRUB-bootloader to the external device. The installer won't even touch your current  (internal) XP installation. and you'll be able to choose the external drive to boot from in the bios . Simple.
I've done this dozens of time without any problem.

---

### Post by legendeveryone on 2010-07-13
> **mlentink said:**
> Could you please clarify this? How exactly did you install the MBR to this external drive?
I meant the boot loader. I follow the instructions in the attached image, which I found from [http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/)
 
I know that my Advanced setup had only one option for the dropdown: /dev/sda, which is what I chose. 
 
As I mentioned before, I really didn't want to make *any* changes to the XP drive, so I removed it while installing.

---

### Post by Tech2077 on 2010-07-13
That means the bios is not detecting a operating system, if this was a problem with grub it would have had a rescue promt, and if it would have been a problem with windows, a windows thing would have come up and complained. It seems that this mean it is not properly detecting the media. Can you boot from a live cd with the drive attached and check the contents of the drives. Also run this and paste the result, if windows isn't the first partition, possible bios may complain: 'fdisk -l' possible as sudo if it doesn't work. This will show all the drives and partions.

---

### Post by YesWeCan on 2010-07-13
[QUOTE=mlentink]
I've done this dozens of time without any problem.[/QUOTE]
I agree with your sentiment. I was not trying to dis Ubuntu; it ought to work fine. However, the possibility of user error or using the wrong grub or whatever causes me to always recommend disconnecting the Windows drive. Belt and braces. The only cost is having to update-grub afterwards and that seems a small price to ensure a mistake doesn't affect Windows. Windows is a pain to fix in my experience.

---

### Post by YesWeCan on 2010-07-13
[QUOTE=legendeveryone]
Let's say I don't have an XP CD to boot from, is there a way to download and burn one myself? Or can I fix it with the Live CD?[/QUOTE]
I don't think you will be able to fix the windows bootloader using the Ubuntu live CD. I really don't know what your options are without having a Windows OS CD. Perhaps someone else has more knowledge.

---

### Post by legendeveryone on 2010-07-13
> **YesWeCan said:**
> I don't think you will be able to fix the windows bootloader using the Ubuntu live CD. I really don't know what your options are without having a Windows OS CD. Perhaps someone else has more knowledge.
After some research on using the XP CD recovery console, I'm beginning to realize what a lovely mess I've gotten myself into. Since I don't know/have the Admin password to Windows, I don't think I'll be able to run any commands from the recovery console. 
 
I'll see if Windows can boot after moving it to the first boot order, and if not I at least need to see if I overwrote the Windows drive or not.

---

### Post by wilee-nilee on 2010-07-13
Here is a link to a XP legit download, for repairs if needed. 
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

The best thing you could do first though is to from a live cd run the bootscript in my signature, then post it in code tags it will tell us or you what is in the mbr of the internal and external amongst other pertinent information.

Since we know you have no admin, I wonder if there is something to do with removing the HD which is at the root of this part...you know like a extra security encryption.

---

### Post by mlentink on 2010-07-13
> **legendeveryone said:**
> 
I'll see if Windows can boot after moving it to the first boot order, and if not I at least need to see if I overwrote the Windows drive or not.


Uhh... I assume you hadn't tried this yet? That would indeed be my first action. Start up your computer until you get to the BIOS prompt (Mine says F9 to change boot order, F10 to change BIOS options, but this differs from brand to brand). Change the boot order so that it lists you windows drive first. Let 'r rip. If it doesn't work you've just lost the World Cup Finals, but maybe all is not lost.

---

### Post by mrtomservo on 2010-07-13
Maybe i'm misunderstanding the problem, but here's what i'd do.  You WILL need that admin password for XP.  No way around it if you want to repair it.  I've come across this problem many times repairing clients computers.  What you'll need is [Ophcrack]("http://ophcrack.sourceforge.net/").  Boot off the liveCD, get the password.  Get into a recovery console (you can find iso's to burn online), using your newly found password, run fixboot and fixmbr.  That should reinstall the bootloader for XP.  Hope that helps.

---

### Post by Zorgoth on 2010-07-13
I did something similar once and I fixed it with a utility called mbrfix after booting Windows with Auto Super Grub Disk, no repair CD involved.  That was Windows 7 though.

---

### Post by legendeveryone on 2010-07-14
Here's what I've had the chance to try:
 
Moving internal XP drive to first boot order gave me the same error as before (No valid OS).
 
Booting from the external Ubuntu didn't get me much farther than the EXT4-fs errors. It prompted me at while booting to enter the username and password I set up, but nothing worked, so I couldn't boot that way.
 
Booting from the Live CD I was able to get this from fdisk -l:
 
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30404 cylinders
Units = cylinders of 16065 * 512 bytes = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimal/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30bda424
 
Device Boot    Start    End        Blocks       Id    System
/dev/sda1      1        30401      244196001    83    Linux
 
Disk /dev/sdb: 100.0 GB, 100030243328 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 bytes = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimal/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb000a0d
 
Disk /dev/sdb doesn't contain a valid partition table
```
 
I haven't been able to try the bootscript since I can't get online from here. 
 
However, what I'm seeing is that the internal drive (/dev/sda) has been renamed to "Ubuntu-NTFS," which is what I was calling my second external drive (or so I thought), which means I must have installed Ubuntu there and overwritten all of Windows anyway. The only folder I see in there is Lost+Found, which it claims I do not have permissions to. Except that the file browser shows 217GB of free space on a 250GB drive, which means that perhaps Windows is somewhere in that 30GB leftover, hidden from Ubuntu?
 
Is there a way for me to find out if Windows is even still there? I'm thinking my best bet with that is an Ophcrack & XP CD combination.
 
I would still like to keep the external drive intact, since I backed up all my important files (mainly music and photos) when I had access to both internal and external. Is that as easy as creating a partitioning table on that drive? If so, is there anything in particular I should be aware of when doing that?

---

### Post by mrtomservo on 2010-07-17
Sorry it took me so long to reply.  If something was on your /dev/sdbx drive, i'd say it's gone now unfortunately.  It can't find a valid partition table, meaning the Ubuntu installer was probably in the middle of writing to it when it was interrupted.  I'm no expert at data recovery or anything, but there may be a small chance you can recover your data, but i'm not personally sure how.  Glad you saved your music/data first at least.

---

