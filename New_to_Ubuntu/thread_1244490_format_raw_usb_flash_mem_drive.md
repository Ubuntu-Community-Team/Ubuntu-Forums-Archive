---
title: "format raw usb flash mem drive"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by webwiller on 2009-08-19
Hi all!

Dont know what my mom's did with my 4gb flash hdd, but after I leaned it to her it came back unrecognizable from ubuntu (which does NOT mount it). I can see it from WinXP (I have dual boot) but cannot format it eighter.
I tried out with GParted and I managed it to see may flash disk but not format it. GParted and WinXP as well, also say my flash mem is now 33mb!!!
4gb>>>33mb :confused:

WinXP tells me it is a RAW disk of 33mb of space. Mom's probably messed up repartitioning or something...

Is there any Easy (not a geeeeeeeeeek;-)) way to turn my flash mem right back?

Ty all in adv!

Chris

---

### Post by Locutus_of_Borg on 2009-08-19
sudo -i
fdisk -l

take note of flash drives /dev/ location, sdb for example

fdisk /dev/sdb

now delete all partitions and create a single new partiton

mkfs.msdos -F 32 /dev/sdb1




you will need to change "sdb" to whatever fdisk says is your flash drive in the second command

---

### Post by LewRockwell on 2009-08-19
> **webwiller said:**
> Hi all!

Dont know what my mom's did with my 4gb flash hdd, but after I leaned it to her it came back unrecognizable from ubuntu (which does NOT mount it). I can see it from WinXP (I have dual boot) but cannot format it eighter.
I tried out with GParted and I managed it to see may flash disk but not format it. GParted and WinXP as well, also say my flash mem is now 33mb!!!
4gb>>>33mb :confused:

WinXP tells me it is a RAW disk of 33mb of space. Mom's probably messed up repartitioning or something...

Is there any Easy (not a geeeeeeeeeek;-)) way to turn my flash mem right back?

Ty all in adv!

Chris

add partition editor to your installation if you don't already have it(you mention it so we would assume that you've already done this, but we'll include it for others reading this thread)

make sure the media is UNMOUNTED(should not show up as any sort of icon on your desktop)

once you're sure it's unmounted then you can proceed to the partition editor and add/delete/reformat to your pleasure

.

---

### Post by webwiller on 2009-08-20
> Disco /dev/sda: 250.0 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x80d2f3ee

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3916    31455238+   7  HPFS/NTFS
/dev/sda2   *        3917        5221    10482412+   7  HPFS/NTFS
/dev/sda3            5222        6788    12586927+  83  Linux
/dev/sda4            6789       30401   189671422+   5  Esteso
/dev/sda5            6789        6853      522081   82  Linux swap / Solaris
/dev/sda6            6854        8028     9438156   83  Linux
/dev/sda7            8029       30401   179711091    7  HPFS/NTFS

Disco /dev/sdb: 32 MB, 32096256 byte
1 testine, 62 settori/tracce, 1011 cilindri
Unità = cilindri di 62 * 512 = 31744 byte
Identificativo disco: 0x00000000

Il disco /dev/sdb non contiene una tabella delle partizioni valida*(translated: disk /dev/sdb does not contain a valid partition table)*
root@webwiller-laptop:~# mkfs.msdos -F 32 /dev/sdb1
mkfs.msdos 3.0.1 (23 Nov 2008)
/dev/sdb1: No such file or directory
root@webwiller-laptop:~# mkfs.msdos -F 32 /dev/sdb
mkfs.msdos 3.0.1 (23 Nov 2008)
mkfs.msdos: Device partition expected, not making filesystem on entire device '/dev/sdb' (use -I to override)
root@webwiller-laptop:~# 

I already tried with GParted but it wont create a new partition on my /dev/sdb. It prompts me that creating a new partition table will erase all datas on my /dev/sdb and when I click "yes" it will work for few secs and then it'll get back saying it was not able to create a new partition table.

---

### Post by webwiller on 2009-08-20
Enclosed screenshot of GParted. In the shown position I click on "new" and get prompet for data erasing if continuing process, I confirm and get a grey screen for a couple of sec's, afterwords I get back to the original screen with "not allocated" space on a grey bar. Again the mem shows to be 25.53mb instead of 4gb!

Any help please???

In addition to this, if it could be of any help, my flash mem also gets very hot in few sec's, when others normally wont. Mhm...

---

### Post by LewRockwell on 2009-08-20
> **webwiller said:**
> Enclosed screenshot of GParted. In the shown position I click on "new" and get prompet for data erasing if continuing process, I confirm and get a grey screen for a couple of sec's, afterwords I get back to the original screen with "not allocated" space on a grey bar. Again the mem shows to be 25.53mb instead of 4gb!

Any help please???

In addition to this, if it could be of any help, my flash mem also gets very hot in few sec's, when others normally wont. Mhm...

If it is getting "very hot in a few seconds" then we would suggest that there is a problem with it and you probably should discard it(they are only $10.00 around here so it's not worth damaging other equipment and/or losing data...throw it away)

.

---

### Post by webwiller on 2009-08-20
You probably right! But it was working fine just b4 I lent it! Anyway...I was looking for some "try-this" option just b4 throwing it away...

---

