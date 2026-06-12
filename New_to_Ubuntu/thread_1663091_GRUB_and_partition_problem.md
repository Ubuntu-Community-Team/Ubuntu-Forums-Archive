---
title: "GRUB and partition problem"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by miglos on 2011-01-09
I've been using windows vista since I bought this VAIO laptop, now I've installed Ubuntu 10.10 Maverick Meerkat, I've had some issues installing and configuring it, but finally it's working and it's awesome.

During the installation process, I created a 10GB partition in my internal disk (with windows vista home edition), but the installation didn't work, so I installed Ubuntu on an external disk (it's a 500GB - 120GB for Ubuntu / 380 for files). Now when I start my computer, if the external disk is plugged there's a menu so I can choose which OS I want to use. If it's not connected, it only shows a cursor blinking for a while and then appears something about GRUB issues, (I modified the booting options to USB device first), while the external HD is connected, everything works fine, but what I need is that if the External HD is not connected, windows vista starts automatically, I suppose that the partition I first created is causing this.

[LIST=1]
[*]Is it possible to "re-assign" that 10GB partition to the original 200GB partition?
[*]If Nº 1 is not possible, simply formatting that space will solve the problem?
[*]Can I connect my external HD to any PC and will show me the GRUB options, so I can use my Ubuntu 10.10 OS?
[/LIST]
Thanks!!!

---

### Post by kansasnoob on 2011-01-09
Please boot into Ubuntu and post the output from Terminal of:

```
sudo parted -l
```

BTW that's a lower case L at the end.

---

### Post by miglos on 2011-01-09
Thanks for your answer, this is the result:

```

Modelo: ATA FUJITSU MHY2200B (scsi)
Disco /dev/sda: 200GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin    Tamaño  Tipo     Sistema de ficheros  Banderas
 2      9814MB  200GB  190GB   primary  ntfs                 arranque


Modelo: Seagate FreeAgent Go (scsi)
Disco /dev/sdb: 500GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin    Tamaño  Tipo      Sistema de ficheros  Banderas
 1      32,3kB  400GB  400GB   primary   ntfs
 2      400GB   500GB  101GB   extended
 5      400GB   496GB  96,5GB  logical   ext4
 6      496GB   500GB  4136MB  logical   linux-swap(v1)
```

---

### Post by Synthetic Sam on 2011-01-09
I've also come across this issue.  It seems that grub installs itself on the HDD that you select during installation, but overwrites the MBR of the first HDD in the system, pointing to the boot partition of the external drive.  Best option is to manually install grub to the MBR of the external disk, then use your vista install CD recovery console to "fix" the MBR of your internal HDD.


This command will install grub to the MBR of the external disk(sdX is external HDD /dev/sdb above):
```


sudo grub-install /dev/sdX 


```

then use Windows Vista install cd and run the following from the recovery console (with external drive unplugged):

```

Bootrec.exe /Fixmbr

```

Now your internal disk will boot vista and you can use compmgmt.msc (Computer Management) to resize your windows partition to occupy the entirety of the disk.

To boot Ubuntu on the external disk, you will need to select that as the boot device in the BIOS when it's plugged in, usually by pressing F12 (or something similar) during the initial boot screen, and selecting the external drive (this should bring you to grub).

See here for more info: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

and here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by miglos on 2011-01-10
Thanks for your answer.
This is the result after installing GRUB to the MBR of the external disk:
```
miguel@miguel-VGN-NR250FE:~$ sudo grub-install /dev/sdb
[sudo] password for miguel: 
Installation finished. No error reported.
```

I don't have any vista install/recovery CD disk, so as soon as I get one I'll post the results.

---

### Post by Synthetic Sam on 2011-01-10
> **miglos said:**
> Thanks for your answer.
This is the result after installing GRUB to the MBR of the external disk:
```
miguel@miguel-VGN-NR250FE:~$ sudo grub-install /dev/sdb
[sudo] password for miguel: 
Installation finished. No error reported.
```

