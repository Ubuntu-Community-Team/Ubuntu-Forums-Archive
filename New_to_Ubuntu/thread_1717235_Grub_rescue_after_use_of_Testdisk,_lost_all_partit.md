---
title: "Grub rescue after use of Testdisk, lost all partitions"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Guaicuru on 2011-03-29
Hi there. My wife bought a new Samsung 440 notebook with Windows 7 in it (sorry to carry to this place a family issue). As I also wanted to use it and I have been using Ubuntu for the last 4 years I installed Ubuntu 10.10 (64 bit) on it. I intended to obtain a dual boot as I have done in many other computers.

During installation everything went ok but when I rebooted the Grub menu did not appear and the notebook booted directly into Ubuntu (I may have done something wrong with the partitions during installation...).
So I google a bit and used Testdisk to undelete the windows partition (there were 4 of them).

In the next boot I faced the following:

```
GRUB- error: no such partition 
grub rescue>

```

I then put the liveCD again and run some tests.
Apparently only one small partition of 10 gb. survived.


I typed:

sudo fdisk -l 

and obtained:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e3661

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           20769       21985     9765620+   7  HPFS/NTFS

```

Ando also tried:

 sudo gpart /dev/sda

which after a long time gave:


```

Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```


I then ran the Boot Info Script from
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
and obtained the following in RESULTS.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         333,641,728   353,172,968    19,531,241   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        62BC3773BC374139                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

I can't understand all this information.

Obviously I would like to recover everything. That is, obtain the dual boot (that I never had) and all the partitions. I can re install the Ubuntu if necessary, but I don't have a Windows recover CD, so I could try (with help please!) to recover the windows partitions and install the Ubuntu again.
Thanks in advance, I hope I was clear enough.

---

### Post by cariboo on 2011-03-29
I'd suggest you run testdisk again, and try and restore your missing partitions, you should be able to do it if you have written anything else to the hard drive yet.

---

### Post by coffeecat on 2011-03-29
Did you choose the "install alongside" option in the installer. There's a nasty design gotcha in that which can lead to the installer reformatting the whole disc if you also click on the "use whole disc" button. You will then lose Windows and get an Ubuntu single-boot.

What has also complicated things is that you say you had four partitions. These were almost certainly primary partitions which complicates things for the installer - four being the maximum number of primary partitions allowed in the mbr partition table.

If I am right, then some of the filesystem for one, two, three or even four of the partitions has been overwritten already. Which is perhaps why testdisk only found one partition of about 10GB (if my calculation is correct). Which would probably have been a recovery partition.

I agree with cariboo907 - run testdisk again. But be prepared for very bad news. Sorry.

Do you have any restore DVDs for your Windows 7? Most manufacturers don't supply these but include a utility in Windows for you to create them yourself. Which may be too late now.

---

### Post by cmcanulty on 2011-03-29
Here are the restore disks
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by coffeecat on 2011-03-29
> **cmcanulty said:**
> Here are the restore disks
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Sadly, they are not the restore discs I was referring to. Those are recovery or repair discs which have various repair utilities but which cannot re-install a Windows OS. If the Ubuntu installer has overwritten some of the OP's C: partition (which I fear it may have done) the OP will need to re-install Windows. OEM manufacturer's restore DVDs are basically images of the manufacturer's tweaked version of Windows, used to "restore" the machine back to its factory condition, which is really a re-installation.

---

### Post by Jerry N on 2011-03-29
You _might_ be able to get a set of install disks from the manufacturer, for a price.  The 10gb partition probably contains the system restore files and they _might_ be intact.  If you get it restored back to Windows, you will likely be back to 4 partitions and, in addition to shrinking the C: partition from within Windows, you will need to delete one of the 4 partitions so you can create a partition for installing Ubuntu.

Is you wife still speaking to you, or does she know yet?

Jerry

---

### Post by Guaicuru on 2011-03-29
Thanks for all of you for giving me suggestions. 
My wife does not know anything about this yet.

So, If did not misunderstood you, you suggest that I must run again testdisk from the liveCD to try to bring back the windows' partitions.
I'll give it a try and then I tell you.
Thanks again.

---

### Post by Guaicuru on 2011-03-29
> **coffeecat said:**
> Did you choose the "install alongside" option in the installer. There's a nasty design gotcha in that which can lead to the installer reformatting the whole disc if you also click on the "use whole disc" button. You will then lose Windows and get an Ubuntu single-boot.


I didn't use the "install alongside" option because it didn't appear as  an option. I choose to create a new partition table after resizing the last windows partition in order to make place at the end of the hard drive. I thought that all the other windows partitions were logical. Then I created (at the end of the disk, in the space I left) a partition for / and another for the swap.

> **coffeecat said:**
> 
What has also complicated things is that you say you had four partitions. These were almost certainly primary partitions which complicates things for the installer - four being the maximum number of primary partitions allowed in the mbr partition table.

If I am right, then some of the filesystem for one, two, three or even four of the partitions has been overwritten already. Which is perhaps why testdisk only found one partition of about 10GB (if my calculation is correct). Which would probably have been a recovery partition.


Testdisk found the 4 partitions (I think they remained untouched because as I said before I made the ubuntu partitions at the end of the disk), but even after that only one of them appears after boot.


> **coffeecat said:**
> 
I agree with cariboo907 - run testdisk again. But be prepared for very bad news. Sorry.


I`ll give it a try.

