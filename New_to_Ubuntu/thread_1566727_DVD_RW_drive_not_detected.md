---
title: "DVD RW drive not detected"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by ursveeresh on 2010-09-02
Hi

Just installed Ubuntu 10.04 Dual boot with Windows XP using wubi, I used the iso image for this installation. (32-bit Desktop edition)

Installation went well, except that my DVD RW wont show up any where on ubuntu. I am not even sure if this is detected. 

DVD RW drive works fine in Win XP. Below info might help in troubleshooting this issue:

sudo lshw -C disk
[sudo] password for veeresh: 
  *-disk                  
       description: ATA Disk
       product: HDS728080PLA380
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: PF2O
       serial: PFDB32S6S9HJUM
       size: 76GiB (82GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=f858f858
  *-disk
       description: ATA Disk
       product: ST3250620A
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 9QE7E279
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=5f0285ea

dmesg|less is attached.

Please guide me in resolving this.

--Veeresh

---

### Post by llamabr on 2010-09-02
In what way isn't it detected?  That is, what isn't it doing?  If you put in a dvd, does it play?  If you put in a blank dvd, does it open the burn dialogue?  pop one in, and then send the output of dmesg

---

### Post by ursveeresh on 2010-09-03
> **llamabr said:**
> In what way isn't it detected?  That is, what isn't it doing?  If you put in a dvd, does it play?  If you put in a blank dvd, does it open the burn dialogue?  pop one in, and then send the output of dmesg

Thank you for replying. here is more info..

when I insert a DVD - light blinks for 5 sec and then goes off - nothing shows up on the screen. Samething happens with a blank DVD/CD.

filesystem has these folders  - /media/floppy0 and /media/floppy (soft link I guess)  no dvdrom or cdrom folder. I do see /cdrom.

attached dmesg for your reference.

---

### Post by anewguy on 2010-09-03
Is this an external drive and connected via USB?

Dave

---

### Post by ursveeresh on 2010-09-23
Hi
 
This is IDE LG DVD RW - this works fine in Windows XP pro.
 
when a CD/DVD is inserted, light blinks for a while and nothing shows up on screen, and nothing is mounted in /media or /mnt
 
Thanks
ursveeresh

---

### Post by mastablasta on 2010-09-23
it might be because you are using Wubi. 
 
Form th einterenet Wubi does get sometimes confused with drives (or at least used to).
 
What happens if you boot from CD (into LiveCD session) and select to try the system without installing it?
 
Wubi is not really a propper dual boot, but can be used to test out the system a bit (similar to live session). Also it is (maybe) not so stable and has some issues that propper install won't have.

---

### Post by ursveeresh on 2010-09-23
Thanks for quick reply, Yes I installed Ubuntu 10.04 using wubi (dual boot with win xp).
 
When I try to boot from Live CD (burned from buntu i386 32 bit.iso).. I get the following error
 
(initramfs) Unable to find a medium containing a live file system 
 
and installation stops. 
 
Is there a workaround for this?
 
Thanks 
Veeresh

---

### Post by rajeev1204 on 2010-09-23
Hi

Can you open up your system and see if your cd drive is connected as master or slave ? The master / slave jumpers diagram will be on the cd drive sticker on top, set it to master , its very simple. have to change the small jumper caps.




rajeev

---

### Post by wkhasintha on 2010-09-23
I got this problem although I have done a full installation. not a wubi that is.

---

### Post by rajeev1204 on 2010-09-23
> **rajeev1204 said:**
> Hi

Can you open up your system and see if your cd drive is connected as master or slave ? The master / slave jumpers diagram will be on the cd drive sticker on top, set it to master , its very simple. have to change the small jumper caps.

I had filed a report here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425756](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425756)  but though its not solved, i dropped into #ubuntu-kernel  on irc and the folks there helped me solve it. My cd drive was set to slave instead of master and ubuntu had trouble detecting it.


rajeev

.....

---

### Post by ursveeresh on 2010-09-24
DVD RW was connected as primary slave - now I have changed the jumper and set to Primary Master (confirmed in BIOS setup)

Still same.. DVD RW is not detected or mounted when CD/DVD is inserted.

I think this is maybe due to wubi installation. I would like to do a full installation with a live CD however installation fails with
(initramfs) Unable to find a medium containing a live file system 

Please help fixing this. I dont want to use Windows XP on my Desktop anymore.

---

### Post by ursveeresh on 2010-09-24
Hi

Removed wubi install and did a full installation using a USB stick (as I could not use the DVD RW, as it fails mounting the live file system).

Still the same.. DVD RW wont show up filesystem and does not mount when a CD/DVD is inserted.

lschw -C disk - does not list the DVD RW 

when desktop startups up I can see the DVD RW in BIOS setup, and after Grub loads ubuntu it does not show up anywhere.

I guess DVD RW drivers may need to passed to kernel to resolve this, or may be some kernel options to setup in grub. 

Please advise on this.

Regards
Veeresh

---

### Post by CharlesA on 2010-09-24
It shouldn't need any drivers for a optical drive. Is there anything like cdrom or dvd listed in /dev/ ?

---

### Post by rajeev1204 on 2010-09-25
> **ursveeresh said:**
> Hi

Removed wubi install and did a full installation using a USB stick (as I could not use the DVD RW, as it fails mounting the live file system).

Still the same.. DVD RW wont show up filesystem and does not mount when a CD/DVD is inserted.

lschw -C disk - does not list the DVD RW 

when desktop startups up I can see the DVD RW in BIOS setup, and after Grub loads ubuntu it does not show up anywhere.

I guess DVD RW drivers may need to passed to kernel to resolve this, or may be some kernel options to setup in grub. 

Please advise on this.

Regards
Veeresh


Hi,

Iam assuming this dvd drive works in windows .

Anyways, what are you trying to play in the drive ? The drive wont show up unless some medium is inserted. that is normal .

---

### Post by ursveeresh on 2010-10-04
Hi

Nothing happens when Cd/DVd is inserted (light blinks for a while). I installed Ubuntu 10.04 with a USB stick as DVD RW was not detected.

Can someone Please help me how to load CD/DVD drivers to existing kernel or may be I will try new install by manually loading CD/DVD drivers.

Note:This is LG standard DVD RW, This works fine in Win XP.

Thanks
Veeresh

---

