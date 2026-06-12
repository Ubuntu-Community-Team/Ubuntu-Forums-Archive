---
title: "deleting windows in dual boot"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by beew on 2011-02-17
Hi,

I have a dual boot system with Windows XP and Ubuntu 10.04. Now I want to get rid of Windows. If I just use gparted to delete the Windows partition (using a live usb) would I render Ubuntu also not bootable? I am worrying that grub may be in the Windows partition so I want to make sure that this is not the case, or if that is the case there is a fix before I go ahead.

Thanks.

---

### Post by sydbat on 2011-02-17
> **beew said:**
> Hi,

I have a dual boot system with Windows XP and Ubuntu 10.04. Now I want to get rid of Windows. If I just use gparted to delete the Windows partition (using a live usb) would I render Ubuntu also not bootable? I am worrying that grub may be in the Windows partition so I want to make sure that this is not the case, or if that is the case there is a fix before I go ahead.

Thanks.I had the same question a few years ago. If I remember correctly, what I did was...

Boot into the LiveCD
Open gparted
Made sure everything was unmounted
Deleted the NTFS partition
Formatted the deleted partition to ext3
Moved / into the newly formatted partition
Deleted the old /
Expanded /home to fill the empty space

In all, it took a few hours, but this box (the one I am writing this on) rebooted just fine. I believe GRUB is in the MBR, an area not part of the first partition.

If there is a problem rebooting, just reinstall GRUB.

---

### Post by marin123 on 2011-02-17
if you installed windows first, then grub is in sda1 and windows partition sda2.
this means you can remove sda2 and still have your ubuntu running. i think that grub is installed in sda1 where mbr is.

i'm not 100% sure, you can google it or wait for someone who is certain this is right.

---

### Post by hansolo4949 on 2011-02-17
Yes, you should delete the windows partition via gparted, then extend your Ubuntu partition (it is the Largest one, the one that is about 3.5 gb is swap). That is all there is to it! And to answer your question about Grub, no, it dies nit reside in the windows partition, so you should have to problem getting rid of windows. Enjoy Ubuntu!

Update: Yes, you should also run sudo update-grub to get rid of the windows entry. I am also sorry about my previous spelling mistakes, I was writing from an Ipad, and the autocorrect was mucking up, not to mention the poor keyboard layout.

---

### Post by sikander3786 on 2011-02-17
> **beew said:**
> Hi,

I have a dual boot system with Windows XP and Ubuntu 10.04. Now I want to get rid of Windows. If I just use gparted to delete the Windows partition (using a live usb) would I render Ubuntu also not bootable? I am worrying that grub may be in the Windows partition so I want to make sure that this is not the case, or if that is the case there is a fix before I go ahead.

Thanks.
Yes the easiest and probably the safest way of getting rid of Windows is to delete the Windows partition via your favorite partition editor and then run this command to get rid of Grub entry for Windows.

```
sudo update-grub
```

If you are using Grub for a dual-boot (most probably with a default install unless you configured some Windows based bootloader like EasyBCD), removing Windows shouldn't render your Ubuntu un-bootable as Grub is installed to the MBR of the HDD and not the partition.

And resizing system partitions, either Windows or Ubuntu is not recommended in my opinion. Instead in the freed up space, just create a new partition (ext3, ext4 or even NTFS) and use it for data storage.

---

### Post by beew on 2011-02-17
> **marin123 said:**
> if you installed windows first, then grub is in sda1 and windows partition sda2.
this means you can remove sda2 and still have your ubuntu running. i think that grub is installed in sda1 where mbr is.

i'm not 100% sure, you can google it or wait for someone who is certain this is right.
  Windows was installed first, it is in sda1 and ubuntu sda2 though.

---

### Post by beew on 2011-02-17
> **sikander3786 said:**
> Yes the easiest and probably the safest way of getting rid of Windows is to delete the Windows partition via your favorite partition editor and then run this command to get rid of Grub entry for Windows.

```
sudo update-grub
```If you are using Grub for a dual-boot (most probably with a default install unless you configured some Windows based bootloader like EasyBCD), removing Windows shouldn't render your Ubuntu un-bootable as Grub is installed to the MBR of the HDD and not the partition.

And resizing system partitions, either Windows or Ubuntu is not recommended in my opinion. Instead in the freed up space, just create a new partition (ext3, ext4 or even NTFS) and use it for data storage.


Thanks. I will try that out. I think resizing Ubuntu's /home partition is ok. Done it many times. I have resized the / partition too, but only expanding it to the right. I tried moving the / partition to the right once by shrinking on  the left and expanding on the right. In the end  it took forever to boot and got tons of input/output error. Reformatting and reinstalling didn't help. Seems like hard disk just died. I don't know if shifting the / partition  was to blame or if that is just  a coincidence

---

### Post by marin123 on 2011-02-17
> **beew said:**
> Windows was installed first, it is in sda1 and ubuntu sda2 though.

by default, windows creates 2 partitions - MBR and ntfs for windows. just make sure you keep mbr partition (size around 100 MB) safe.

---

### Post by beew on 2011-02-17
> **hansolo4949 said:**
> Yes, you should delete the windows partition via boarded, then extend your Ubuntu partition (it is the ,attest one). That is all there is to it! And to answer your question about Grub, no, it dies nit reside in the windows partition, so you should have to problem getting rid of windows. Enjoy Ubuntu!

Thanks, that is reassuring. I am not sure if I would want to expand the / partition to the right though, see above. I probably would dual boot with another version of Linux.

---

### Post by beew on 2011-02-17
> **marin123 said:**
> by default, windows creates 2 partitions - MBR and ntfs for windows. just make sure you keep mbr partition (size around 100 MB) safe.


How? Where is it? Others seem to be saying just go ahead and delete the Windows partition. 

Thanks.

---

### Post by sikander3786 on 2011-02-17
> **beew said:**
> How? Where is it? Others seem to be saying just go ahead and delete the Windows partition. 

Thanks.
It is Windows 7 and Vista which create another System Partition 100 MB in size. With XP it is just one partition. If you are not sure, post an output of gparted or this command from Terminal.

```
sudo fdisk -lu
```

---

### Post by beew on 2011-02-17
> **sikander3786 said:**
> It is Windows 7 and Vista which create another System Partition 100 MB in size. With XP it is just one partition. If you are not sure, post an output of gparted or this command from Terminal.

```
sudo fdisk -lu
```


It is XP. I am not at home right now so can't post the output of the command, but I am pretty sure there isn't a 100MB partition. I haven't used Vista or Windows7.

---

### Post by pekon on 2011-02-17
Just for sharing.. 
1) incase ever you mess up ur MBR.. you can still recover it using a very nice utility called "testdisk" .. 
But for that "testdisk" should be installed on ur system. And you should not hv rebooted ur system, otherwise u end--up in "chicken or egg" deadlock :)

2) for deleting Windows partition.. follow "[B]sikander3786" method
[/B]

---

