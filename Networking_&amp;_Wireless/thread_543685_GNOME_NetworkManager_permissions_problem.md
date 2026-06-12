---
title: "GNOME NetworkManager permissions problem?"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by johnnyb01 on 2007-09-05
I did a very messy thing when partitioning my hard drive, and ended up copying an existing Feisty install onto a new partition and trying to boot it. After a day or two of headaches getting the drive to mount and GRUB to work, I can finally log into my GNOME session and almost everything works right. One thing that doesn't is the NetworkManager applet. It spins and spins and never connects to anything (and also never admits failure). The network is fine -- if I disable the applet and do 'ifconfig' and 'dhclient' on my device, I get a normal, usable connection. My guess is that there's a temp file or some other file that the applet is supposed to read or write, that it can't. That has been a problem with several other programs, because when I copied the partition some of those things got screwed up (e.g., /tmp was not world-writable, which initially prevented GNOME from starting at all). Short of browsing the source code, is there any way to find out (or does anybody happen to know) what files the NetworkManager needs in order to operate correctly? Does it output a log somewhere that would tell me why it's hanging?

---

### Post by johnnyb01 on 2007-09-05
Oh, in case it matters, this is a 64-bit Feisty install.

---

### Post by oscarjd74 on 2008-06-20
By accident I screwed up file ownership and groups recursively on /. Luckily I had backed up my system partitions onto a spare disk not too long ago. Too fix it I booted into the backup, mounted my broken system on /mnt and recursively did 'chown -h $(stat -c %U:%G /path/file) /mnt/path/file', copying the owner/groups from my backup to my broken system. Except of course for those files that didn't exist on the backup. Nonetheless, everything ran smoothly...

...except for the NetworkManager. I seemed to have the same problem as johnny. I managed to fix it though. Probably too late for johnny by now but maybe someone else will benefit from this. Here's what I did:

1. I booted into my backup. If you don't have one, boot into the Live CD instead. That should work too. This got my internet connection up and running.

2. I mounted my partitions on /mnt, /mnt/usr, /mnt/var etc.

3. I did a 'chroot /mnt' to change the root dir.

4. I used aptitude (but synaptic should work too) to remove and reinstall the network-manager, dhcp3-client, dhcp3-common, dhcdbd, and wpasupplicant packages.

5. I rebooted into my system. Hurray, a functional NetworkManager!

6. As dhcbd had choked on its post-installation script I finished up with apt-get -f install.

Cheers,
Oscar

---

