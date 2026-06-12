---
title: "Advice please"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by wezzie1954 on 2010-12-12
Hi. I'm running Maverick on my main hard drive and wish to buy an external USB 2 hd on which I intend to run Ubuntu Studio, Cakewalk guitar tracks pro and file backup for my main hd. Obviously I'm looking at a three way partition here particularly as my Cakewalk software will be running off Windows XP.
Any Ideas about how I should approach this project would be most welcome. Thanks in advance.

---

### Post by cariboo on 2010-12-12
It would probably be easier for you to setup a Windows (NTFS) partition in XP, leaving free space for any ext4 partitions you may want to setup, You can then install Ubuntu to the free space on the drive.

---

### Post by toupeiro on 2010-12-12
If I am understanding correctly, you have a drive with meercat and xp partitions, then a second drive which you want a backup partition and an ubuntu studio install.  If so, proceed, if not, ignore:


I would recommend using gparted on the usb drive and create your backup partition first, and when doing so, label it in gparted as such (such as /mnt/backup as an example)  using ext4 should be fine.  Make it as large as you think you will need.

When you're doing the ubuntu studio install, do not let it automatically format the drives, and select the manual format options.  You should see all your drives, and on one of them, you should see the /mnt/backup partition you created.  This is the drive you will want to install studio on.

On this drive you will want to create no less than 2 partitions.  a root partition (/) and a swap partition. Create the swap partition first. A general rule of thumb I use for desktops to determine the size of the swap partition is to double the amount of RAM you have in the system.  That said, for an average desktop, I cannot see much value in going larger than 12GB.  If you know you only have 1GB of RAM, you might consider doing more than double your swap, as it will allow you to run more programs/process more data, but with a performance penalty.  

Create the / partition with the remaining amount of free space on that drive if thats what you desire (I would not recommend making it any smaller than 8GB unless you are doing a more advanced config and moving /tmp and /home off to other drives.)

Once installed, the easiest thing to do would be to go into your BIOS and tell your system to boot to your ubuntu drive, because grub will have detected your existing windows and meerkat installations and they should be listed in the grub menu.