I don't have any vista install/recovery CD disk, so as soon as I get one I'll post the results.
That output looks fine.  Windows XP CD won't work for Vista unfortunately, so it will have to be Vista/7 disk to fix the Windows Bootloader MBR.

---

### Post by wilee-nilee on 2011-01-10
> **miglos said:**
> Thanks for your answer.
This is the result after installing GRUB to the MBR of the external disk:
```
miguel@miguel-VGN-NR250FE:~$ sudo grub-install /dev/sdb
[sudo] password for miguel: 
Installation finished. No error reported.
```

I don't have any vista install/recovery CD disk, so as soon as I get one I'll post the results.

You do now.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by kansasnoob on 2011-01-10
For lack of a Vista disc you can also use Lilo to create a Windows readable mbr just by booting into Ubuntu and running:

```
sudo apt-get install lilo

```

```
sudo lilo -M /dev/sda mbr

```

Regarding this:

> Is it possible to "re-assign" that 10GB partition to the original 200GB partition?

It appears that 10GB is unallocated:

```
Modelo: ATA FUJITSU MHY2200B (scsi)
Disco /dev/sda: 200GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin    Tamaño  Tipo     Sistema de ficheros  Banderas
 2      9814MB  200GB  190GB   primary  ntfs                 arranque

```

But the 10GB appears to be at the beginning of the drive which scares me a bit. What did you use to create that 10GB partition? I always prefer resizing Vista and Win7 using only their own partitioning tools.

Anyway, if Windows boots OK, I'd be very reluctant to move the beginning of that Vista partition.

---

### Post by mastablasta on 2011-01-10
> **kansasnoob said:**
> For lack of a Vista disc you can also use Lilo to create a Windows readable mbr just by booting into Ubuntu and running:
 
...
 
Out of curiousity, why is Lilo not used by default in Ubuntu?

---

### Post by miglos on 2011-01-10
Thanks for your answers, to all of you!
So, after creating a readable windows MBR with these commands:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```will I be able to load Vista automatically if my external HDD is not plugged in?

That 10GB partition was created using the Ubuntu installation disk, what should I do with that -unallocated- 10GB partition?

---

### Post by miglos on 2011-01-10
I've just executed
```
sudo apt-get install lilo
``` and this is what came out:
```
Configuración de LILO                                                                                          
   &#9474;                                                                                                               
   &#9474; Parece que esta es su primera instalación de LILO. Es absolutamente necesario
   &#9474; ejecutar liloconfig(8) cuando
   &#9474; complete este proceso y después ejecutar /sbin/lilo.                            
   &#9474;                                                                                                                
   &#9474; LILO no funcionará si no hace esto.
