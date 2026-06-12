---
title: "how do i mount an external hard drive"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by hoppyandy on 2008-12-30
i have recently uninstalled vista and replaced it with ubuntu 8.10 on my fujitsu siemens laptop. i have had no problems except i have a 320gb seagate external hard drive which when plugged in does nothing. i can see in gparted and labelled as fat32 /dev/sdb1 shows as unmounted and not visible in computer. i have turned off automount in windows still not visible. i found a post which via terminal allowed me to manually add it which i was happy with, but you guessed it i never wrote down instructions and for the life of me i cant find the post again. Any help would be appreciated. i am as i said a complete newbie, but having fun learning.

---

### Post by Bucky Ball on 2008-12-30
Is the usb drive formatted? If not, format it in gparted.

ps: sorry, fat32. Will think some more

---

### Post by kansasnoob on 2008-12-30
Install pmount either from synaptic or:

```
sudo apt-get install pmount
```

Brief description:

> pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.


---

### Post by hoppyandy on 2008-12-30
Thanks for reply, i havent formatted it with gparted as it has all my music and videos on and i think they will be deleted if i format it, i still have a windows computer i was hoping to switch drive between the 2 computers. it allowed me to play files when i added info in terminal but info didnt save and i cant remember what i typed

---

### Post by wizard10000 on 2008-12-30
> **hoppyandy said:**
> Thanks for reply, i havent formatted it with gparted as it has all my music and videos on and i think they will be deleted if i format it, i still have a windows computer i was hoping to switch drive between the 2 computers. it allowed me to play files when i added info in terminal but info didnt save and i cant remember what i typed

I had the same problem when I upgraded from Hardy to Intrepid - turned out that in Intrepid regular users no longer have rights to mount removable drives.

If you go into System --> Administration --> Authorizations you'll see where you need to change the setting to allow regular users to mount removable drives.

good luck -

[rant]

Ubuntu developers, are you listening?  Upgrades should not change existing security policies without thorough documentation and in my case they certainly did  :)

[/rant]

---

### Post by hoppyandy on 2008-12-30
i have tried pmount looked hopefull but still didnt show, went into authorizations and changed to yes on both counts but still no show, how do i mount manually ? not sure if i am supposed to manually add after your suggestions, thanks for your help so far.

---

### Post by wizard10000 on 2008-12-30
> **hoppyandy said:**
> i have tried pmount looked hopefull but still didnt show, went into authorizations and changed to yes on both counts but still no show, how do i mount manually ? not sure if i am supposed to manually add after your suggestions, thanks for your help so far.

You have to log off and back on for the new authorizations to take effect.

---

### Post by hoppyandy on 2008-12-30
log off and on - no change, switched off and on still no change - sorry when i use a usb stick all works fine just this hard drive ? i edited storage - mount file systems from removeable drives to yes for both options was that correct ?

---

### Post by wizard10000 on 2008-12-30
> **hoppyandy said:**
> log off and on - no change, switched off and on still no change - sorry when i use a usb stick all works fine just this hard drive ? i edited storage - mount file systems from removeable drives to yes for both options was that correct ?

I'm at the office and my Intrepid box is at home so I can't read the options for you - perhaps someone who's on a Linux box can answer this?

---

### Post by xjcannonx on 2008-12-30
Was this hooked up to a windows machine before. If so, it does need to be 'safely removed' from windows or else it probably wont work.

---

### Post by hoppyandy on 2008-12-30
Yes it was hooked up to windows, i think i safely removed will reconnect and try again, i did switch off autostart as i read this was a problem for someone else but still didnt work, annoying thing is it worked fine when i manually mounted it i think via terminal, but forgot how i did it and cant find the post which gave the instructions, but many thanks for all your quick replies, i expected to wait days, you guys are great.

---

