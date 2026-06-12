---
title: "Installed to hda; boot attempt from sda (bad)"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by AndyInNYC on 2009-01-19
My system has the following:

1 IDE HD which shows as hda
1 IDE CD ROM
1 3 TB array on a 3ware 9500S-8 which shows as sda

When I install Ubuntu, I choose hda as the target; the RAID array is for data only; presently unformatted.

Great install.

When I reboot, the 'first' drive it attempts to boot to is the RAID array.

When I reboot the CD and direct it to boot from the 'first hard disk' it boots perfectly.

I have formatted the RAID array; I still don't want it as my boot drive.

I have changed all the options in my BIOS for selecting boot order - no change or success.

What shall I do so that I can at least boot without having the Live CD in the drive?

thanks.


Andrew

---

### Post by x22 on 2009-01-19
you may find when booting normally, that what was called "hda" by the
install CD, is called "sda" by the new kernel--with the RAID "sdb"

if using grub bootloader: go into /boot/grub with a text editor, and
change "hda1" to "sda1"--or 2...or whatever...

---

### Post by caljohnsmith on 2009-01-19
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by egalvan on 2009-01-19
> When I reboot, the 'first' drive it attempts to boot to is the RAID array.

Does this mean that the motherboard is attempting to boot the wrong drive?

Or that GRUB is attempting to boot the wrong drive?

caljohnsmith will sort out the GRUB problem in jig-time, :)

As to the mobo being the culprit, be aware that some mobo BIOS's have separate (and confusing) "boot order" and "boot group" screens.

And some bios's have them in totally different parts of the set-up.

---

### Post by AndyInNYC on 2009-01-19
This motherboard is an ASUS M2NPV-VM.  I have installed the most recent BIOS.  I updated the BIOS after having this problem.

I have no idea what a boot group is.  I can set the boot order between CD, removable, HD.

When I install off the CD is works fine/installs to hda (the only IDE drive).

I actually got the machine to boot back into ubuntu w/out the CD.  I then ran the updates and bang, I'm back to no boot.

I'm reinstalling and checking to see what grub looks like; then after the update, I'll see if anything has changed.

This has turned into an 3 day weekend nightmare.

Any other thoughts?

Andrew

---

### Post by AndyInNYC on 2009-01-19
Found where the HD boot order was stored!  I've never looked there before.

Unfortunately I've bashed the install a bit and need to do a reinstall from scratch anyway.

Thanks.

Andrew

---

### Post by mcduck on 2009-01-19
The current kernel doesn't use "hd*" names for anything any more. All hard drives (including IDE drives!) are managed by SATA/SCSI driver, and thus get "sd*" as their names.

Also you should notice that the naming used by Grub is completely different from what Linux itself uses. ("hd0,0" as opposed to the "sda1" to point to the first partition of first disk)

---

### Post by AndyInNYC on 2009-01-20
Sure, that makes sense.  Why make anything easy or consistent?

Now I need to figure out what my issues are with the array - it degrades the moment I format the drive to ext3.  Gahh!


> **mcduck said:**
> The current kernel doesn't use "hd*" names for anything any more. All hard drives (including IDE drives!) are managed by SATA/SCSI driver, and thus get "sd*" as their names.

Also you should notice that the naming used by Grub is completely different from what Linux itself uses. ("hd0,0" as opposed to the "sda1" to point to the first partition of first disk)

---

### Post by mcduck on 2009-01-20
I'd say using the same naming for all hard disks, regardless of their type, is consistent. ;)

The reason for the change was that the SATA/SCSI driver handles IDE drives better than the actual IDE driver ever did.

---

