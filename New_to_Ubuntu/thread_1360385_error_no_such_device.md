---
title: "error no such device"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by sweepdaleg on 2009-12-20
I'm a newbie wanting to try out ubuntu 9.10. I did a clean install over winxp on my old desktop. Now my pc will not boot. I have a 40gb hdd and I noticed that ubuntu was reading it as 70gb. I finished the install and rebooted. I see the grub loading and a message saying error no such device. 

My pc will then load GNU GRUB version 1.97 with these 4 options to choose from:

Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

When I select the first two options I get this message: 

error: no such device: 31a60106-1534-44c3-a45e-820556198263

No problems when I select the third option as the memory test just starts. 

When I select the last memory test option I get a black screen with on in the middle of it. 

Please help, I tried looking at other posts with the same issue but could not find one. 

Thanks.

---

### Post by 73ckn797 on 2009-12-20
Did you verify the "iso" file you downloaded for correct "md5sum"? Did you run the LiveCD disk check to verify the LiveCD is a good burn? If so, how fast did you burn the CD, what was the burn speed? Slow is best.

---

### Post by sweepdaleg on 2009-12-20
How do I check if I have the correct md5sum? Also how do I run LiveCD to check the if it is a good burn? I'm really new to this and would appreciate more assistance. Also, I downloaded the iso from the ubuntu website directly if that makes a difference. I know for sure I didn't burn the iso image on the slowest setting.

---

### Post by 73ckn797 on 2009-12-20
A quick check will be to boot the computer using the LiveCD. There is a menu choice to check the disk for errors. Select that and see what the results are. If it checks OK, that is eliminated. If not, then follow info below.