### Post by kansasnoob on 2008-12-30
Read the Manually Mounting section here:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by hoppyandy on 2008-12-30
Thanks for the link, i got it to mount manually by using sudo mkdir /media/ SEA_DISK 
sudo mount -t vfat /dev/sdb1 / media/SEA_DISK
is there a way i can save this ? so i dont have to enter it every time i connect.? 
i am happy i can now use the hard drive now even if i do have to enter this each time. thanks to all for help:D

---

### Post by xjcannonx on 2008-12-30
You can add a line to your /etc/fstab file, but be careful with this file, there are many tutorials that can explain better than me on how to edit fstab

But i still want to say that the force mount is not the ideal solution in my opinion, it seems to me that windows is still holding on to your drive, 

From my limited understanding windows will write something to your drive basically "claiming it" and the best way is to get rid of that "hold" by either safely removing or what working for me was to have it connected to my windows machine and then i just shut down and then removed the drive and hooked it up to ubuntu

It can possibly be harmful to mount a drive that anather OS has a hold of still...Anyone correct me if I am wrong.

---

### Post by hoppyandy on 2008-12-30
Thanks for the warning, i will look into what the problem is further, i have another external hard drive i use on my windows machine perhaps i will try that one and i will safely remove first, i was hopeing to be able to share the files between the 2 computers. but not really important probably got too much space and too much junk anyway. i dont really understand what /etc/fstab file is, so i probably best leave alone until i do, keep reading the books ha ha . thanks for the advise though.

---

### Post by xjcannonx on 2008-12-30
here is a good tutorial by one of the staff here [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=283131[/COLOR]]("http://ubuntuforums.org/showthread.php?t=283131")

Don't get discouraged at all, what you want to do is totally possible and im sure you will find that the "sky is limitless" (well almost...) if you can think it you can probably do it....its just the idea that we need

---

### Post by hoppyandy on 2008-12-30
Thanks for the link i have bookmarked as heavy reading but i am starting to understand, will i do any harm to my computer or external hard drive if i manually add as i mentioned before at least until i understand about fstab etc.

---

### Post by xjcannonx on 2008-12-30
If you force mount an uncooperative external HD like talked about, nothing bad will most likely happen, fellow users around here seem to do it a lot, i was just cautioning that something could happen although I have not personally heard of anything bad happening

---

### Post by kaginken on 2008-12-30
You don't have to worry about any harm coming to your pc or ext hard drive, feel free to play with the configs...

HOWEVER note that you should definitely back up that fstab file first before making any changes!  Once you have that, you run no risk at all in fiddling around with your fstab file because you can always just restore your backed up copy.

Best way to get a local backup is to just copy it like so

```
cp /etc/fstab /etc/original_fstab
```

Hope this tip helps!

:guitar:

---

### Post by decoherence on 2008-12-30
it looks like you have some workaround suggestions, but if you're interested in getting it to work the way it should (plug and play -- yes, it IS supposed to work!) then do the following to diagnose the problem

first unplug your external drive, then type the following in to a terminal

```
sudo udevadm monitor > ~/udevOutput.txt
```

hit return, let it sit there and plug in your external drive. wait for oh... ten seconds (to be safe) then press CTRL C to exit udevadm.

In your home directory you should find a file called udevOutput.txt. Please copy/paste the contents here.

also,

```
cat /etc/udev/rules.d/60-persistent-storage.rules > ~/udevRules.txt

```

will create a file called udevRules.txt. I think it's supposed to be universal but I don't know for sure so best include it as well.

---

### Post by hoppyandy on 2008-12-30
Tried to backup as you suggest and get message

cp : missing destination file operand after /etc/original_fstab


i guess i need to add a destinationfolder ? but dont know how to add one in terminal
sorry only been using Ubuntu 2 days always used windows, till now got shot of vista and here i am 

Ps i notice people have thanks against them i suspect added by people like me ? how do i thank people for there help other than just adding to this text ?

---

### Post by RealG187 on 2008-12-30
Maybe it's something in the fstab.

