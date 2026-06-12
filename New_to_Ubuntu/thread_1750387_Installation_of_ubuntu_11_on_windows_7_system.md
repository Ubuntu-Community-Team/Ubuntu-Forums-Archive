---
title: "Installation of ubuntu 11 on windows 7 system"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by gigabyte rookie on 2011-05-05
installed ubuntu from iso disk and it ask to use free space i click it and it erased complete disk.  reinstalled windows 7 and am ready to give it another try.  How do i find disk partitioning for ubuntu?  I am a lil reserved to try the install again without the aid of someone who knows what they are doing. need step by step instructions on how to install without wiping my win7 OS again. please help any help will be greatly appreciated. By the way have read all threads about dual booting systems and they are not making any since to me. anxiously waiting to try ubuntu out.   Thank you Roniie

---

### Post by oldfred on 2011-05-05
Those of us who want more control partition in advance and use manual install. Then we avoid the issues of the automatic going off and doing something we do not want. It also gives us the advantage of creating a separate /home. Herman has lots of detail in his install guides. I think they still are based on 10.10, but slight screen differences should not confuse (too much:))

Does you system already use all 4 primary partitions? Post this from liveCD terminal.
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

```
sudo fdisk -lu
```Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by computerandu on 2011-05-05
What is the size of your hard disk?

How many drives do you have? (on Windows)?

While installing Ubuntu choose manual format. Don't touch the drive where Windows is installed. At least have one more drive in NTFS format. Create / drive in ext3 or ext4 format. 2-4 GB of swap and rest in ext3-4 /home.

Here is a link to help you...

[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

---

### Post by gigabyte rookie on 2011-05-05
> **computerandu said:**
> What is the size of your hard disk?

How many drives do you have? (on Windows)?

While installing Ubuntu choose manual format. Don't touch the drive where Windows is installed. At least have one more drive in NTFS format. Create / drive in ext3 or ext4 format. 2-4 GB of swap and rest in ext3-4 /home.

Here is a link to help you...

[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)
 i have 1 drive designated C on a 2 tb hd with 928.91gb nonallocated space.  where do i find the partition manger for ubuntu to create / drive in ext4 format? thanks Ronnie

---

### Post by oldfred on 2011-05-05
If you use manual install, you can create partitions as part of the install. With that much unallocated, I would still leave a lot unallocated. Allow for extra data and root partitions. The extra root partitions of 25GB let you test alpha or beta Ubuntu or try out other installs. Lots of room for data. Some should be NTFS to share data with windows.

But it is gparted and gparted is on the LiveCD.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by gigabyte rookie on 2011-05-05
> **oldfred said:**
> If you use manual install, you can create partitions as part of the install. With that much unallocated, I would still leave a lot unallocated. Allow for extra data and root partitions. The extra root partitions of 25GB let you test alpha or beta Ubuntu or try out other installs. Lots of room for data. Some should be NTFS to share data with windows.

But it is gparted and gparted is on the LiveCD.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
  Thanks Fred for the help heres a little insight to my system
gigabyte mobo model ex58-4dup
2 tb hd
12 gb corsair ddr3 ram
running 2-way sli with nvidia 9800gt gpu's
liduid cooled I7 920 CPU

---

### Post by gigabyte rookie on 2011-05-05
OK the light bulb just came on ...i should get the partition menu when installing ubuntu 11 well i dont will make a new iso copy and retry will inform of the outcome Thanks Ronnie

---

### Post by oldfred on 2011-05-05
I only have one 9600gt nVidia, but have had to do this for most installs. Natty worked a bit better but you may have to add some parameters.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

---