Look here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and here: [http://releases.ubuntu.com/karmic/MD5SUMS](http://releases.ubuntu.com/karmic/MD5SUMS)

In a terminal enter:
```
md5sum
``` and the path to where the iso file was downloaded to. The instruction in the first link will guide you.

---

### Post by sweepdaleg on 2009-12-20
Booted the pc with the LiveCD and ran the check disc option. The check came back okay. I checked the md5sum on my windows pc. That checked out okay.

---

### Post by Chesamo on 2009-12-20
Boot into the LiveCD, then in the Terminal type```
sudo update-grub
```Let us know if this fixes your problem, or if the problem persists.

---

### Post by 73ckn797 on 2009-12-20
Did you have Ubuntu completely repartition and reformat the drive or did you follow the, possibly, recommendation to install on any free space?

If you boot from the CD then go to Applications/Accessories/Terminal and enter the follow commands:

```
 sudo fdisk -l
``` (That is a lower case L.)

Copy the results and post in reply.

Also enter:
```
sudo blkid
``` and copy the results in reply.

This info may be a help.

---

### Post by sweepdaleg on 2009-12-20
I followed the ubuntu recommendations.

---

### Post by 73ckn797 on 2009-12-20
> **Chesamo said:**
> Boot into the LiveCD, then in the Terminal type```
sudo update-grub
```Let us know if this fixes your problem, or if the problem persists.

This will possibly correct the problem too.

---

### Post by sweepdaleg on 2009-12-21
Chesamo: When I entered sudo update-grub I got this message:

grub-probe: error: cannot find a device for /. 

After entring sudo fdisk -l:

Disk /dev/sda: 80.1 GB, 80060424192
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

sudo blkid:

/dev/loop0: TYPE ="squashfs"
/dev/sda1: UUID="851fe97c-d3d5-4a73-8985-424238599c72" TYPE="ext4"
/dev/sda5: UUID="3ceec9a5-43a3-40fb-8d2c-924423785100" TYPE="swap"

---

### Post by 73ckn797 on 2009-12-21
> **sweepdaleg said:**
> Chesamo: When I entered sudo update-grub I got this message:

grub-probe: error: cannot find a device for /. 

After entring sudo fdisk -l:

Disk /dev/sda: 80.1 GB, 80060424192
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

sudo blkid:

/dev/loop0: TYPE ="squashfs"
/dev/sda1: UUID="851fe97c-d3d5-4a73-8985-424238599c72" TYPE="ext4"
/dev/sda5: UUID="3ceec9a5-43a3-40fb-8d2c-924423785100" TYPE="swap"

In a terminal enter this:
```
gksudo gedit /boot/grub/device.map
```See if you have this listing:
```
 (hd0)     /dev/sda
```If not then edit the file, save and then run in terminal:
```
sudo update-grub2
``` then reboot.

---

### Post by 73ckn797 on 2009-12-21
> **sweepdaleg said:**
> I have a 40gb hdd and I noticed that ubuntu was reading it as 70gb. I finished the install and rebooted.

According to your info, you have a 80GiB drive. I also have a 80GiB drive and our info nearly matches.

Your drive:
```
Disk /dev/sda: 80.1 GB, 80060424192
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001
```My drive:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf832f832
```

---

### Post by sweepdaleg on 2009-12-21
> In a terminal enter this:
Code:
gksudo gedit /boot/grub/device.map
See if you have this listing:
Code:
 (hd0)     /dev/sda
If not then edit the file, save and then run in terminal:
Code:
sudo update-grub2
then reboot.

I do have the (hd0)     /dev/sda file.

---

### Post by CaptainMark on 2009-12-21
what is the output from ```
sudo cat /boot/grub/menu.lst/
```

---

### Post by sweepdaleg on 2009-12-21
> **CaptainMark said:**
> what is the output from ```
sudo cat /boot/grub/menu.lst/
```

After entering in that command my result was, "No such file or directory"

I tried the last bit as a "1"-one and "l"-L. Both came back the same.

---

### Post by CaptainMark on 2009-12-21
yeah sorry, me not thinking. you need to have the system loaded for this command, if you load a live session from cd can you mount your main partition and run ```
sudo cat /(mount point)/boot/grub/menu.lst
``` replace (mount point) with wherever your main drive is mounted.  If your main drive pops up as an icon on the desktop just open it and navigate to /boot/grub/menu.lst and paste its contents here

---

### Post by adam814 on 2009-12-21
The grub error is this:

> error: no such device: 31a60106-1534-44c3-a45e-820556198263The number after the colon is a filesystem uuid.  GRUB cannot find a filesystem matching this UUID.  The output from blkid is:

> sudo blkid:

/dev/loop0: TYPE ="squashfs"
/dev/sda1: UUID="851fe97c-d3d5-4a73-8985-424238599c72" TYPE="ext4"
/dev/sda5: UUID="3ceec9a5-43a3-40fb-8d2c-924423785100" TYPE="swap"None of the filesystems on your system match the UUID from the error message, explaining the mix-up.

Try editing the boot parameters by pressing the "e" key at the GRUB prompt.  Find the part after "linux /boot/vmlinuz-2.6.31-14-generic" where it says "root=UUID=31a60106-1534-44c3-a45e-820556198263".  Change what's after the equal sign so it reads "root=/dev/sda1".  If it boots open a terminal and type "sudo grub-mkconfig && sudo update-grub".  If it doesn't boot post the new error message.

It's normal for /boot/grub/menu.lst not to be found if you're using GRUB2 which 9.10 does by default for new installs since GRUB2 uses /boot/grub/grub.cfg for a config file.

---

### Post by sweepdaleg on 2009-12-22
> > **adam814 said:**
> The grub error is this:

The number after the colon is a filesystem uuid.  GRUB cannot find a filesystem matching this UUID.  The output from blkid is:

None of the filesystems on your system match the UUID from the error message, explaining the mix-up.

Try editing the boot parameters by pressing the "e" key at the GRUB prompt.  Find the part after "linux /boot/vmlinuz-2.6.31-14-generic" where it says "root=UUID=31a60106-1534-44c3-a45e-820556198263".  Change what's after the equal sign so it reads "root=/dev/sda1".  If it boots open a terminal and type "sudo grub-mkconfig && sudo update-grub".  If it doesn't boot post the new error message.

It's normal for /boot/grub/menu.lst not to be found if you're using GRUB2 which 9.10 does by default for new installs since GRUB2 uses /boot/grub/grub.cfg for a config file.

Sorry for replying so late guys. It's been a hectic few days. I typed in "root=/dev/sda1"

I received this error message:

error: no such device: 851fe97c-d3d5-4a73-8985.

---

### Post by sweepdaleg on 2009-12-22
> **CaptainMark said:**
> yeah sorry, me not thinking. you need to have the system loaded for this command, if you load a live session from cd can you mount your main partition and run ```
sudo cat /(mount point)/boot/grub/menu.lst
``` replace (mount point) with wherever your main drive is mounted.  If your main drive pops up as an icon on the desktop just open it and navigate to /boot/grub/menu.lst and paste its contents here

I'm sorry for being such a newbie. Am I right to assume that my mount point is either sda1 or sda5? If so, both times I entered that into the terminal I received the message: "No such files or directory."

---

### Post by 73ckn797 on 2009-12-23
Enter the uuid from the "blkid" result:
```
 /dev/sda1: UUID="851fe97c-d3d5-4a73-8985-424238599c72" TYPE="ext4"
```

From the boot screen press "e" and change the uuid and see what happens.

---

### Post by adam814 on 2009-12-23
Your root partition has to be /dev/sda1 since /dev/sda5 is marked as a swap partition.  It *should* boot with the root option set to either root=/dev/sda1 or root=UUID=851fe97c-d3d5-4a73-8985-424238599c72

You could also try finding the files from the GRUB command prompt.  If you press 'c' at the menu you can type ls to see the devices GRUB finds.  Then you can try for example>  ls (hd0,0)/When you find the root partition you'll see your Ubuntu directory structure with that.

Above the line for the kernel in the boot parameters there's probably a line like this:
> root (hd0,0)Make sure this line matches the one you found earlier (i.e. if "ls (hd1,0)/" shows your files it should be "root (hd1,0)" instead).

---

