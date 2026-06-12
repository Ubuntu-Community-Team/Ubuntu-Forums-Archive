---
title: "Want To Create Separate Boot Partition"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by tb75252 on 2011-06-18
I am using Ubuntu 11.04, 32-bit.  Not much of an expert with Linux.

I would like to install a different Linux distribution (probably Debian 6) side by side with my Ubuntu 11.04, thus creating a dual-boot system.

I did some research on the Internet and I've seen that some recommend that GRUB 2 be installed on its own partition as the best way to do this.  The two distributions would then need to be chainlinked in the new /boot partition.

I came across this link as a way of doing it:
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

Am I on the right track?

---

### Post by garvinrick4 on 2011-06-18
> Am I on the right track?Not really I think you should just use as is without a /boot partition Grub go's into
sda into the mbr (master boot record) and all is fine without seperate partition.
Just not needed really.
##I do believe Debian grub comes without os-prober to find other installs and put them
in grub. (not positive but have an install of Debian and think it was Debian that I had
to install os-prober.) Debian is a bit more difficult to install even believe I had to put my
intel network cards firmware on a flashdrive so Debian could install using installer.
Have to set up /etc/sudoers which in Ubuntu you do not have to. So be aware of some
differences in installing. Might have to google search around a bit to find some answers.
##After install use Ubuntu's install to boot from.

---

### Post by YesWeCan on 2011-06-18
> **tb75252 said:**
> Am I on the right track?
No.
What you probably would like to have is a Grub in its own partition that is independent of any OS. That would be really useful but that's not how Grub works.

Grub has to be "hosted" by one linux OS. It makes no difference whether you have a separate boot partition. So you have to decide which OS will host Grub and make sure you don't delete that OS or Grub won't work at all.

To modify Grub you have to boot the host OS. Then you use utilities that are run by this OS to make changes to Grub. Such as update-grub and grub-install.

The way I would recommend is to install Ubuntu and use it to host Grub. This is a default install. When you install Debian, don't let it install Grub again otherwise Debian will become the Grub host. To add the Debian OS to the Grub menu boot into Ubuntu and run update-grub which scans all your disks looking for bootable OSs.

---

### Post by srs5694 on 2011-06-18
> **YesWeCan said:**
> Grub has to be "hosted" by one linux OS.

It's true that GRUB is conventionally set up this way, but it doesn't have to be. You can set GRUB up in its own partition and then delete the auto-maintenance scripts in the OS you used to set it up. *You* will then be responsible for maintaining its menu when you upgrade kernels, add new OSes, etc. One of my systems is currently set up this way.

---

### Post by Jarramundi on 2011-06-18
interesting....

---

### Post by YesWeCan on 2011-06-19
> **srs5694 said:**
> It's true that GRUB is conventionally set up this way, but it doesn't have to be. You can set GRUB up in its own partition and then delete the auto-maintenance scripts in the OS you used to set it up. *You* will then be responsible for maintaining its menu when you upgrade kernels, add new OSes, etc. One of my systems is currently set up this way.

Technically true, but not suitable for the OPer who is "Not much of an expert with Linux".

A standalone version with automation tools and no need for custom MBR would be very useful. I wonder how hard it would be to code this?

---

### Post by amjjawad on 2011-06-20
Had 9 OS's installed once on my PC (one HDD) without a Separate /boot.

I think it's an old way and with GRUB2 one doesn't need that much.

---

### Post by srs5694 on 2011-06-20
> **YesWeCan said:**
> [quote=srs5694][quote=YesWeCan]Grub has to be "hosted" by one linux OS.It's true that GRUB is conventionally set up this way, but it doesn't  have to be. You can set GRUB up in its own partition and then delete the  auto-maintenance scripts in the OS you used to set it up. *You*  will then be responsible for maintaining its menu when you upgrade  kernels, add new OSes, etc. One of my systems is currently set up this  way.[/quote]Technically true, but not suitable for the OPer who is "Not much of an expert with Linux".[/quote]

It may not be suitable for the OP, but my post was meant as correction of misinformation. Just because a configuration might not be suitable for a given purpose is no reason to claim it's not possible. Even if the OP would be better off with a different configuration, somebody else reading the thread might be interested in it, and claiming it's not possible could confuse or unnecessarily deter such a person.

> A standalone version with automation tools and no need for custom MBR would be very useful. I wonder how hard it would be to code this?

You might look at [GRUB4DOS.](http://gna.org/projects/grub4dos/) I've not studied it in detail, but my impression is that it's designed for that sort of configuration.

---

