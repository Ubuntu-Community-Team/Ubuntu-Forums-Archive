---
title: "Correct way to remove ubuntu??"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by rls53 on 2009-06-14
Is there a proper way to remove UBUNTU from a virgin install on a new hard drive.
Afraid to just use DBAN as this may have lead to a failed attempt on previous HD.
When I installed UBUNTU I did enter a user name and simple password.
Thanks:)

---

### Post by Raistlin355 on 2009-06-14
You will have to format in some way, DBAN is the most common way I think.  I have used DBAN for years and I doubt it lead to the hard drive failure you talked about unless the drive was already failing.  Make sure you check your S.M.A.R.T logs before you use it.  BTW why do you wanna get rid of Ubuntu?

---

### Post by Amilo1718 on 2009-06-14
for the one who likes the dos prompt: format c:\ ??? :KS

---

### Post by Raistlin355 on 2009-06-14
> **Amilo1718 said:**
> for the one who likes the dos prompt: format c:\ ??? :KS

Yes that is the correct syntax, however I don't think format comes with windows anymore......

---

### Post by Amilo1718 on 2009-06-14
> **Raistlin355 said:**
> Yes that is the correct syntax, however I don't think format comes with windows anymore......

d***n... not back in the w7 shell? no new 'viruses' in the old programming languages?

---

### Post by Raistlin355 on 2009-06-14
> **Amilo1718 said:**
> d***n... not back in the w7 shell? no new 'viruses' in the old programming languages?

Sorry I'm afraid I don't understand what your asking

---

### Post by halitech on 2009-06-14
couple of options:

1. boot from your windows install cd and tell it to use the entire drive.

2. use the live cd to simply remove the partitions

3. grab a win98 boot disk (bootdisk.com) and use that to boot and format the drive

4. if the motherboard supports it, do a low level format from the bios.

---

### Post by Amilo1718 on 2009-06-14
> **Raistlin355 said:**
> Sorry I'm afraid I don't understand what your asking

lol

---

### Post by theozzlives on 2009-06-14
Just use partition Editor on the live CD and delete your Linux partitions.

---

### Post by lisati on 2009-06-14
> **halitech said:**
> 
3. grab a win98 boot disk (bootdisk.com) and use that to boot and format the drive

Don't forget to take care of grub with ```
fdisk /mbr
```

OP: as you may have already figured out, there are multiple answers

---

### Post by Raistlin355 on 2009-06-14
> **theozzlives said:**
> Just use partition Editor on the live CD and delete your Linux partitions.

Just to add you can delete the partitions, but unless you make new partitions and write over the old data, it will remain.  So if you were to sell or give the hard drive to someone else the could retrieve your old data.

---

### Post by halitech on 2009-06-14
> **lisati said:**
> Don't forget to take care of grub with ```
fdisk /mbr
```

OP: as you may have already figured out, there are multiple answers

good point, although the OP hasn't stated why he wanted it wiped so hard to say just how extreme we need to go

---

### Post by camper365 on 2009-06-14
If you restart your computer in a windows xp recovery disk, and select recover your system using the recovery console (press r), then you will be given a DOS prompt. At that point, select your Windows installation (probably 1, just type 1 at the prompt) then type the Administrator password. After that, you will be given a DOS prompt. Type "fixmbr" (without the quotes) and say continue. It will tell you you have a bizzare MBR so it may make partitions inaccesable. It doesn't matter.
After that, you will be able to boot up Windows.
However, you will not have full access to the entire disk. What you do is boot up into the Ubuntu livecd and go to GParted (System -> Administration -> Partition Editor) and delete the Ext3 Partitions and the Swap partition. Then resize your NTFS partition to fill up the entire disk. Reboot and "enjoy" your Windows installation.

---

### Post by rls53 on 2009-06-14
Please elaborate on grub.
Thanks

---

### Post by Amilo1718 on 2009-06-14
> **camper365 said:**
> If you restart your computer in a windows xp recovery disk, and select recover your system using the recovery console (press r), then you will be given a DOS prompt.
is there in the MS OS section no such thing as a live-cd or a bootable setup-cd ?

---

### Post by rls53 on 2009-06-14
I am in partition editor however dev/sda2 and dev/sda5 are locked and can not delete.
I am using Live CD. I am getting message that the volume is mounted even with live CD.
Thanks

---

### Post by lisati on 2009-06-14
> **rls53 said:**
> Please elaborate on grub.
Thanks

"grub" is what Ubuntu uses to let you choose between different operating sytems when you first power up your computer. If you just take Ubuntu off your system but forget to take care of grub, it *can* get confused and refuse to let you start Windows.....

---

### Post by Bradtek on 2009-06-14
> **rls53 said:**
> I am in partition editor however dev/sda2 and dev/sda5 are locked and can not delete.
I am using Live CD. I am getting message that the volume is mounted even with live CD.
Thanks

Unmount them

Would also help if you said what you want to do with the hard drive.
If you're going to reinstall Ubuntu or Install windows or throw it away ?

---

### Post by rls53 on 2009-06-14
Sorry about that. I want to start using Ubuntu but want to put it on another HD. I need to clear the new Seagate 60 for use in another laptop only running Windows but now that it is locked I cant access it to remove the virgin Ubuntu install. I love the Ubuntu OS but I need a laptop with Windows also and I only have 2 HDs. I installed the OS on the wrong HD to start with,my bad.
I am stuck in commands that are new to me with the current /dev/sda and dev/sda2 mounted even with the live cd. Am in partion editor at the monent and was able to remove largest partition.
Stuck

---

### Post by Bradtek on 2009-06-14
Put the drive in the other Laptop and Use the Windoze Install CD/DVD to partition/format
Windoze should happily get rid of Ubuntu

Or as I previously said .... Unmount the drives when using the Live CD
then partition.

---

### Post by arizonagirl11 on 2009-06-14
I also must remove ubuntu. Ubuntu is currently the only thing installed on my PCs. Unfortunately, I mainly use my PC for Second Life, and Second LIfe does not work properly with Ubuntu. Therefore, I wish to go back to Windows. I attempted putting the windows disk in, but it tells me that the drive is in the wrong format, and Windows cannot be installed. I attempted fdisk, that won't work, I also attempted to destroy the particians. nothing will work for me. Is there any other ideas how I can get the drive in the right format to run Windows? Thanks!
Kimmy

---

### Post by lisati on 2009-06-14
> **arizonagirl11 said:**
> I also must remove ubuntu. Ubuntu is currently the only thing installed on my PCs. Unfortunately, I mainly use my PC for Second Life, and Second LIfe does not work properly with Ubuntu. Therefore, I wish to go back to Windows. I attempted putting the windows disk in, but it tells me that the drive is in the wrong format, and Windows cannot be installed. I attempted fdisk, that won't work, I also attempted to destroy the particians. nothing will work for me. Is there any other ideas how I can get the drive in the right format to run Windows? Thanks!
Kimmy

You might want to use gParted on the Ubuntu Live CD to format the Ubuntu partition as NTFS or some other scheme that Windows recognizes then use the Windows installation disk to do the installation.

---

### Post by H2SO_four on 2009-06-14
> **lisati said:**
> You might want to use gParted on the Ubuntu Live CD to format the Ubuntu partition as NTFS or some other scheme that Windows recognizes then use the Windows installation disk to do the installation.

+1 or use DBAN to nuke the HDD.

---

### Post by arizonagirl11 on 2009-06-14
Thank you so much! The GPart seemed to do the trick! Maybe it will let me keep ubuntu too. I hope!

Kimmy

---