```which means I have to execute ```
liloconfig(8)
``` and then ```
/sbin/lilo
```, in order to get LILO working.
and finally showed this:
```
WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian
```

what do these commands do?

---

### Post by miglos on 2011-01-10
> So, after creating a readable windows MBR with these commands:
[LIST]
[*]sudo apt-get install lilo
[*]sudo lilo -M /dev/sda mbr
[/LIST]will I be able to load Vista automatically if my external HDD is not plugged in?

YES, it works just fine now.
**But!** if I plug in my external HDD with ubuntu to another PC it does not shows the GRUB menu. 
It shows this:```
error: no such partition
grub rescue> _
```
What do I need to do now?

---

### Post by Synthetic Sam on 2011-01-10
> **miglos said:**
> YES, it works just fine now.
**But!** if I plug in my external HDD with ubuntu to another PC it does not shows the GRUB menu. 
It shows this:```
error: no such partition
grub rescue> _
```
What do I need to do now?
Read and follow the instructions under "Rescue Mode" at the following webpage: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[edit] Alternatively, read "METHOD 3 - CHROOT" under the reinstalling grub2 section.  Personally I would find that easier, as I'm not too familiar with grub command line, but the basic idea is that you want to be able to access your system to run the "sudo update-grub" command which will update the grub configuration file.

---

### Post by kansasnoob on 2011-01-10
> **miglos said:**
> YES, it works just fine now.
**But!** if I plug in my external HDD with ubuntu to another PC it does not shows the GRUB menu. 
It shows this:```
error: no such partition
grub rescue> _
```
What do I need to do now?

Slow down a bit, I'm old and need to do one thing at a time ;)

I want you to certain that the original machine (from here on referred to as machine #1) boots properly with the new MBR we created using Lilo if the external drive is not plugged in, but that both Ubuntu and Windows boot alright using grub when the external is plugged in!

If yes then we need to check out machine #1's hardware. The output of the following commands should tell me what I need to know:

```
cat /proc/cpuinfo|head -10
```

```
free -m
```

```
lspci | grep VGA
```

```
lspci | grep Audio
```

I already know what the partitioning/drive arrangement is on machine #1 from the output of "sudo parted -l" but now we need to look at the OTHER machine (from here on we'll call it machine #2).

So on machine #2 you need to boot either a Live CD or Live USB and produce the same output as I referenced above. Be sure to label/separate the outputs so I know which is machine #1 and which is machine #2.

So, just to recap, from machine #2 I need to see:

```
sudo parted -l
cat /proc/cpuinfo|head -10
free -m
lspci | grep VGA
lspci | grep Audio
```

There are a few reasons for this. If the hardware is a lot different it will require too much reconfiguration going from one machine to another, and if the internal drive arrangement is considerably different that can also cause problems.

Anyway, let's work from there. I have two different machines, one of which is largely Intel, and the other largely VIA and an actual "hard" install simply doesn't share well between them.

Off topic, but I happen to love using the newer Lucid Puppy Live CD/USB to play back and forth between my two machines. It only requires about one minute to boot and after booted it runs totally in RAM.

NOTE: I may be unavailable off and on due to livestock needs and a snowstorm so please be patient.

---

### Post by kansasnoob on 2011-01-10
> **Synthetic Sam said:**
> Read and follow the instructions under "Rescue Mode" at the following webpage: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[edit] Alternatively, read "METHOD 3 - CHROOT" under the reinstalling grub2 section.  Personally I would find that easier, as I'm not too familiar with grub command line, but the basic idea is that you want to be able to access your system to run the "sudo update-grub" command which will update the grub configuration file.

But it's then very likely that the OP will have to repeat that each time the drive is moved from one machine to another isn't it?

---

### Post by kansasnoob on 2011-01-10
> **miglos said:**
> Thanks for your answers, to all of you!
So, after creating a readable windows MBR with these commands:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```will I be able to load Vista automatically if my external HDD is not plugged in?

That 10GB partition was created using the Ubuntu installation disk, what should I do with that -unallocated- 10GB partition?

