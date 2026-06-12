---
title: "Grub Error 13: Unsupported or invalid executable file"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by sepz on 2009-02-26
Good day gents,

Hopefully a quick issue, 

I installed ubuntu 8.10 x64 last night onto what is now dev/sda,
and installed Grub to (iirc) HDC aka my windows hdd (which BIOS boots as first hdd), unfortunately I received a GRUB error "Grub Error 13: Unsupported or invalid executable file".
So I played around a little and towards the end of the post you will see the old and new grub file;

I have read other posts regarding this issue and tried a couple of things
but from what I can tell everything should work.. (spacing is correct, correct hd association)
Would one of you be so kind as to take a look at this for me please?

SDA = Linux partitions
SDB = NTFS Storage drive
SDC = NTFS Windows partition

```
Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x425d425c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       14589    97651102+   5  Extended
/dev/sda5            2433        3648     9767488+  82  Linux swap / Solaris
/dev/sda6            3649       14589    87883551   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x102997d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       77826   625129472    7  HPFS/NTFS

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97839783

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9038    72597703+   7  HPFS/NTFS
```


Here is the auto generated menu.lst 

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows XP Professional x64 Edition
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

and here is what I currently have 

```
title WindowsXP
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
makeactive
chainloader +1
```


I have read and I beleive understood the mapping to hd0 is
so that windows can believe that is is booting from the first disk,
HD2,0 would mean 3rd disk, 1st partition which from fdisk tells me
is correct, yet still receive the unsupported grub error.

Any help is very much appreciated

---

### Post by halovivek on 2009-02-26
Please check this [thread]("http://ubuntuforums.org/showthread.php?t=282545"). it will help you to solve.

---

### Post by sepz on 2009-02-26
Halovivek thanks for your quick response,

I have followed that thread before posting here,
and a copy and paste of the code in that thread
switching from hd1,0  to hd2,0  (as my xp is on 3rd hdd)
and swapping 
```

map                (hd0) (hd1)
map                (hd1) (hd0)
```

to 

```
map                (hd0) (hd2)
map                (hd2) (hd0)

```

yields me the same result which is Grub error 13
the rest of the thread talks about fixing the windows boot.ini
which to my knowledge does not require attention on this pc

---

### Post by caljohnsmith on 2009-02-26
So do you get the Grub menu on start up OK, but when you choose to boot Windows you get the Grub error 13? Can you boot Ubuntu OK? In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop (can be the Live CD if necessary):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to Grub error 13 might be.

---

