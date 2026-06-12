---
title: "Dual Boot Can't Find New Partition in Linux"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by dannistories on 2009-11-11
Folks,
  Here's my thing:
sudo fdisk -l
[sudo] password for dannis: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x322ca97f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       63283   508315616    7  HPFS/NTFS
/dev/sda2          120102      121602    12048384    7  HPFS/NTFS
/dev/sda3           63284      120101   456390585    5  Extended
/dev/sda5           63284      118877   446558773+  83  Linux
/dev/sda6          118878      120101     9831748+  82  Linux swap / Solaris

Partition table entries are not in disk order
 I used ext2 for windows to partition, and use GRUB to boot.  In Vista, I can see the L: drive and S: [linux swap] partitions I created, but where are they in Linux? I can see my HP drive and everything on it just fine, and my network drive. I want to get every data file off Vista and Linux onto a partition by themselves in case I have to reinstall Vista again [got yet another blue screen of death this morning - thank goodness for Ubuntu!!]

Went to ext2 for win site and I think I need to download a diagnostic, because when I try to look at L: or S: in Vista, it asks if I want to format. Is this because I don't have data there yet, or do I need to format L: in NTFS, or do I need to do the diagnostic?! I'm soooo confuuuuuuused!!

I used to speak UNIX at work, but that was before the GUI, and I forgot more than I ever learned from MAN. I think I got stupider as I got older. I hate Vista, but have to keep it if I want sound [sound chips in Intel chipset - will Intel ever play ball with Tux??]. Video is GForce [it's written down someplace in a file]. My PC is an IQ 506t with a touchscreen.

I tried to upgrade to 9.10, and screensaver went off every 15 seconds and asked me for my password, no matter how I set screensaver. To my pleasant surprise, Ubuntu fixed it [don't remember how--it was late at night] but I get errors when I try to install updates now. Related?

If you're confused now, I tend to have that effect on folks. Blame my ADD.

Looking forward to help, thanks!

Dannis

---

### Post by jbrown96 on 2009-11-11
I don't understand what you are saying about all the drives showing up.

If you want to mount them, so you can copy data from them, then do this. 

1) Create a mount mount ```
mkdir Desktop/windows
```
2) mount the first partition ```
sudo mount /dev/sda1 Desktop/windows
```
3) Open the windows folder on your desktop, and copy over the files you want. 
4) Unmount the partition ```
sudo umount Desktop/windows
```
5) try mounting /dev/sda2 to see if there's anything on there you want. It looks like some kind of recovery partition or Windows boot partition, so there's probably nothing on there you need. 

Intel has the best hardware support of any manufacturer. They actively develop open source drivers with the Linux community. Your intel hardware should work with very few issues. The Nvidia graphics card should be fine as long as it's not too old. Nvidia makes good proprietary drivers. 

Windows can't read linux file systems, so it always wants to format them into something it understands. You don't want to format them, or Ubuntu will break.

---

### Post by dannistories on 2009-11-11
Please explain Step 1; it's been 20 years since I did any command prompt stuff, and a lot has changed ;). Am I creating a logical, then assigning a partition to the logical? If not, where exactly am I creating the new directory? I don't want to copy stuff over from Vista, I want to move stuff from Vista and Linux to the new partition and make it a shared data only partition.

sudo mount /dev/sda1
mount: /dev/sda1 already mounted or /media/HP busy
mount: according to mtab, /dev/sda1 is already mounted on /media/HP
~$ sudo mount /dev/sda2
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
~$ sudo mount /dev/sda3
mount: can't find /dev/sda3 in /etc/fstab or /etc/mtab
~$ sudo mount /dev/sda4
mount: can't find /dev/sda4 in /etc/fstab or /etc/mtab
~$ sudo mount /dev/sda5
mount: /dev/sda5 already mounted or / busy
mount: according to mtab, /dev/sda5 is already mounted on /

I can see files on sda1, now that I know what that is. Is sda5 my Linux partition? Why don't I see files on the swap drive, the Vista restore, or the [empty?] new sda3 [I would expect at least something similar to a directory entry with no files]

