---
title: "dual boot"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by nvivek91 on 2011-01-28
hello friends...
I have been using windows seven and ubuntu in my dual boot ...
I need to remove windows seven from the list....
Can anyone help me how to do this

---

### Post by mharrison on 2011-01-28
Taken from:  [http://superuser.com/questions/148418/remove-windows-7-entry-from-grub](http://superuser.com/questions/148418/remove-windows-7-entry-from-grub)


Ubuntu 10.04 LTS uses Grub2, which no longer uses the /boot/grub/menulist.lst file for configuration.

Instead, you should edit the file /etc/default/grub.

do
```
sudo gedit /etc/default/grub
```

If your hard disk still contains a Windows partition, add the line:

```
GRUB_DISABLE_OS_PROBER=true
```
to prevent Windows being added to your grub menu.

To write the change, run

```
sudo update-grub
``` 

which will write a new /boot/grub/grub.cfg file.

You can then run

```
cat /boot/grub/grub.cfg
```
to check that your Windows entry has disappeared.

---

### Post by sikander3786 on 2011-01-28
Welcome to the forums :-)

You said you want to remove Windows from your Grub menu. Does that mean you've already got rid of the Windows partition? If yes, all you need to do is run this command in Applications > Accessories > Terminal:

```
sudo update-grub
```

No need to edit any other configuration files. And turning off os_prober will not be much helpful later if you decide to re-install Windows or anyother Operating System. You'll need to turn it on again.

---

### Post by nvivek91 on 2011-01-28
thank you very much:)
It worked..
One more help how to remove windows files from my hard disk...
Is it correct if i delete all the files??

---

### Post by sikander3786 on 2011-01-28
> **nvivek91 said:**
> thank you very much:)
It worked..
One more help how to remove windows files from my hard disk...
Is it correct if i delete all the files??
Which method did you try? If Windows is still there, it was not the correct method. You should delete your Windows partition and then recreate a partition in that space and mount it under Ubuntu. You can use gparted for that.

---

### Post by nvivek91 on 2011-01-28
What should i do??
My windows is still there:(

---

### Post by mharrison on 2011-01-28
I know some will disagree, but perhaps the easiest thing to do would be to backup your data and simply reinstall Ubuntu and let it use the entire drive.  This will ensure Windows is fully gone, if this is the end result you are wanting to achieve.

---

### Post by sikander3786 on 2011-01-28
> **nvivek91 said:**
> What should i do??
My windows is still there:(
Please post the output of this command.

```
sudo fdisk -l
```

Or a screenshot of gparted.

---

### Post by nvivek91 on 2011-01-28
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        1202     9566208    7  HPFS/NTFS
/dev/sda3            1202       22242   169006080    7  HPFS/NTFS
/dev/sda4           22242       38914   133915649    f  W95 Ext'd (LBA)
/dev/sda5           22242       28721    52041246+   7  HPFS/NTFS
/dev/sda6           29891       38914    72474624    7  HPFS/NTFS
/dev/sda7           28721       29834     8944640   83  Linux
/dev/sda8           29834       29890      449536   82  Linux swap / Solaris

Partition table entries are not in disk order





This is what i get...

---

### Post by sikander3786 on 2011-01-28
So sda2 is your Windows partition. If you have installed gparted, fire it up. Or go to System > Administration > Disk Utility and delete your Windows partition (be careful about the partition you are going to delete and don't delete any of your data partitions). Then create a new partition in the freed up space. As you'll be using it under Ubuntu, I would prefer an ext4 partition.

Then run the command mentioned in post # 3. If you've turned off os_prober, I would recommend to run it back on.

---

### Post by nvivek91 on 2011-01-28
thank you very much:):)
I successfully did it...
One more thing will it be good if i install windows seven in virtual box

---

### Post by sikander3786 on 2011-01-28
> **nvivek91 said:**
> thank you very much:):)
I successfully did it...
One more thing will it be good if i install windows seven in virtual box
You are Welcome :-)

Yes you can run Windows 7 inside the Virtualbox but it wouldn't be much good for gaming. However, you can run nearly all the Windows software. The things that matter are the power of your CPU and the amount of RAM. I would suggest to assign at least 1GB RAM to Windows 7. Check my signature for installation of Windows inside Virtualbox.

---

