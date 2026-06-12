---
title: "Partitioning and RAID 0 (And another hard drive?)"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by Captain Man on 2010-09-09
Okay guys, I'm about to put Ubuntu on my new computer. I've hesitated because I wanted a "clean" windows system but... I just can't resist. I like Windows but I also like Ubuntu and whatever. Why does all this matter anyways?

Sorry. But here's my questions: As of now, I have two 1TB WD HDDs in RAID 0. Can I create a partition on the virtual drive without unRAIDing them? I don't have a way to back up my data is why I don't want to unRAID them.

However... I found a 160GB Samsung HDD which could fit all my data almost perfectly! But for some reason I can't access the drive, as in it is connected and spinning and stuff but not under "my computer." Any ideas? I couldn't care less about this HDD though if you can safely create partitions on RAID 0 though.

That's all. I know it's a lot but I know how helpful the Ubuntu community is, so thank you so much in advance everyone!

---

### Post by seawolf167 on 2010-09-10
First of all I'd ***very highly ***suggest backing up everything on your disks. Either backing up the data to another drive, or imaging the drive with the OS. Raid 0 is striping only, no mirroring or parity. So backups are necessary.

For your new disk, you can use gparted from within Ubuntu to initialize, convert and partition the drive however you'd like. If you are in Windows, right-click "My Computer", select "Manage", then "Disk Management". You'll be prompted to initialize and convert.

You can also use gparted on a [Ubuntu] live cd to edit your partitions in the 2 TB raid, or if you want to use a Windows program from within Windows you can use one called "Disk Director Suite" by Acronis.

After the drive is partitioned go ahead and install Ubuntu (assuming you will be installing alongside Windows for a dual boot system).

There are a ton of guides to installing Ubuntu on your system (just Google it), just keep in mind that with any computer changes, and especially when editing your disk partition information, backups are extremely important!

---

### Post by Captain Man on 2010-09-10
Hey thanks so much Seawolf! I was about to try and get hard drive jumpers to set that up as a slave but you saved me some time!

Yes, I understand back ups are necessary but the computer is still pretty new so I haven't worried about it yet, but have no fear, I am in the process.

One problem down, three to go.

1) How do I back up windows? If i just drag and drop my C:\ drive to the B:\ drive (the one I just got working) won't the license not work? Should I seek out a program? The Windows back up only works with disks, I don't have enough DVDs and honestly don't want to use like 40.

2) I was going to use GParted but after the LiveCD showed the purple screen with the keyboard and the assistive technologies logo and the load bar dots the screen went black. It was still working though because I pressed buttons and heard sounds. My video card is an ATI 5970 if that helps.

3) Not really a 'problem' just clarification. So I *do not* have to unRAID my RAID volume and create the partitions on each disk separately?

Thanks again in advance!

---

### Post by seawolf167 on 2010-09-13
Sorry for the late reply, I was out of town for the weekend.

1. There are a couple ways you can backup windows (for free).

One way is to use NTBACKUP within windows itself (Start -> Run -> NTBACKUP), then backup everything.

Another (and preferred way) is to burn yourself a Clonezilla cd and use that to image your computer to another hard drive ([http://clonezilla.org/](http://clonezilla.org/)). You may need to select the option that says something like "use another mode of clonezilla", then select "vga normal".

With Clonezilla it will only backup full sectors and skip the empty ones, so if for example the drives only contain 100 GB of data, only a 100 GB image will be made (not a 2 TB image)

2. Since your drives are NTFS formatted, you may want to skip GParted (since it wasn't working for whatever reason) and just partition from within Windows. Use Partition Magic, Disk Director Suite, or the Linux SystemRescueCD ([http://www.sysresccd.org/Index.en.php](http://www.sysresccd.org/Index.en.php)) etc. to do that.

3. RAID-0 is just a method to improve read/write times by interleaving drives together. There is no reason that you shouldn't (or can't) partition your drive(s).

---

### Post by Captain Man on 2010-09-13
Okay, I am finally backing up my drive, I've been through hell and back to do this... I'll never upgrade to a new version of Windows again!

Anyways, I think I might end up trying out wubi instead of bothering with partitions and see how it works. As far as I'm concerned I'm going to consider this thread answered, thanks for all the help, seawolf167!

---

