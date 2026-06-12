---
title: "Marked my ntfs partition as swap"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Saija on 2010-12-05
Hi all

Installing Merkat i just marked my secondary ntfs partition(pictures, games, movies, etc) as swap, now i just searched some solutions which include using cfdisk to change te type from 82 to 7(ntfs), i did that, then i try to mount the partition this way: ```
sudo mount -t ntfs /dev/sda7 COSAS/
``` and this is all i get:
```
NTFS signature is missing.
Failed to mount '/dev/sda7': Argumento inválido
The device '/dev/sda7' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

This is my fdisk -l output:
```
saija@hal9000:/media$ sudo fdisk -l

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xa57f6db9

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1           5       40131   de  Utilidad Dell
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1919       15461   108784147+   7  HPFS/NTFS
/dev/sda4   *       15462       60801   364193519+   5  Extendida
/dev/sda5           15462       23350    63368361   83  Linux
/dev/sda6           23351       31295    63817383   83  Linux
/dev/sda7           36159       60653   196756056    7  HPFS/NTFS
/dev/sda8           60654       60801     1188778+  82  Linux swap / Solaris
/dev/sda9           31295       36158    39061504    b  W95 FAT32

Las entradas de la tabla de particiones no están en el orden del disco

```

I hope someone has the patience to make some suggestion and i hope i can bring my data back.

Thank you.

PS: all of the messages posted here are in spanish, that's my native language

---

### Post by sikander3786 on 2010-12-05
First of all, stop using your system from the HDD. Instead boot into a Live CD.

And try testdisk.

[https://help.ubuntu.com/community/DataRecovery#Testdisk](https://help.ubuntu.com/community/DataRecovery#Testdisk)

---

### Post by Saija on 2010-12-06
Thank you for your answer, i tried changing the type of the partition using TestDisk and this failed, tonight i'll try some more options with this program and i'll let you know how it performed.

---

### Post by Saija on 2010-12-08
Again i've tried changing the type of the partition from 82(swap) to 7(ntfs), testdisk ask me to restart the laptop, i restart it and the change it's ignored, the partition remains the same.  Now i couldn't even log to windows(vista), there's some error trying to read something(the boot sector i think i saw... :S), now my only option left is make some recovery and reinstall all again?
What can i do to recover my partitions and data?

thank you.

---

### Post by sikander3786 on 2010-12-08
Feeling sorry for your troubles.

I don't know much about data recovery. I gave you the link because I know testdisk works. How? I have no experience myself.

If the data on those partitions was that important, you can send your disks for forensic recovery.

Re-install is always an option if you feel you can live without your old data.

---

### Post by oldfred on 2010-12-08
I lost a folder or two and was able to recover some files with photorec. It does not recover names, but music & photos have internal data that you can use to rename files it recovers. You have to copy recovered data to a different drive and it will take a long time. Text files that I had updated many times showed up many times and I had lots of trouble figuring out which was the most current (never did), but recovered most  of the contents of the most important ones. Lots of grepping to search files for key words.

Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by iponeverything on 2010-12-08
My guess is that that the install formated the swap partition so just changing the type flag is not going to bring it back. 

oldfred's suggestions might be your best bet.

---

### Post by Saija on 2010-12-11
Hi all

Thank you by your replies, i think i'm going to take the recovery option, but right now i don't have an spare disk to perform this, and yes, the data is important: 
[LIST]
[*]family pictures and videos, including some passed away relatives
[*]music dating 11 years
[*]games(Quake 3 i'm missing you!)
[/LIST]

I think i'm going to call dell support and ask them if they could do something, when i bought this laptop i included some guarantee and support, maybe this option have some costs but i'm using all the options i have.

Again, thank you guys and i'll let you know how i solve this.

PS: yes, i know, i must have some backups, but as we say in my country:"Al perro no lo capan si no una vez", know i'll make backups as soon as i recover my data.

---

### Post by Saija on 2010-12-11
Sorry, i'm just reading the tutorial left by Oldfred([http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)) and there i need other disk, can i do that using some kind of remote disk? 
i ask this because i have the desktop of my brother and i want to left the recovered data there.

Thank you.

EDIT= I'm testing with nfs right now, i'll let you know how well this works...

EDIT2 = the disk in my brother's desktop is also screwed, i guess i'll have to buy an external disk... :S

---

### Post by amjjawad on 2010-12-11
> **iponeverything said:**
> My guess is that that the install formated the swap partition so just changing the type flag is not going to bring it back. 

oldfred's suggestions might be your best bet.

+1

But Good Luck :)

---

### Post by oldfred on 2010-12-11
One more possibility. NTFS requires both the 07 type and the boot sector as NTFS. 

Test disk has a recover boot sector function, but that may be gone with the change. But if you have converted to 07 testdisk may be able to rebuild the boot sector so you can mount it. Not sure if any data would then be recoverable or not beyond having to use photorec to scan drive.

As described, it has an option to "Recover NTFS boot sector from its backup"
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Saija on 2011-01-08
Hi guys

Sorry by no replying to yours posts, right now i'm checking the disk using Testdisk, Santa's got me a brand new disk and an external cage so i can try to recover some files, i'll let you know how well this performs.

---

