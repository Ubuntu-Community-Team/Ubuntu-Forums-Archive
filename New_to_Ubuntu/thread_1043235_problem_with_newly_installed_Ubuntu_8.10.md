---
title: "problem with newly installed Ubuntu 8.10"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by medic on 2009-01-18
i just installed Ubuntu 8.10 with windows vista..
after the installation was complete the DVD came out and i just restarted..
But in GRUB there were only three entries one for **Ubuntu memtest **and **other two** were for **windows vista**..
I am unable to start Ubuntu.. is there anyway out to add another entry for Ubuntu??

---

### Post by Michael.Godawski on 2009-01-18
hi,

in which order did you install ubuntu and vista? What was first on the drive?

---

### Post by medic on 2009-01-18
i installed Ubuntu after windows Vista..
VIsta came pre installed on the system..
again i reinstalled but the problem is still there..

---

### Post by medic on 2009-01-18
::bump::

---

### Post by fuser312 on 2009-01-18
> reinstall it
it will take around 30-40 minutes and there is no data in ubuntu to worry about, just reinstall it.

and remeber to read one or two guide about installing ubuntu, if you are not sure about installation (just google it). and are you sure during installation no error message was flashed.

---

### Post by empty_spaces on 2009-01-18
How did you do the partitioning of you hard drive to accomodate ubuntu? 
Also, it might be helpful if you could post the contents of the /boot/grub/menu.lst file

---

### Post by medic on 2009-01-18
> **empty_spaces said:**
> How did you do the partitioning of you hard drive to accomodate ubuntu? 
Also, it might be helpful if you could post the contents of the /boot/grub/menu.lst file

how can i do that?
i cant boot into Ubuntu..
is there anyother way?

---

### Post by empty_spaces on 2009-01-18
You could run the live cd and then browse to /boot/grub/menu.lst on the partition where ubuntu is installed and grab a copy of menu.lst.

If your problem is grub, You could also try reinstalling grub using this link - [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Also, how did you do the partitioning?

---

### Post by Indian_Guy101 on 2009-01-18
ok yes we need to know how you did the paartitioning

---

### Post by Sef on 2009-01-18
Let's check your partitions first:

Using the LIve CD, go into Terminal (Applications > Accessories > Terminal)

and copy (or type) this code:

```
sudo fdisk -l
``` Small L

---

### Post by medic on 2009-01-19
> **Sef said:**
> Let's check your partitions first:

Using the LIve CD, go into Terminal (Applications > Accessories > Terminal)

and copy (or type) this code:

```
sudo fdisk -l
``` Small L


```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab9e2973

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1298    10424320   27  Unknown
/dev/sda2   *        1298       19121   143159296    7  HPFS/NTFS
/dev/sda3           19121       24766    45342720    7  HPFS/NTFS
/dev/sda4           24766       30401    45267649    f  W95 Ext'd (LBA)
/dev/sda5           24766       27590    22687744    7  HPFS/NTFS
/dev/sda6           27591       30143    20506941   83  Linux
/dev/sda7           30144       30401     2072353+  82  Linux swap / Solaris

```

---

### Post by empty_spaces on 2009-01-19
fyi, check this other thread, might have something for you.
[http://ubuntuforums.org/showthread.php?t=1044090](http://ubuntuforums.org/showthread.php?t=1044090)

---

### Post by caljohnsmith on 2009-01-19
Medic, in order to get a clearer picture of your setup, how about booting your Live CD again, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by medic on 2009-01-19
just got it solved..
the DVD came with the magazine and it was corrupted thats why i was having this problem..
Downloaded it again and now i am a happy user.. :)

One thing i want to know is that how can i search for wi-fi networks available??

---

