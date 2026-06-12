---
title: "how can i restore my windows"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by aab001 on 2010-01-03
i have installed my ubuntu 9.10 from the live usb and i used new partition for the hard disk. i diveded the hard disk 3000 for sawp and 15000 Mpb for the /. But after installation i found that windows is removed. how can i make reboot option menu to reboot with window or at least how can i restore my windows.:confused:

---

### Post by shuttleworthwannabe on 2010-01-03
it seems you may have installed on the Windows partition by mistake? Do verify boot with the Live Cd to see if the windows partition is there. if it is there, you could reinstall GRUB to list windows in the boot menu. I do not remember how to reinstall GRUB from the LiveCd, but I am sure someone here wiill help. Okay, here is the [link]("http://ubuntuforums.org/showthread.php?t=224351") that describes this.

---

### Post by aab001 on 2010-01-03
it is not working, when i typed (sudo grub) it gives me command not found

---

### Post by shuttleworthwannabe on 2010-01-03
Sorry, I just realized karmic uses Grub 2, and not the legacy Grub. Google a bit and see of someone has not done this already. My apologies.

S

---

### Post by shuttleworthwannabe on 2010-01-03
Hi there try this [thread]("http://ubuntuforums.org/showthread.php?t=1327197")

---

### Post by Cheesemill on 2010-01-03
Boot from your Live USB then open a terminal and type:
```
fdisk -l
```(Thats a small L not a one)

Post the results back here.

**Do not use your installed Ubuntu**, if you have wiped Windows you'll just be making things worse.

---

### Post by teward on 2010-01-03
If the windows partition was overwritten, you've lost windows.  there's no way to restore whatever files or programs or anything that were on it, and in order to repair it you've got to purchase a new Windows disc and key.

---

### Post by Paqman on 2010-01-03
> **TrekCaptainUSA said:**
> in order to repair it you've got to purchase a new Windows disc and key.

If you've got a valid key you just need to get a copy of the right install disk. You shouldn't need to buy a whole new license just to reinstall.

---

### Post by aab001 on 2010-01-03
> **Cheesemill said:**
> Boot from your Live USB then open a terminal and type:
```
fdisk -l
```(Thats a small L not a one)
 
Post the results back here.
 
**Do not use your installed Ubuntu**, if you have wiped Windows you'll just be making things worse.
 hi there i tried to copy it but unfourtuntly i could not because the connection there is not set. so i will write it here
 
device Boot          start             end            blocks              id   system
/dev/sda1*                 1             1824       14651248+    83   Linux
/dev/sda2             1825              2189      2931862+       5    extended
/dev/sda5            1825               2189      2931831       82   Linux swap / Solaris
 
 
Disk /dev/sdb:  2029 MB, 20299518848
129 heads, 32 sectors/track, 960 cylinders
Units = cylinder of 4128 * 512 = 2113536 bytes
Disk identifier: 0xbf957c29
 
        
device Boot          start             end            blocks              id   system
/dev/sdb1 *              1               961          1981936          6  FAT16
partition 1 has different physical/logical endings:
       phys=(967,   128,   32) logical=(960,  31,  32)

---

### Post by rosswmcgee on 2010-01-03
do you have your restore disks?

---

### Post by aab001 on 2010-01-04
> **rosswmcgee said:**
> do you have your restore disks?
 i have the restore disk. i tried to repair it but it is not working. i don>t want to install the windows again because i have other software that i need them and i don't have thier CD.

---

### Post by worx101 on 2010-01-04
bad news boss, you have overwritten your windows partition.

Only solution is to reinstall windows.

---

### Post by nesdany71 on 2010-01-04
hola, tengo speedy le instale el ubuntu 9.1 llame a telefonica y me dijeron que no tenia los driver para usar la tarjeta de red con ubuntu, pero con xp funciona lo mas bien el internet, el router es un billion bipac 5200g r3.

---

### Post by aab001 on 2010-01-05
> **Cheesemill said:**
> Boot from your Live USB then open a terminal and type:
```
fdisk -l
```(Thats a small L not a one)
 
Post the results back here.
 
**Do not use your installed Ubuntu**, if you have wiped Windows you'll just be making things worse.
 
i am waiting for ur help

---

### Post by aab001 on 2010-01-05
> **aab001 said:**
> hi there i tried to copy it but unfourtuntly i could not because the connection there is not set. so i will write it here
 
device Boot start end blocks id system
/dev/sda1* 1 1824 14651248+ 83 Linux
/dev/sda2 1825 2189 2931862+ 5 extended
/dev/sda5 1825 2189 2931831 82 Linux swap / Solaris
 
 
Disk /dev/sdb: 2029 MB, 20299518848
129 heads, 32 sectors/track, 960 cylinders
Units = cylinder of 4128 * 512 = 2113536 bytes
Disk identifier: 0xbf957c29
 
 
device Boot start end blocks id system
/dev/sdb1 * 1 961 1981936 6 FAT16
partition 1 has different physical/logical endings:
phys=(967, 128, 32) logical=(960, 31, 32)
 
 
please i need ur help ASAP

---

### Post by Methuselah on 2010-01-05
aab001, you have no NTFS partitions so it means that windows was completely obliterated.
Unfortunately it seems like you selected 'use entire disk' when installing Ubuntu on that computer.

I am afraid that there is not much hope of recovering that windows installation, in my opinion.
Maybe there is a possibility fragments of some files may be hanging around but you'd have to do some serious forensic work to find/recover them.

---

