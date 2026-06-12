---
title: "Installing Ubuntu 10.10 from scratch (new hardware)"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by randalledward on 2011-03-11
Hi,
I am brand new here. I am somewhat computer literate and used to work with Unix (10 years ago). I just bought a new (no OS) computer system and want to run Ubuntu exclusively (no Windows - YAY! i hope).
Just looking to get off on the right foot with system setup.
 
Want to install Ubuntu 10.10 from CD (I will download and burn)
on a Athlon II X2 250 / 4gB ram / Seagate 1TB HD
 
I am asking questions beforehand because I won't have handy internet access until the new system running.
 
My questions are how should I format HD? Use Seagate tool? Partitioning? (root, usr, swap?) File systems?
 
Are there tools for the above operations on the Ubuntu CD?
 
After I get the drive properly formatted/partitioned I am assuming that I can plug in the CD and get started with the install via prompting.
 
After system is operational I will be trying to connect to internet via DSL modem to Verizon.
 
Any feedback is greatly appreciated. Sorry if I rambled.

---

### Post by randalledward on 2011-03-11
also, I was planning on loading the 64 bit version, is this good?

---

### Post by TeoBigusGeekus on 2011-03-11
First of all, before you do anything, download both the 10.10 AND the 10.04 cds and test them (via live session) on your system. Check everything, internet connection, sound, graphics, etc.
There is a debate about whether Maverick was a successful release, that's why I'm proposing you to give Lucid a shot as well. 10.04 is also a long term release (support for 3 years).

Once you decide on installing ubuntu, boot up with the live cd and choose install ubuntu.
The installer is pretty straightforward, but pay attention to the partitioner.
Choose manual configuration and create 3 partitions:
Partition 1: ~1gb - use it as swap (you shouldn't ever need it with 4gb of ram, but just in case...).
Partition 2: ~20-30gb - use it as your root partition: ext4 format - / mount point
Partition 3: The rest of your hd - use it as your home partition: ext4 - /home mount point

If you were able to install linux 10 years ago, you will be amazed with the simplicity and ease of use of the ubuntu installer. Welcome aboard!

---

### Post by metalf8801 on 2011-03-11
> **randalledward said:**
> Hi,
I am brand new here. I am somewhat computer literate and used to work with Unix (10 years ago). I just bought a new (no OS) computer system and want to run Ubuntu exclusively (no Windows - YAY! i hope).
Just looking to get off on the right foot with system setup.
 
Want to install Ubuntu 10.10 from CD (I will download and burn)
on a Athlon II X2 250 / 4gB ram / Seagate 1TB HD
 
I am asking questions beforehand because I won't have handy internet access until the new system running.
 
My questions are how should I format HD? Use Seagate tool? Partitioning? (root, usr, swap?) File systems?
 
Are there tools for the above operations on the Ubuntu CD?
 
After I get the drive properly formatted/partitioned I am assuming that I can plug in the CD and get started with the install via prompting.
 
After system is operational I will be trying to connect to internet via DSL modem to Verizon.
 
Any feedback is greatly appreciated. Sorry if I rambled.

The Ubuntu CD can formate the hard drive for you. Do you know if your new hard drive has the new 4k (4096) sectors or the old 512 bytes sectors? That will affect how you formate the drive. 

Make sure you connect to your modem using an Ethernet cable not a usb cable.

---

### Post by oldfred on 2011-03-11
I am not familar with Athlon II X2 250 based systems. Most new systems are 64 bit. But both CPU & motherboard chips have to support 64 bit.

Gparted is on liveCD and you can use it to partition hard drive. I used to use CD, but now use USB flash drives. If your system lets you boot USB devices flash is a good way & reusable.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by randalledward on 2011-03-11
I would like to thank everyone for replying to my questions so quickly! I now have an idea of where to start. For the person who asked about my HD sectors, I still don't know - its a Seagate Barracuda 7200.12 ST31000528AS 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s. (still in box)

---

### Post by randalledward on 2011-03-11
Sorry for so many follow ups. But is sounds like sound advice to go with 10.04 for now - thanks.

---

### Post by metalf8801 on 2011-03-11
> **randalledward said:**
> I would like to thank everyone for replying to my questions so quickly! I now have an idea of where to start. For the person who asked about my HD sectors, I still don't know - its a Seagate Barracuda 7200.12 ST31000528AS 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s. (still in box)

According to [http://www.amazon.com/Seagate-Barracuda-7200RPM-Internal-ST31000528AS-Bare/dp/B00272NHOK](http://www.amazon.com/Seagate-Barracuda-7200RPM-Internal-ST31000528AS-Bare/dp/B00272NHOK) the hard drive has the old 512 sectors so you won't have to do anything. Not that Seagate clearly says that on their website or on newegg. 

Good luck I hope everything goes well for you and please post how things went when your done 
Dan

---

