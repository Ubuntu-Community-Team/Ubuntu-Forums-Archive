---
title: "Dual-boot - help understand Grub loader?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by deadmanschest on 2009-02-06
Hi all - new to Ubuntu and Linux. On a new laptop, preinstalled with Vista x64, I have partitioned the single disk and installed Ubuntu 8.10 on a second logical partition within the drive. The dual boot works fine, Vista64 and U8.10 64bit work fine. 

I have no concept of boot loaders, hdd architecture or anything else. I have uneasy concerns about what happens when I image my C:\ (Vista OS partition)or any other active or logical partition for backup purposes and have to restore an image. I wonder what happens if I choose to further partition my Ubuntu partition or move things around...I just generally worry about critical things that I don't understand...hehe.

In a nutshell, where is the Grub loader physically on the hdd? 

When I did a reinstall of U8.10 (I installed the 32 bit before I learned there was a 64bit, so just clean installed the 64bit) I let the boot loader config options stay at default and it said install to "hd0" - I assumed that meant at the beginning of the single hdd in the prime real estate. I assumed that it must affect my Vista installation on the 'primary, active, boot" first C:\ partition, but Vista thinks that all its boot up properties are just great..  The intial BIOS screen options and properties are all just fine..

So my partitions are all good, my Os's are all happy, I just want to understand a little about the Grub and so avoid buggerin' it up.....

Thanks

dmc

---

### Post by gettinoriginal on 2009-02-06
Maybe reading through this might help, you could also bookmark it for future reference  :p  Welcome to Ubuntu
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by hellion0 on 2009-02-06
In a nutshell, GRUB gets put on the Master Boot Record. If Vista was the only thing on your machine, then its bootloader goes there instead.

---

### Post by bumanie on 2009-02-06
Without doubt, one of the most informative sites about grub is [here]("http://users.bigpond.net.au/hermanzone/p15.htm") - it has virtually everything you'll ever need to know about grub.

---

### Post by deadmanschest on 2009-02-06
> **hellion0 said:**
> In a nutshell, GRUB gets put on the Master Boot Record. If Vista was the only thing on your machine, then its bootloader goes there instead.

Hi all - thanks gettinoriginal & bumanie for the links (& welcome), and hellion0 for the quote...

So I am correct if I (noob speaking) guess that the MBR is on the beginning of the single hdd, has something to do with the BIOS, and has no 'direct connection' to the Vista installation on the first primary partition...?

In other words, if I ghost image my Vista OS partition, that leaves my MBR with the Grub mods unaffected?

Please feel free to correct my assumptions...hehe...

Thanks!

dmc

---

### Post by carml on 2009-02-06
Yes,should be right.Feel free to post in the forum if you have got any problems.:)

---

### Post by deadmanschest on 2009-02-06
> **carml said:**
> Yes,should be right.Feel free to post in the forum if you have got any problems.:)

Hi carml, thanks. Thanks all - I read the first few paragraphs of the Grub links, but my eyes are glazing over....."run sudo ... crub...etc...."

:)Everything works fine, I am reading the .pdf of the Ubuntu Pocket Guide..and as long as Vista is happy and U8.10 are happy then no worries!

Thanks all

dmc

---

### Post by bumanie on 2009-02-06
The mbr is the first 512 bytes of a hard drive and it is where the bootloader instructions are held for the first stage of booting. It also contains the partition table. It does have a direct relationship to vista in as far as, the partition table will include the vista partition reference. If you ever have to reinstall vista, vista will overwrite grub in the mbr and only vista will boot (this can be fixed via the use of a live cd). What grub basically does is recognize the OSes on your hard drive and hands over to the bootloader of the OS you wish to boot ie vista's bootloader boots vista, grub boots linux - the second stage of the bootloader files are part of the OS. The mbr does not boot anything, it just has the information as to where instructions should be sent for the bootloader to do its job at the second stage. I hope this is clear enough - I don't think it is a very good explanation.

---

### Post by carml on 2009-02-06
On my PC Ubuntu is happy,Vista less ,because I don't use it so much since I installed Ubuntu.:)

---

### Post by deadmanschest on 2009-02-06
> **bumanie said:**
> The mbr is the first 512 bytes of a hard drive and it is where the bootloader instructions are held for the first stage of booting. It also contains the partition table. It does have a direct relationship to vista in as far as, the partition table will include the vista partition reference. If you ever have to reinstall vista, vista will overwrite grub in the mbr and only vista will boot (this can be fixed via the use of a live cd). What grub basically does is recognize the OSes on your hard drive and hands over to the bootloader of the OS you wish to boot ie vista's bootloader boots vista, grub boots linux - the second stage of the bootloader files are part of the OS. The mbr does not boot anything, it just has the information as to where instructions should be sent for the bootloader to do its job at the second stage. I hope this is clear enough - I don't think it is a very good explanation.

:D No bumanie, that's very good, "direct relation' was just my poor wording for 'its not part of the C:\ partition'. What's confusing to someone who has no idea of the guts of the machine (c'est moi) is that the partition tools give the impression that the first partition of the hdd is jammed bar tight up against the outside edge, and because of the supremacy of "C:\" in the windows world you kinda think that the C:\ must control everything...

I think now, when I first start up and my BIOS welcome screen comes off and offers me a 'first stage boot' menu (CD, hdd, others) thats all happening in RAM/chip before it gets to the MBR. By default I let it go to the 'second stage boot' and the MBR, as modded by Grub, gives me the OS' choices and defaults to U8.10...

(By the by, since I discovered imaging software (Acronis) years back I have never had to 'reinstall' windows...whew!)

Perfect sense, I think. Thanks!

dmc

---

### Post by deadmanschest on 2009-02-06
> **carml said:**
> On my PC Ubuntu is happy,Vista less ,because I don't use it so much since I installed Ubuntu.:)

:D Hehe - gotta admit, I just started using the Vista x64 this week... coming from years of win 9x on an old beater that served my needs fine...and I must say I'm liking it a lot...oops..

But I finally have the hdd capacity to add linux as dual boot OS, and I'm intrigued by the Ubuntu buzz and the concepts..

Cheers!. Thanks to all!

dmc

---

