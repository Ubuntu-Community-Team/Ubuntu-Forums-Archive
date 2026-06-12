---
title: "Ubuntu  im new to it and need help"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by balkrish999 on 2010-02-19
Hello, I am new to ubuntu and am a complete begginer and not a computer expert

i need some help and some guidence 

first, i have a laptop which cam with windows 7 64 bit version and has a 280gb hard drive, also when i go to my computer there another hard drive which is 12gb and its got my recovery part on it.

what i want to do is i want to keep my windows 7 and instal ubuntu 9.10 (on a duall bott i think so i get to chosse both os's at the start up.

how do i do this ?? i am confused at the ubuntu installtion on step 4, i dont know what to do and if im doing it right  please help me, what do i click on if i want a dual boot?  

thank you please help me :):):):): (if possible can you post screen shots on what i have to do )

---

### Post by hortstu on 2010-02-19
Hi,

I'm relatively new to this myself.  I'd try to walk you through it but I'm sure that I'd miss something.  So I'll give you this link and bump your thread back to the top.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

How new is this computer?  Brand spanking new with no personal data in it yet?  If so then it should be easy to partition the drive and install a dual boot.  That link up there should get you going.

---

### Post by drpjkurian on 2010-02-19
> **balkrish999 said:**
> Hello, I am new to ubuntu and am a complete begginer and not a computer expert

i need some help and some guidence 

first, i have a laptop which cam with windows 7 64 bit version and has a 280gb hard drive, also when i go to my computer there another hard drive which is 12gb and its got my recovery part on it.

what i want to do is i want to keep my windows 7 and instal ubuntu 9.10 (on a duall bott i think so i get to chosse both os's at the start up.

how do i do this ?? i am confused at the ubuntu installtion on step 4, i dont know what to do and if im doing it right  please help me, what do i click on if i want a dual boot?  

thank you please help me :):):):): (if possible can you post screen shots on what i have to do )

Hi
You can do this in a simple way

Step 1 Defragment your windows 7 by a defragmenter. This will save you from losing data

Step 2 Boot from live cd

Step 3 select the option install in continuous free space

You will get a dual boot

---

### Post by balkrish999 on 2010-02-20
hello can u help me please

when on the installation on step 4 i only get 2 options where the othere  one ????

i get the options
use entire disk
 specify partions manually (adbance)
BUT WHERE IS    THE     :    USE THE LARGEST CONTINUS FREE SPACE  OPTION?????

i want  a dual boot and i have windows 7 and i used that on disk management and cretesd a 30gb partion and i left it unallocated   so why dont i have the other option

---

### Post by thebigob on 2010-02-20
> **balkrish999 said:**
> hello can u help me please

when on the installation on step 4 i only get 2 options where the othere  one ????

i get the options
use entire disk
 specify partions manually (adbance)
BUT WHERE IS    THE     :    USE THE LARGEST CONTINUS FREE SPACE  OPTION?????

i want  a dual boot and i have windows 7 and i used that on disk management and cretesd a 30gb partion and i left it unallocated   so why dont i have the other option

This is in the specify partitions manually section. It its simple to use. Also bear in mind during this stage any changes you make will not take effect until you proceed to stage 5.

---

### Post by balkrish999 on 2010-02-20
ok if i do specify manullay how do i do it please help me tell me what to do thern thanks

---

### Post by atomizer on 2010-02-20
The Vista uses your whole HD probably.

You have to shrink the windows partition to make room for Ubuntu.

You need about 10 Gig for your system, a few Gig for Swap and an amount for /home (sort of documents and settings folder) Usually I give it 60 Gig (for movies and music) That would be 10+4+60 = about 75 Gig to free from your windows.

---

### Post by philinux on 2010-02-20
> **balkrish999 said:**
> ok if i do specify manullay how do i do it please help me tell me what to do thern thanks

Run the livecd. Then run gparted the partition editor in System>admin.

Post back here a screen shot of your partitions.

---

### Post by Easy Limits on 2010-02-20
Watch this youtube video.  It's a little dated but very accurate.

[http://www.youtube.com/watch?v=w8a-smrPlvE](http://www.youtube.com/watch?v=w8a-smrPlvE)

---

### Post by presence1960 on 2010-02-20
> **philinux said:**
> Run the livecd. Then run gparted the partition editor in System>admin.

Post back here a screen shot of your partitions.

philinux has the safest suggestion- let's see what you have before giving any specific advice. You can do what philinux says or from the ubuntu live cd go Applications > Accessories > Terminal and run in terminal ```
sudo fdisk -l
``` That is a lowercase L in -l

Post the output from that command or the screenshot philinux suggested.

It would be wise indeed to see your setup prior to proceeding.

Also I would use the windows disk management utility to shrink windows 7 C; partition rather than gparted. Defrag windows once or twice prior to resize. Turn off system restore until after resize.

---

