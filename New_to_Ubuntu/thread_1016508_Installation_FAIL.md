---
title: "Installation FAIL"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by paramethis on 2008-12-20
heres my system

asrock 939Dual-SATA2 link to mobo

AMD Athlon64 4000+

2gb WINTEC ddr 400 ram

maxtor 40gb sata 3.0g/s HDD

Western digital 500 GB sata 3.0g/s HDD

BFG NVIDIA GeForce 7600 GT OC 256MB PCIe
__________________________________________________ _______________________

I have tried installing
ubuntu 8.10
ubuntu 8.10 alt
ubuntu 7.10 fiesty
ubuntu gutsy
ubuntu 5.10 (had it laying around)
kubuntu 8.10
debian 40rs
fedora 10
__________________________________________________ ___________________
it freezes while attempting to format partitions on all ubuntus like below

partions formating

5%

creating ext3 file system for / in partition #1 of scsi1 (0,0,0)
__________________________________________________ ______________________
I have also tried using Gpart and it just freezes claiming kernal sync error. I also tried DBAN which starts then pops up stuff over top its run screen and freezes.

my hardware isn't the issue. i have tried installing on both hard drives with the other unplugged. have tried 2 cdrom drives. all bios settings are standard (default). i have also looked through for anything out of the ordinary 

Some one previously mentioned a jmicron controller which I have no idea what that is or how to fix it. Others have pointed out that since its sata it shouldn't read as scsi.

What should I do besides breakdown spend $90 and go buy WinXP

---

### Post by dwasifar on 2008-12-20
Can you give some detail about the machine?  How much ram is in it?

---

### Post by paramethis on 2008-12-20
athlon64 4000+
2gb ram
500gb wd hdd
40gb maxtor hdd
asrock mobo

will post full specs in morning

it freezes on the partions formating screen 

5%

creating ext3 file system for / in partition #1 of scsi4 (0,0,0)

---

### Post by hyper_ch on 2008-12-20
are you sure it freezes? it could just take a long time for 500gb

---

### Post by igknighted on 2008-12-20
Is it really a scsi drive?

If it's really sata or pata, what type of controller do you have?  Many times jmicron controllers have caused Ubuntu to throw fits.

---

### Post by logos34 on 2008-12-20
> **igknighted said:**
> Many times jmicron controllers have caused Ubuntu to throw fits.

oh, the dreaded jmicron issue...

---

### Post by paramethis on 2008-12-20
it is a sata hdd so if that is the issue how do I change or fix that. currently i am downloading the alt CD for 8.04 to see if that will help.

have downloaded and tried alts for 8.04 and gutsy still no luck. am thinking of trying another distro to see if i can find Microsoft free success

---

### Post by paramethis on 2008-12-20
heres my system 

asrock 939Dual-SATA2  [link to mobo]("http://http://www.asrock.com/mb/overview.asp?Model=939Dual-SATA2&s=939")

AMD Athlon64 4000+

2gb WINTEC ddr 400 ram

maxtor 40gb sata 3.0g/s HDD 

Western digital 500 GB sata 3.0g/s HDD 

BFG NVIDIA GeForce 7600 GT OC 256MB PCIe
_________________________________________________________________________

I have tried installing
ubuntu 8.10
ubuntu 8.10 alt
ubuntu 7.10 fiesty 
ubuntu gutsy
ubuntu 5.10 (had it laying around)
kubuntu 8.10
debian 40rs
fedora 10
_____________________________________________________________________
it freezes while attempting to format partitions on all ubuntus like below

partions formating

5%

creating ext3 file system for / in partition #1 of scsi1 (0,0,0)
________________________________________________________________________
I have also tried using Gpart and it just freezes claiming kernal sync error. I also tried DBAN which starts then pops up stuff over top its run screen and freezes.

Some one previously mentioned a jmicron controller which I have no idea what that is or how to fix it. Others have pointed out that since its sata it shouldn't read as scsi. 

What should I do besides breakdown spend $90 and go buy WinXP

---

### Post by p_quarles on 2008-12-20
Threads merged. Please create only one thread per topic -- it's much easier to help you that way, and it reduces the total number of threads that need to be managed.

---

### Post by sloggerkhan on 2008-12-20
I'd go through your bios options thoroughly. Sometimes they have interesting options for storage emulation or ACPI and such, and a variety of which, if set to unexpected choices, can cause unexpected problems for Linux.

---

### Post by kansasnoob on 2008-12-20
My first and best guess is a bad CD drive!

Look here:

[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

Beginning with figure 29!

---

### Post by paramethis on 2008-12-20
tried both hdds with other unplugged. used different cdrom drive. and bios settings are good.

---

### Post by sloggerkhan on 2008-12-21
if you have problems how do you know bios settings are good?

---

