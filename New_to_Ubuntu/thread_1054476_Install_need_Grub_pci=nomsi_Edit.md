---
title: "Install need Grub pci=nomsi Edit"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Joerice50 on 2009-01-29
Installed ubuntu8.10 from CD using pci=nomsi I now need to edit Grub's menu list to include pci=noms1 via a live CD session but find I have no permissions to edit this file or change permissions.

In simple terms how do i edit the menu.lst

If I use sudo gedit /boot/grub/menu.lst I get:

** (gedit:8335): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.OSOKOU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory
ubuntu@ubuntu:~$ sudo gedit /boot/grub/menu.lst

if I open the file with the text editor in live CD I have no permission to change the file.

Please advise 

Thanks 

Joe Rice

---

### Post by caljohnsmith on 2009-01-29
How about first doing:
```
sudo fdisk -lu
```
Find which is your Ubuntu partition, say sda1 for example, and then do:
```
sudo mount /dev/[COLOR="Blue"]sda1[/COLOR] /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
Let me know if that works OK or if you still run into problems.

---

### Post by Joerice50 on 2009-01-30
Still a few queeries:

Following your instructions I get the following:
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26932692

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1465127999   732563968+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0ce3888

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   154079414    77039676   83  Linux
/dev/sdb2       154079415   160071659     2996122+   5  Extended
/dev/sdb5       154079478   160071659     2996091   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sdb .mnt
mount: mount point .mnt does not exist
ubuntu@ubuntu:~$ sudo mount .dev/sdb1  /mnt
mount: special device .dev/sdb1 does not exist
ubuntu@ubuntu:~$ gksudo gedit /mnt/boot/grub/menu.lst

However the edit pane has no code in it yet displays menu.lsy as it file neam. 

If I click on the file open icon I get :
Error stating file '/mnt/boot/grub': No such file or directory

so I seem to be off the correct directory somehow 
so I used the edit commands to open grub and included the pci=nomsi see details below and saved it:

itle		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		93eb10b9-97c9-46f4-a6b5-cb16a6626692
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=93eb10b9-97c9-46f4-a6b5-cb16a6626692 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		93eb10b9-97c9-46f4-a6b5-cb16a6626692
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=93eb10b9-97c9-46f4-a6b5-cb16a6626692 ro  single pci=nomsi
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		93eb10b9-97c9-46f4-a6b5-cb16a6626692
kernel		/boot/memtest86+.bin pci=nomsi 
quiet

I will reboot now to see if this works and let you know

Joe Rice

---

### Post by rajeev1204 on 2009-01-30
> **Joerice50 said:**
> Installed ubuntu8.10 from CD using pci=nomsi I now need to edit Grub's menu list to include pci=noms1 via a live CD session but find I have no permissions to edit this file or change permissions.

In simple terms how do i edit the menu.lst

If I use sudo gedit /boot/grub/menu.lst I get:

** (gedit:8335): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.OSOKOU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory
ubuntu@ubuntu:~$ sudo gedit /boot/grub/menu.lst

if I open the file with the text editor in live CD I have no permission to change the file.

Please advise 

Thanks 

Joe Rice


If you have already installed ibex, are you sure you need to add pci=nomsi in grub? Isnt your system booting?


I too had to add the pci=nomsi option when booting with live cd as the installer had problems recognising between cd rom and hard disk but post installation , there is no need and it booted correctly.

---

### Post by Joerice50 on 2009-01-30
Hard Drive Boot Error

The pci=nomsi modification has not resolved my harddrive boot problem. The system stops with a busybo at the initramfs prompt.

The proceeding messages are as follows:
gave up waiting for root device
boot args(cat/proc/cmdline)
check root delay
Stuck in boot: Missing modules (cat /proc/modules; ls /dev) in busybox

I note this problem is being experienced by a large number of 8.10 64 bit installers see thread Stuck in boot: Missing modules (cat /proc/modules; ls /dev) in busybox 

So I guess I will need to wait with the others until someone can sort the problem

Cheers

Joe Rice

---

### Post by rajeev1204 on 2009-01-30
> **Joerice50 said:**
> Hard Drive Boot Error

The pci=nomsi modification has not resolved my harddrive boot problem. The system stops with a busybo at the initramfs prompt.

The proceeding messages are as follows:
gave up waiting for root device
boot args(cat/proc/cmdline)
check root delay
Stuck in boot: Missing modules (cat /proc/modules; ls /dev) in busybox

I note this problem is being experienced by a large number of 8.10 64 bit installers see thread Stuck in boot: Missing modules (cat /proc/modules; ls /dev) in busybox 

So I guess I will need to wait with the others until someone can sort the problem

Cheers

Joe Rice


Is this from live cd ?

Or you have already installed and booting from hard disk?

---

### Post by Joerice50 on 2009-01-30
I was trying to boot from hard drive. 

However, I have now found and implemented the fix

see: [http://ubuntuforums.org/showpost.php...&postcount=322](http://ubuntuforums.org/showpost.php...&postcount=322)

Thanks everyone for your help you will see from my posts to this beginners section that it has been a problematical journey to get ubuntu working on this chip set, but we got there. 

I will now start using Ubuntu now!

Cheers

Joe Rice

---

### Post by gmanrodt on 2009-02-25
The "fix" link you posted above does not work, and I am having this same issue. Can you repost the link?

Thanks,

---