I had to remove a few lines. Did you use Unetbootin to install Ubuntu?

---

### Post by xjcannonx on 2008-12-31
> **hoppyandy said:**
> Tried to backup as you suggest and get message

cp : missing destination file operand after /etc/original_fstab


i guess i need to add a destinationfolder ? but dont know how to add one in terminal
sorry only been using Ubuntu 2 days always used windows, till now got shot of vista and here i am 

Ps i notice people have thanks against them i suspect added by people like me ? how do i thank people for there help other than just adding to this text ?

You shouldn't have to do anything to copy that fstab file but you do need to preface the command with sudo.

To thank someone you need to look for the "medal" looking thing on the bottom right of each post

---

### Post by hoppyandy on 2008-12-31
good morning all thanks for all the advise, i have reconnected ext hard drive to windows and safely removed still no change.
i have carried out procedure as instructed by DECOHERENCE and pasted below

udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent
udevOutput.txt
UDEV  [1230725889.763505] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5 (usb)
UEVENT[1230725889.772930] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0 (usb)
UEVENT[1230725889.775567] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8 (scsi)
UEVENT[1230725889.777272] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/scsi_host/host8 (scsi_host)
UEVENT[1230725889.780243] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/usb_endpoint/usbdev5.4_ep02 (usb_endpoint)
UEVENT[1230725889.780648] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/usb_endpoint/usbdev5.4_ep86 (usb_endpoint)
UEVENT[1230725889.781383] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/usb_endpoint/usbdev5.4_ep00 (usb_endpoint)
UDEV  [1230725889.785035] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/usb_endpoint/usbdev5.4_ep00 (usb_endpoint)
UDEV  [1230725889.839921] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0 (usb)
UDEV  [1230725889.852271] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8 (scsi)
UDEV  [1230725889.854006] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/usb_endpoint/usbdev5.4_ep86 (usb_endpoint)
UDEV  [1230725889.854459] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/usb_endpoint/usbdev5.4_ep02 (usb_endpoint)
UDEV  [1230725889.855153] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/scsi_host/host8 (scsi_host)
UEVENT[1230725894.782803] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0 (scsi)
UEVENT[1230725894.783225] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0 (scsi)
UEVENT[1230725894.783585] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0/scsi_disk/8:0:0:0 (scsi_disk)
UDEV  [1230725894.809495] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0 (scsi)
UDEV  [1230725894.906215] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0 (scsi)
UDEV  [1230725894.907659] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0/scsi_disk/8:0:0:0 (scsi_disk)
UEVENT[1230725900.270688] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0/block/sdb (block)
UEVENT[1230725900.270721] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0/block/sdb/sdb1 (block)
UEVENT[1230725900.271784] add      /devices/virtual/bdi/8:16 (bdi)
UDEV  [1230725900.273047] add      /devices/virtual/bdi/8:16 (bdi)
UEVENT[1230725900.278294] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0/scsi_device/8:0:0:0 (scsi_device)
UEVENT[1230725900.278467] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0/scsi_generic/sg2 (scsi_generic)
UDEV  [1230725900.282383] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0/scsi_device/8:0:0:0 (scsi_device)
UDEV  [1230725900.291508] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0/scsi_generic/sg2 (scsi_generic)
UDEV  [1230725900.421166] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0/block/sdb (block)
UDEV  [1230725900.517601] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host8/target8:0:0/8:0:0:0/block/sdb/sdb1 (block)

udevRules.txt
# do not edit this file, it will be overwritten on update

# persistent storage links: /dev/disk/{by-id,by-uuid,by-label,by-path}
# scheme based on "Linux persistent device names", 2004, Hannes Reinecke <hare@suse.de>

