---
title: "External Hard Drive without access"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by sweetthdevil on 2005-10-13
Hi Good Evening,

I Just Update Ubuntu to Breezy, and everythings is working very well, except for my external hard drive of 250go on the usb.

This hard drive is seperate in two drive, on the last hoary the first party of my hd was usb and the second was usb1, the problem is now i only see the second party...

The first party do not appear...

What can i do??:confused:

---

### Post by Mr_J_ on 2005-10-13
This is going to sound stupid. I know it will.

Have you tried manually "[COLOR="DarkOrange"]mount[/COLOR]"ing them?
This is also a request to you to take extra care in formulating your english, because I had some problems in understanding what your problem was.

As a non native english speaker I had the luck to have been nuts about GIJoe when I was a child, which surprisingly roose my english level greatly.

---

### Post by sweetthdevil on 2005-10-13
Sorry for my english, i wright to fats, anyway...

No i didn't try to mount it because if i do a cfdisk i can not see my external hard drive at all, not even the one i can access.

This is only my internal hard drive...


```
 cfdisk 2.12p

                           Unité de disque: /dev/hda
                      Taille: 60011642880 octets,  60.0 Go
             Têtes: 255   Secteurs par piste: 63  Cylindres: 7296

    Nom         Fanions    Part Type  Type SF          [\ufffftiq.]        Taille (Mo)------------------------------------------------------------------------------
    hda1        Amorce      Primaire  NTFS             []              26411,38
    hda5        Amorce      Logique   Linux ext3       [/]             31461,70
    hda6                    Logique   Linux swap / Solaris              2138,58









     [Amorçable][Détruire] [  Aide  ]  [Maximiser] [Afficher]
     [Quitter ]  [  Type  ]  [Unités ]  [\uffffcrire ]

             Basculer le fanion d'amorce pour la partition courante


```

And that's a fdisk -l:

```
Disque /dev/sda: 250.0 Go, 250059350016 octets
255 têtes, 63 secteurs/piste, 30401 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1       25063   201318516    c  W95 FAT32 (LBA)
/dev/sda2           25064       30401    42877485    c  W95 FAT32 (LBA)

```


So to be honest with you i'm a bit lost...

---

### Post by sweetthdevil on 2005-10-13
I was watching ubuntu starting up, and the module were ok except the "hot plug system", so i guess it's coming from there...

But where i'm surprise is that only one partition of my external hard drive is automatly monted, and the second one..

So if anyone can help me.... :???:

---

### Post by meastp on 2005-10-13
[QUOTE=sweetthdevil]I was watching ubuntu starting up, and the module were ok except the "hot plug system", so i guess it's coming from there...[/QUOTE]

Second that! I noticed that too. However, my (new, unformatted) external drive was detected instantly (and I partitioned it (FAT32) with gparted). When it was finished writing partition table etc. to disk, it showed up as an external disk.

---

### Post by sweetthdevil on 2005-10-13
Yes but mine isn't new and i've all my data on it, so i'm not going to format :(

---

### Post by sweetthdevil on 2005-10-14
Any one?

---

### Post by Mr_J_ on 2005-10-14
If I'm reading that french correctly, then all you need to do is:

 $ mount -t fat32 /dev/sda1 /mnt/win1
 $ mount -t fat32 /dev/sda2 /mnt/win2

#you do have to have the /mnt/win1 or 2 can be whatever you want, as long #as they're already created

OR

Go to Hardrives in the Sistem Menu.... I use Ubuntu in portuguese, so diferent translations...
Should be around Users. It should allow you to set up any internal Hdds. Those I tried, but not external ones. Should show up there tho.

---

### Post by sweetthdevil on 2005-10-14
Good reading, i'm actually french, anyway...

I went to system menu, and the file is media for me. I've got usb0 but when i open it, it's empty..

i try  $ mount -t fat32 /dev/sda1 /mnt/win1 /mnt/win1 isn't valid.

:???:

---

