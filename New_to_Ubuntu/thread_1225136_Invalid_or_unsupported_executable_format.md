---
title: "Invalid or unsupported executable format"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by glide on 2009-07-28
Hi guys,

I have a problem that many guys have aparently,
but I can't find the solution for mine in the forum.
I get...
[QUOTE=my computer]Invalid or unsupported executable format[/QUOTE]
... when I hit my Windows Grub link.

Here is my fdisk
```

Disque /dev/sda: 1000.2 Go, 1000204886016 octets
255 têtes, 63 secteurs/piste, 121601 cylindres, total 1953525168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Identifiant de disque : 0x00063093

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *          63  1941455249   970727593+  83  Linux
/dev/sda2      1941455250  1953520064     6032407+   5  Etendue
/dev/sda5      1941455313  1953520064     6032376   82  Linux swap / Solaris

Disque /dev/sdb: 320.0 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Identifiant de disque : 0x375e8732

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1   *          63    40965749    20482843+   6  FAT16
/dev/sdb2        40965750   625137344   292085797+   f  W95 Etendue (LBA)
/dev/sdb5        40965813   625137344   292085766    7  HPFS/NTFS

Disque /dev/sdc: 203.9 Go, 203928109056 octets
255 têtes, 63 secteurs/piste, 24792 cylindres, total 398297088 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Identifiant de disque : 0x16c175da

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdc1   *          63   398283479   199141708+   7  HPFS/NTFS
```

Here is my Windows menu.lst section:

```

title           Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1
```

My Windows system is actually located in sdc1.

Do someone have a clue ?

---

### Post by unutbu on 2009-07-28
While booted into Ubuntu, edit /boot/grub/menu.lst.
```

gksu gedit /boot/grub/menu.lst
```

Go to the bottom of the file. Add the following boot stanza:
```

title           Microsoft Windows XP Professional (hd1,0)
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

Save and exit the text editor. Reboot. Try booting "Microsoft Windows XP Professional (hd1,0)".

If it does not work, please run [boot_info_script]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and post the RESULTS.txt file here.

---

### Post by glide on 2009-07-28
It works ! thanx
But how ?

---

### Post by unutbu on 2009-07-28
When booted into Linux, GRUB uses Linux to list the order of the drives. The first drive gets named (hd0), the second on (hd1), etc.

When booting the computer, GRUB uses the BIOS to list the order of the drives. Sometimes the BIOS order does not match Linux's order. 

So even though sdc1 looks like (hd2) while booted in Linux, you were getting a GRUB error when trying to boot (hd2,0). So the Windows partition apparently was not (hd2,0).

Since you are using GRUB to boot the machine, I guessed that you set the BIOS to boot from sda first. This usually causes the BIOS to list sda as (hd0). If my guess is correct, then the Windows drive could not be (hd0,0).

That left only one option: that the Windows partition is (hd1,0).

---

### Post by glide on 2009-07-29
Got it! thanx again

---