# forward scsi device event to corresponding block device
ACTION=="change", SUBSYSTEM=="scsi", ENV{DEVTYPE}=="scsi_device", TEST=="block", ATTR{block/*/uevent}="change"

ACTION!="add|change", GOTO="persistent_storage_end"
SUBSYSTEM!="block", GOTO="persistent_storage_end"

# skip rules for inappropriate block devices
KERNEL=="ram*|loop*|fd*|nbd*|gnbd*|dm-*|md*", GOTO="persistent_storage_end"

# never access non-cdrom removable ide devices, the drivers are causing event loops on open()
KERNEL=="hd*[!0-9]", ATTR{removable}=="1", DRIVERS=="ide-cs|ide-floppy", GOTO="persistent_storage_end"
KERNEL=="hd*[0-9]", ATTRS{removable}=="1", GOTO="persistent_storage_end"

# ignore partitions that span the entire disk
TEST=="whole_disk", GOTO="persistent_storage_end"

# /sys/class/block will export this
ENV{DEVTYPE}!="?*", ATTR{range}=="?*", ENV{DEVTYPE}="disk"
ENV{DEVTYPE}!="?*", ATTR{start}=="?*", ENV{DEVTYPE}="partition"

# for partitions import parent information
ENV{DEVTYPE}=="partition", IMPORT{parent}="ID_*"

# by-id (hardware serial number)
KERNEL=="hd*[!0-9]", IMPORT{program}="ata_id --export $tempnode"
KERNEL=="hd*[!0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}"
KERNEL=="hd*[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}-part%n"

KERNEL=="sd*[!0-9]|sr*", ATTRS{ieee1394_id}=="?*", ENV{ID_SERIAL}="$attr{ieee1394_id}", ENV{ID_BUS}="ieee1394"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", SUBSYSTEMS=="usb", IMPORT{program}="usb_id --export %p"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted -d $tempnode", ENV{ID_BUS}="scsi"
KERNEL=="cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted -d $tempnode", ENV{ID_BUS}="cciss"
KERNEL=="sd*[!0-9]|sr*|cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}"
KERNEL=="sd*[0-9]|cciss*p[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}-part%n"

# libata compat (links like hd*)
KERNEL=="sd*[!0-9]|sr*", ENV{ID_VENDOR}=="ATA", PROGRAM="ata_id $tempnode", RESULT=="?*", ENV{ID_ATA_COMPAT}="$result", SYMLINK+="disk/by-id/ata-$env{ID_ATA_COMPAT}"
KERNEL=="sd*[0-9]", ENV{ID_ATA_COMPAT}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_ATA_COMPAT}-part%n"

KERNEL=="mmcblk[0-9]", SUBSYSTEMS=="mmc", ATTRS{name}=="?*", ATTRS{serial}=="?*", ENV{ID_NAME}="$attr{name}", ENV{ID_SERIAL}="$attr{serial}", SYMLINK+="disk/by-id/mmc-$env{ID_NAME}_$env{ID_SERIAL}"
KERNEL=="mmcblk[0-9]p[0-9]", ENV{ID_NAME}=="?*", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/mmc-$env{ID_NAME}_$env{ID_SERIAL}-part%n"

# by-path (shortest physical path)
ENV{DEVTYPE}=="disk", IMPORT{program}="path_id %p"
ENV{DEVTYPE}=="disk", ENV{ID_PATH}=="?*", SYMLINK+="disk/by-path/$env{ID_PATH}"
ENV{DEVTYPE}=="partition", ENV{ID_PATH}=="?*", SYMLINK+="disk/by-path/$env{ID_PATH}-part%n"

# skip unpartitioned removable media devices from drivers which do not send "change" events
ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"
# skip optical drives without media
ENV{DEVTYPE}=="disk", KERNEL=="sr*", ENV{ID_CDROM_MEDIA_TRACK_COUNT}!="?*", GOTO="persistent_storage_end"

# import filesystem metadata
IMPORT{program}="vol_id --export $tempnode"

# by-label/by-uuid links (filesystem metadata)
ENV{ID_FS_USAGE}=="filesystem|other|crypto", ENV{ID_FS_UUID_ENC}=="?*", SYMLINK+="disk/by-uuid/$env{ID_FS_UUID_ENC}"
ENV{ID_FS_USAGE}=="filesystem|other", ENV{ID_FS_LABEL_ENC}=="?*", SYMLINK+="disk/by-label/$env{ID_FS_LABEL_ENC}"

LABEL="persistent_storage_end"

---

### Post by hoppyandy on 2008-12-31
> **xjcannonx said:**
> You shouldn't have to do anything to copy that fstab file but you do need to preface the command with sudo.

To thank someone you need to look for the "medal" looking thing on the bottom right of each post

carried copy out again with sudo in front and nothing happened - suspect worked but i dont know where or how to find / look, not in home folder like copies of report logs previously posted.

found thanks "medal" slow learner i guess, thanks for your patience aswell as your help.

---

### Post by mc4man on 2008-12-31
As mentioned by DECOHERENCE you shouldn't have to do anything but plug the drive in. 
If you were to go to places -> computer and then plug the drive in, nothing shows up?
Why don't you also post your fstab

```
cat /etc/fstab
```

---

### Post by hoppyandy on 2008-12-31
Nothing shows for it on computer. did as you suggest and heres the info. ext hard drive shows i gparted as sdb1.not sure it mentions it here, other report showed it and some entries show as Blocked ? but not sure what it means.
results below.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=871c22d1-d6c6-41f8-b738-afacb764ee11 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=07acd29d-ebbb-4bef-82a4-fff7e585d48a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by vanadium on 2008-12-31
An external drive should mount automatically. It should not be mentioned in /etc/fstab.

Is the drive seen by Ubuntu? To check that, make sure the drive is connected (and powered on) and post the output here of following commands

```

sudo fdisk -l
mount

```

---

### Post by hoppyandy on 2008-12-31
> **vanadium said:**
> An external drive should mount automatically. It should not be mentioned in /etc/fstab.

Is the drive seen by Ubuntu? To check that, make sure the drive is connected (and powered on) and post the output here of following commands

```

sudo fdisk -l
mount

```
copy of what you ask, notice it is mentioned label is sdb1


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc84b2669

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14031   112703976   83  Linux
/dev/sda3           14032       14593     4514265    5  Extended
/dev/sda5           14032       14593     4514233+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA)
andy@andy-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andy)

---

### Post by hoppyandy on 2008-12-31
i must have something on this hard drive left over from windows so i will move all files onto my windows machine then format this drive, should i do that under windows or ubuntu and how and what should i label it as or will it be done automatically.

Is there a way i can make this drive usable by both ubuntu and vista.?

---

### Post by mc4man on 2008-12-31
> Is there a way i can make this drive usable by both ubuntu and vista.?

If your going to start fresh I'd format it on windows as ntfs  ( control panel -> administrative tools -> computer management -> disc management.


Before it formats you will be given an opportunity to give it it a 'volume label' (will probably default to 'new volume'

After it's formatted you can also set a volume label in disc management by right clicking on the partition -> properties and insert a name in the box. I'd kept it simple.
All my seagate usb drives by default were named SEA_DISK which I've left on one and named the other one STORAGE.

You can change the volume label in ubuntu with ntfsprogs if you so choose

You can think of the volume label as a 'display' name, in ubuntu when you connect the drive it should automount to /media/<volume label> and appear on your desktop and in computer or places as 'whatever volume label you gave it'



> i have turned off automount in windows still not visible
Don't quite get that, I wouldn't do anything in that regard.

---

### Post by hoppyandy on 2009-01-17
I finally managed to move all the files from this hard drive then did as you suggested, formatted using windows as ntfs and labelled seagate.
took a few hours but GREAT as soon as i plugged it into my laptop Ubuntu recognised it and auto mounted as you said.
Well happy.
Many thanks to all you guys for your help with this.

---