Also, I want to use sda3 for my file storage. Any way to format just that partition to NTFS so Vista won't complain, but preserve the other partitions as is? I created it large with the intention of using it for all my file storage, but apparently the Vista partition didn't shrink as much as I wanted. I want to shrink Vista, remove the useless restore partition, and add space to sda3 [now I'm beginning to see how this works, I think].

Another complication is that Vista will not boot now, and I probably have to reformat that partition, if Windows won't ruin my whole setup. Any suggestions?

As for the Linux/no sound problem, I'm not alone. See Multimedia and Sound board. Many of us are having sound problems with onboard Intel sound on HP machines. Someplace [can't find it now] on the Ubuntu site, someone said Intel makes so many versions, Ubuntu can't keep up, so maybe not Intel's fault, after all. Someone was blaming Intel. I checked the volume controls, unmuted, installed PulseAudio to try to get Skype to work [works with headphones but can't use mic], and haven't had time to keep trying other things. My upgrade to 9.10 blew up so I'm scared to try upgrading again for a while; also having problems updating anything thru Update Mgr.

Thanks for help!

---

### Post by jbrown96 on 2009-11-11
Your partition setup is not going to work for another data partition. Hard drives only support four partitions; you can get around this by using "extended" partition, which are containers for other partitions. Sda3 is an extended partition. You can't delete it, or else you will lose access the sda5/6 (Ubuntu). sda3 doesn't actually use any space, but it reports that it is the size of the partitions inside it. 

I'm not a big fan of separate data partitions. They really aren't necessary. Just store everything on your Vista partition. You can mount that in Ubuntu, and create links to the folders you want to access. 

Your system has already mounted sda1 to /media/HP. You can access everything there. 

In order to mount partitions, there needs to be an empty folder (not really, but for simplicity let's say so) to mount the partition. Step 1 just creates an empty folder called windows on your Desktop. Step 2 actually mounts the drive there. 

I've never liked pulseaudio. It doesn't work very well, and doesn't offer any real-world advantages. Pulseaudio uses Alsa as a back-end. Why not just use Alsa directly? It has wonderful Intel support.

---

### Post by kansasnoob on 2009-11-11
> **dannistories said:**
> Folks,
  Here's my thing:
sudo fdisk -l
[sudo] password for dannis: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x322ca97f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       63283   508315616    7  HPFS/NTFS
/dev/sda2          120102      121602    12048384    7  HPFS/NTFS
/dev/sda3           63284      120101   456390585    5  Extended
/dev/sda5           63284      118877   446558773+  83  Linux
/dev/sda6          118878      120101     9831748+  82  Linux swap / Solaris

Partition table entries are not in disk order
 I used ext2 for windows to partition, and use GRUB to boot.  In Vista, I can see the L: drive and S: [linux swap] partitions I created, but where are they in Linux? I can see my HP drive and everything on it just fine, and my network drive. I want to get every data file off Vista and Linux onto a partition by themselves in case I have to reinstall Vista again [got yet another blue screen of death this morning - thank goodness for Ubuntu!!]

Went to ext2 for win site and I think I need to download a diagnostic, because when I try to look at L: or S: in Vista, it asks if I want to format. Is this because I don't have data there yet, or do I need to format L: in NTFS, or do I need to do the diagnostic?! I'm soooo confuuuuuuused!!

I used to speak UNIX at work, but that was before the GUI, and I forgot more than I ever learned from MAN. I think I got stupider as I got older. I hate Vista, but have to keep it if I want sound [sound chips in Intel chipset - will Intel ever play ball with Tux??]. Video is GForce [it's written down someplace in a file]. My PC is an IQ 506t with a touchscreen.

I tried to upgrade to 9.10, and screensaver went off every 15 seconds and asked me for my password, no matter how I set screensaver. To my pleasant surprise, Ubuntu fixed it [don't remember how--it was late at night] but I get errors when I try to install updates now. Related?

If you're confused now, I tend to have that effect on folks. Blame my ADD.

Looking forward to help, thanks!

Dannis

I'm more than a little bit unclear what you're trying to do here.

I assume you're trying to copy data from Win to another partition using Windows???????????

If your Ubuntu is working I think it would be tons easier to install ntfsprogs in Ubuntu (it's in the repos), and copy those files/folders to another partition using Ubuntu.

For example (with ntfsprogs installed) I can mount my Win XP:

[ATTACH]135767[/ATTACH]

I'd likely want to double click the Document & Settings folder and then just right click any of the contents I want to copy and then paste them into whatever other partition I've mounted.

I always just use NTFS for shared data partitions. It's just simpler.

---