---

### Post by Guaicuru on 2011-03-29
Ok. I ran testdisk again with more care (about the primary, logical and booteable partitions to recover). I only choose to recover the 4 windows partitions.

After the boot, the "grub rescue" reapperared and after typing "ls" I obtained:

(hd0) (hd0,msdos4) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)

Should I be optimistic?
How do I make windows boot again?
And after that, should I try to delete one of the primary windows
partitions in order to install Ubuntu again?

Thanks to all of you!

---

### Post by cmcanulty on 2011-03-30
I believe you can get the whole windows images here
[http://www.microsoft.com/downloads/en/details.aspx?FamilyID=696dd665-9f76-4177-a811-39c26d3b3b34&displaylang=en](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=696dd665-9f76-4177-a811-39c26d3b3b34&displaylang=en)

---

### Post by Guaicuru on 2011-03-30
Thank you **cmcanulty**, but that means buying windows again, or am I wrong?
(since in this part of the earth it is almost impossible to buy a notebook without windows preinstalled). 

Since I have "found" the windows partitions apparently untouched, I thought I could fix the MBR somehow (using linux or something else) to recover the original soft installation. As a mater of fact the first partition was called RECOVERY and the second SYSTEM.

I have another question about this. Since the first partition was RECOVERY I choose this one (using Testdisk) to be the bootable partition. I choose the other 3 to be primary partitions (remember I undeleted only the windows' partitons). 
**Question**: that was the right thing to do? 

Thanks in advance.

---

### Post by coffeecat on 2011-03-30
> **Guaicuru said:**
> Since I have "found" the windows partitions apparently untouched, I thought I could fix the MBR somehow (using linux or something else) to recover the original soft installation. As a mater of fact the first partition was called RECOVERY and the second SYSTEM.

If you didn't create a Windows 7 repair CD you can download one from the link cmcanulty posted earlier. You can then run 'bootrec /FixMbr' from it. See here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If that is not feasible, you can repair the Windows mbr with the Ubuntu live CD. Boot up the live CD and go to the live desktop. Run these terminal commands:

```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```Ignore any warnings and let it be installed to the MBR.

> **Guaicuru said:**
> I have another question about this. Since the first partition was RECOVERY I choose this one (using Testdisk) to be the bootable partition. I choose the other 3 to be primary partitions (remember I undeleted only the windows' partitons). 
**Question**: that was the right thing to do? 


Probably. Pre-installed Windows 7 usually has a separate boot/recovery partition of about 100-200MB only. If your recovery partition is that size, then it almost certainly is the one that needs the boot flag.

---

### Post by cmcanulty on 2011-03-30
No it should work as long as you have a legal key. It is on microsofts own page. I think the most is you might have to activate again by phone or web using your key.

---

### Post by Guaicuru on 2011-03-30
Great!!
I got a windows 7 recovery disk at work and then run
after choosing the recovery option at the command prompt:
```
BootRec.exe /fixmbr
```

and afterwards:
```
BootRec.exe /FixBoot
```

(These was taken from: [http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html](http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html))

Then, as I read somewhere that all that might not be enough I typed:

```
sfc /scannow
```

to fix any loose end (taken from: [http://www.bloginformatico.com/comando-sfc-scannow-escanear-detectar-reparar-archivos-danados-en-windows.php](http://www.bloginformatico.com/comando-sfc-scannow-escanear-detectar-reparar-archivos-danados-en-windows.php)).
That last command took a long time but didn't find anything wrong.

That fixed the boot in windows!!!
Afterwards I deleted one of the 4 partitions that were created during the original windows installation. Then I installed Ubuntu on that left space (having reduced to 3 the primary partitions). 

Do you think the regular installation made 4 primary partitions on purpose?
I think the first of them was made by the "Samsung recovery"
soft (20gb) and is called "RECOVERY". 
The other is small and has only 100mb and is called
"SYSTEM".
On the third were all the windows programs.
The fourth was done (I believe) to save the data in a different partition. 
But all this was done without options (or at least they
were not obvious to me)...


Dear people, with you Ubuntu has a long life guaranteed.

Thank you so much.

---

### Post by coffeecat on 2011-03-30
> **Guaicuru said:**
> 
Do you think the regular installation made 4 primary partitions on purpose?
I think the first of them was made by the "Samsung recovery"
soft (20gb) and is called "RECOVERY". 
The other is small and has only 100mb and is called
"SYSTEM".
On the third were all the windows programs.
The fourth was done (I believe) to save the data in a different partition.

Not on purpose. Just thoughtlessness I think. HP is another make where they have four primary partitions making it difficult if you want to install Linux.

From your description, my guess is that the 100MB SYSTEM partition was the original Windows boot partition. If you've installed Windows boot files to the C: partition with bootrec then that's fine. I have a separate 100MB boot partition for Windows 7 on my pre-installed Acer laptop but when I installed W7 on my main desktop with a retail disc I made sure it all went into one partition. 

Then there's the 20GB "RECOVERY" partition. That's probably a manufacturer's restore partition for if you ever need to re-install the Windows system back to its factory condition. If the fourth partition is a data partition then there's no reason why it could not have been a logical partition in the first place. Laziness or lack of imagination on the part of the Samsung developers is my most generous explanation for why they did not make it so.

I'm glad you've recovered your partitions. Good luck with Ubuntu. But there's one last thing I suggest you do. Sometimes testdisk will successfully recover partitions but put illegal entries in the partition table. These are easily fixed but worth knowing about because they confuse Ubuntu's Gparted partitioner mightily. If you want to be sure, boot up with the Ubuntu live CD and post the output of this terminal command:

```
sudo fdisk -lu
```

---

### Post by Guaicuru on 2011-03-30
I typed on a usual session (not with the liveCD) the command
```

sudo fdisk -lu
```
in a terminal and obtained:
```

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x000e3661

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048    41945087    20971520    7  HPFS/NTFS
/dev/sda2        41945088    42149887      102400    7  HPFS/NTFS
/dev/sda3        42149888   176238591    67044352    7  HPFS/NTFS
/dev/sda4       176240638   498188287   160973825    5  Extendida
/dev/sda5       176240640   371550207    97654784   83  Linux
/dev/sda6       371552256   488736767    58592256   83  Linux
/dev/sda7       488738816   498188287     4724736   82  Linux swap / Solaris

```

Do I have to do it with the liveCD or this is enough? 
Thanks for caring about these details.


I still have to build an NTFS partition at the end in order to share data with windows.

---

### Post by coffeecat on 2011-03-31
> **Guaicuru said:**
> Do I have to do it with the liveCD or this is enough? 

That's fine. Sorry - I should have said live CD **or** your new installation of Ubuntu.

> **Guaicuru said:**
> I still have to build an NTFS partition at the end in order to share data with windows.

That will have to be a logical partition, but Windows will be happy  with a logical data partition. You will have to enlarge your extended partition sda4 first because its end sector is 498188287, the same as the end sector of the current last logical partition sda7. The last sector of the hard drive is 625142448, which gives you about 65GB free space according to my calculation. 

Whether you create this partition from Gparted in the live CD or install Gparted to your new installation for this, you will have to right-click on the swap partition (in Gparted) and choose "swapoff" before you will be able to resize the extended partition. 

Good luck!

---

### Post by Guaicuru on 2011-03-31
Thank you so much **coffecat**!!!

I needed this details.

I followed your instructions and finally made that last NTFS partition.
I had to do it from the liveCD (I suppose that was because the extended partition sda4 was mounted when I tried to do it after booting the hard drive).

Everything is working fine now.

I post here how everything was left.
Typing
```
sudo fdisk -lu
```
I got

```
Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x000e3661

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048    41945087    20971520    7  HPFS/NTFS
/dev/sda2        41945088    42149887      102400    7  HPFS/NTFS
/dev/sda3        42149888   176238591    67044352    7  HPFS/NTFS
/dev/sda4       176240638   625141759   224450561    5  Extendida
/dev/sda5       176240640   371550207    97654784   83  Linux
/dev/sda6       371552256   488736767    58592256   83  Linux
/dev/sda7       488738816   498188287     4724736   82  Linux swap / Solaris
/dev/sda8       498190336   625141759    63475712    7  HPFS/NTFS

```

Thanks to you all again.

---

### Post by coffeecat on 2011-03-31
> **Guaicuru said:**
> I got

```
Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x000e3661

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048    41945087    20971520    7  HPFS/NTFS
/dev/sda2        41945088    42149887      102400    7  HPFS/NTFS
/dev/sda3        42149888   176238591    67044352    7  HPFS/NTFS
/dev/sda4       176240638   625141759   224450561    5  Extendida
/dev/sda5       176240640   371550207    97654784   83  Linux
/dev/sda6       371552256   488736767    58592256   83  Linux
/dev/sda7       488738816   498188287     4724736   82  Linux swap / Solaris
/dev/sda8       498190336   625141759    63475712    7  HPFS/NTFS

```

I forgot to mention in my last post that I couldn't see any testdisk-induced irregularites in your earlier fdisk output. Neither are there now - or not that I can see - which is good news. :)

Testdisk sometimes gives you a partition table with overlapping partitions or other oddities, but it didn't this time.

Good luck!

---