For further details on this, I would recommend you refer to the ubuntu guide for 10.10: [http://ubuntuguide.org/wiki/Ubuntu:Maverick](http://ubuntuguide.org/wiki/Ubuntu:Maverick)

---

### Post by -kg- on 2010-12-12
I have a bit of a caveat:

> Once installed, the easiest thing to do would be to go into your BIOS and tell your system to boot to your ubuntu drive, because grub will have detected your existing windows and meerkat installations and they should be listed in the grub menu.

I would certainly not suggest a typical installation of this type on an external drive unless you're OK with it being necessary to have this external drive connected to your system in order to boot.  If you allow Ubuntu Studio to install without changing the default GRUB installation, it will install on your sda drive and, since Ubuntu Studio's subsequent GRUB stages will be on the external drive in the /boot directory, it will be necessary to have that drive connected in order for any OS on your computer to boot.

As toupeiro suggested, I would use the Manual partitioning selection to install but, at the very last screen where you see all the installation information, you will notice a button marked "Advanced."  This button leads you to a screen where you will be able to indicate where GRUB is to be installed.  You will want to either install it to the external drive's MBR (suggested)...that likely being sdb (if you only have one internal hard drive)...or to the partition itself (sdb1, sdb2...whatever Ubuntu Studio's root partition is...pay attention to where you're installing it).

If you install it to the MBR of the external drive, you will make that drive bootable to any computer that is able to boot to a USB device, which makes it the suggested method.  Installing it to the root partition itself will work if you don't anticipate the need to boot it separately.

Then boot back into Ubuntu on the main hard drive (with the external drive connected, of course) and once there, pull up a terminal and execute the command:

```
sudo update-grub
```

This will detect the installation on the external drive and include it in the GRUB menu list on your computer.  If you have installed U.S.'s grub in the external's MBR, you can also boot from that, assuming that your computer can boot to a USB device.  Most of the newer ones can.

This works perfectly and doesn't tie the external to your computer in order to boot any OS at all.  I have a similar setup here on my external.

Another caveat with this type of installation...every time you upgrade your U.S. kernel you will need to once again run update-grub from your main Ubuntu's terminal.  It will update its own GRUB automatically, but not the GRUB that you generally use to boot.  It's not a major problem, though, and none at all if you choose to boot to U.S. by booting to the external device itself.

<Edit>  As an addendum:

> If you know you only have 1GB of RAM, you might consider doing more than double your swap, as it will allow you to run more programs/process more data, but with a performance penalty.

I'm sure the OP will know this, but with certain aspects of Ubuntu Studio, you cannot afford many "performance penalties."  Ubuntu Studio is shipped with an "rt" (real time) kernel and does not include NM (network manager) as it interferes with certain aspects of sound recording and processing.  I don't know that he would be able to afford performance penalties incurred with a larger swap size (as matter of fact, this is the first I've heard of the issue).

It all depends on for what the OP is going to use U.S. for, however.  If it's recording, then he can't afford the penalties.  I get by fine with a 1 1/2 X swap partition size.

---

### Post by toupeiro on 2010-12-14
> **-kg- said:**
> I have a bit of a caveat:



I would certainly not suggest a typical installation of this type on an external drive unless you're OK with it being necessary to have this external drive connected to your system in order to boot.  If you allow Ubuntu Studio to install without changing the default GRUB installation, it will install on your sda drive and, since Ubuntu Studio's subsequent GRUB stages will be on the external drive in the /boot directory, it will be necessary to have that drive connected in order for any OS on your computer to boot.

As toupeiro suggested, I would use the Manual partitioning selection to install but, at the very last screen where you see all the installation information, you will notice a button marked "Advanced."  This button leads you to a screen where you will be able to indicate where GRUB is to be installed.  You will want to either install it to the external drive's MBR (suggested)...that likely being sdb (if you only have one internal hard drive)...or to the partition itself (sdb1, sdb2...whatever Ubuntu Studio's root partition is...pay attention to where you're installing it).

If you install it to the MBR of the external drive, you will make that drive bootable to any computer that is able to boot to a USB device, which makes it the suggested method.  Installing it to the root partition itself will work if you don't anticipate the need to boot it separately.

Then boot back into Ubuntu on the main hard drive (with the external drive connected, of course) and once there, pull up a terminal and execute the command:

```
sudo update-grub
```

This will detect the installation on the external drive and include it in the GRUB menu list on your computer.  If you have installed U.S.'s grub in the external's MBR, you can also boot from that, assuming that your computer can boot to a USB device.  Most of the newer ones can.

This works perfectly and doesn't tie the external to your computer in order to boot any OS at all.  I have a similar setup here on my external.

Another caveat with this type of installation...every time you upgrade your U.S. kernel you will need to once again run update-grub from your main Ubuntu's terminal.  It will update its own GRUB automatically, but not the GRUB that you generally use to boot.  It's not a major problem, though, and none at all if you choose to boot to U.S. by booting to the external device itself.

<Edit>  As an addendum:



I'm sure the OP will know this, but with certain aspects of Ubuntu Studio, you cannot afford many "performance penalties."  Ubuntu Studio is shipped with an "rt" (real time) kernel and does not include NM (network manager) as it interferes with certain aspects of sound recording and processing.  I don't know that he would be able to afford performance penalties incurred with a larger swap size (as matter of fact, this is the first I've heard of the issue).

It all depends on for what the OP is going to use U.S. for, however.  If it's recording, then he can't afford the penalties.  I get by fine with a 1 1/2 X swap partition size.

I'm not erring to the side of performance assumptions and "what the OP knows", I'm outlining possibilities.  With 1GB of RAM, they shouldn't be running studio, but not everyone has the perfect storm for audio..  Performance penalty > no functionality because no memory left.

Either way, hope it works for you.

---

### Post by wezzie1954 on 2010-12-15
Many thanks for your input everyone. I've now gone from a state of clueless to information overload :D. Thing is, I now have some ideas to work with! Thanks again.
BW Paul

---