If Windows boots OK I'm reluctant to do anything with it. I'd need to see the output of the Boot Info Script as described in the following link before even considering what to do:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Moving the beginning of a Win OS partition can often render a Win OS unbootable and require re-installation :(

---

### Post by kansasnoob on 2011-01-10
> **mastablasta said:**
> Out of curiousity, why is Lilo not used by default in Ubuntu?

I don't know for sure. Very little recent development judging from the Maverick changelog:

> lilo (1:22.8-8ubuntu1) karmic; urgency=low

  * Merge from debian unstable, remaining changes: LP: #409321
    - debian/control: Build for lpia, too.
    - 03_boot-prompt.patch, 03_lilo-version.patch: Change Debian branding to
      Ubuntu.

 -- Bhavani Shankar <right2bhavi@gmail.com>  Wed, 05 Aug 2009 18:43:40 +0530

lilo (1:22.8-8) unstable; urgency=low

  * Fix some more bashisms. (Closes: #535399)
  * debian/lilo.postinst: Add -H flag to only install to active MD arrays.
    (Closes: #507366)

 -- William Pitcock <nenolod@dereferenced.org>  Sat, 01 Aug 2009 15:54:10 -0500

lilo (1:22.8-7ubuntu1) jaunty; urgency=low

  * Merge from debian unstable, remaining changes: (LP: #304346)
    - debian/control: Build for lpia, too.
    - 03_boot-prompt.patch, 03_lilo-version.patch: Change Debian branding to
      Ubuntu.

 -- Bhavani Shankar <right2bhavi@gmail.com>  Tue, 02 Dec 2008 16:26:42 +0530

---

### Post by Synthetic Sam on 2011-01-10
> **kansasnoob said:**
> But it's then very likely that the OP will have to repeat that each time the drive is moved from one machine to another isn't it?
If the drive configuration between the two machines is different, then yes, as grub will constantly be looking on the wrong partition for /boot.

---

### Post by miglos on 2011-01-10
> "Slow down a bit, I'm old and need to do one thing at a time... :)
 
I want you to certain that the original machine (from here on referred to as machine #1) boots properly with the new MBR we created using Lilo if the external drive is not plugged in, but that both Ubuntu and Windows boot alright using grub when the external is plugged in!
 
**[SIZE=1](I don't know how to add the "Originally Posted by..." thing [/SIZE]**:()

 
The original machine works perfect! 
 
 
 

Ok, now we have 2 issues open, in order of importance:[LIST=1]
[*]What to do with the 10GB missing in HDD(Machine #1)
[LIST]
[*]I'll follow the instructions of the link and post.
[/LIST]
[*]How to boot with that external HDD in another PC.
[LIST]
[*]I'll post the result of the commands **_kansasnoob_** wrote.
[/LIST]
[/LIST]

---

### Post by miglos on 2011-01-10
Answer for the second issue:

_**Machine #1:**_
```
miguel@miguel-VGN-NR250FE:~$ cat /proc/cpuinfo|head -10
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
stepping    : 13
cpu MHz        : 1000.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
miguel@miguel-VGN-NR250FE:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2003        742       1260          0         48        343
-/+ buffers/cache:        350       1652
Swap:         3943          0       3943
miguel@miguel-VGN-NR250FE:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
miguel@miguel-VGN-NR250FE:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```[U][B]Machine #2 (Ubuntu Live CD - 10.10 Maverick Meerkat)
[/B][/U]```
ubuntu@ubuntu:~$ sudo parted -l
Modelo: ATA Hitachi HTS54161 (scsi)
Disco /dev/sda: 120GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin    Tamaño  Tipo     Sistema de ficheros  Banderas
 1      32,3kB  112GB  112GB   primary  ntfs                 arranque
 2      112GB   120GB  8183MB  primary  ntfs


Aviso: No se puede abrir /dev/sr0 en modo lectura-escritura (Sistema de solo
lectura). /dev/sr0 ha sido abierto en modo de sólo lectura.
Error: /dev/sr0: etiqueta de disco no reconocida                          
ubuntu@ubuntu:~$ cat /proc/cpuinfo|head -10
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping    : 6
cpu MHz        : 1000.000
cache size    : 4096 KB
physical id    : 0
siblings    : 2
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        723        277          0         96        406
-/+ buffers/cache:        220        780
Swap:            0          0          0
ubuntu@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
ubuntu@ubuntu:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
```

---

### Post by kansasnoob on 2011-01-10
Since machine #1 uses Intel Graphics:

> miguel@miguel-VGN-NR250FE:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

And machine #2 uses ATI:

> ubuntu@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]

I think you'd be foolish to pursue trying to get a "hard install" to boot on both machines. A "live" installation configures as it loads whereas a "hard" install does NOT!

Based on that I think it would be foolish to try and figure out how to get grub2 or any bootloader to boot both.

---

