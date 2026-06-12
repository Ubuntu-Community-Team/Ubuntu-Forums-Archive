---
title: "cannot write to usb - need root permission"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by tadcan on 2010-05-09
I have been doing some research, but i don't know enough to solve the issue. If I mount a usb drive with a name, then the name appears in places but will not open. Then usb0 appears below it, which I can open but not write to. 

Looking up the forums I found a request to post cat ```
/etc/mtab
```

```
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/tadcan/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=tadcan 0 0
/dev/mmcblk0p1 /media/702A-9012 vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
/dev/sdb /media/usb0 vfat rw,noexec,nodev,sync,noatime,nodiratime 0 0
```

I found this as a fix, but I presume the syntax is different 
```
/dev/hda2 /media/documents vfat user,auto 0 0
```

I tried playing around with it, but no luck. 
```
tadcan@tads-lappy:~$ /media/documents vfat user,auto 0 0
bash: /media/documents: No such file or directory
tadcan@tads-lappy:~$ cd /media/usb0 vfat user,auto 0 0 
tadcan@tads-lappy:/media/usb0$ vfat user,auto 0 0
No command 'vfat' found, did you mean:
 Command 'vcat' from package 'atfs' (universe)
vfat: command not found
```

Any advice

---

### Post by -humanaut- on 2010-05-09
When the usb drive shows up right-click on it and go to properties and see what the permissions are. Another thing it could be Locked up if it was unmounted improperly If you pulled it from a Windows machine without properly "ejecting" the drive it will lock it up until you unmount it properly.

---

### Post by tadcan on 2010-05-09
The permissions of "usb0" could not be determined

---

### Post by -humanaut- on 2010-05-09
My guess would be it was improperly unmounted. You could always reformat the drive I had a similar problem to yours and a quick format to Fat32 (vfat) seemed to Solve the problem. ((( It was a usb drive that was given to me so I don't know why it was locked )))

---

### Post by tadcan on 2010-05-09
I rebooted into windows and unmounted the drive, it didn't work. I ejected usb key from another windows machine and its permissions were listed as root(usb1). When I try to unmount usb1 I'm told umount: /media/usb1 is not in the fstab(and you are not root)

It is an issue with any usb drive. I am running 10.04 since beta 1, would it be worth it to reinstall?

---

### Post by dagdeniz on 2010-05-09
i don't know if this will work but...
type ```
gksudo nautilus
``` in the terminal so that you can navigate with root permissions and unmount it that way. you should also be able to change the permissions that way.

---

### Post by tadcan on 2010-05-09
I got the same message about not be able to unmount, but it did after I pressed ok. Then by clicking on the name of the drive I had full read/write access.

Is there a permanent fix?

---

### Post by dagdeniz on 2010-05-09
can you post your /etc/fstab?

---

### Post by tadcan on 2010-05-09
hm, when I use ls fstab is listed, but when I try to go there I'm told its not a folder.

```
tadcan@tads-lappy:~$ cd /etc
tadcan@tads-lappy:/etc$ ls
acpi                    gshadow              perl
adduser.conf            gshadow-             pm
akonadi                 gtk-2.0              pmount.allow
alternatives            hal                  pnm2ppa.conf
anacrontab              hdparm.conf          polkit-1
apm                     host.conf            popularity-contest.conf
apparmor                hostname             ppp
apparmor.d              hosts                printcap
apport                  hosts.allow          profile
apt                     hosts.deny           profile.d
at.deny                 hp                   protocols
avahi                   ifplugd              pulse
bash.bashrc             init                 python
bash_completion         init.d               python2.6
bash_completion.d       initramfs-tools      rc0.d
bindresvport.blacklist  inputrc              rc1.d
blkid.conf              insserv              rc2.d
blkid.tab               insserv.conf         rc3.d
bluetooth               insserv.conf.d       rc4.d
bogofilter.cf           iproute2             rc5.d
bonobo-activation       issue                rc6.d
brlapi.key              issue.net            rc.local
brltty                  kbd                  rcS.d
byobu                   kernel               rearj.cfg
ca-certificates         kernel-img.conf      resolvconf
ca-certificates.conf    kerneloops.conf      resolv.conf
calendar                ksysguarddrc         rmt
chatscripts             ldap                 rpc
checkbox.d              ld.so.cache          rsyslog.conf
compizconfig            ld.so.conf           rsyslog.d
computer-janitor.d      ld.so.conf.d         samba
ConsoleKit              legal                sane.d
console-setup           lftp.conf            screenrc
couchdb                 libao.conf           securetty
cron.d                  libpaper.d           security
cron.daily              locale.alias         sensors3.conf
cron.hourly             localtime            sensors.d
cron.monthly            logcheck             services
crontab                 login.defs           sgml
cron.weekly             logrotate.conf       shadow
crypttab                logrotate.d          shadow-
cups                    lsb-base             shells
dbus-1                  lsb-base-logging.sh  skel
debconf.conf            lsb-release          sound
debian_version          ltrace.conf          speech-dispatcher
default                 magic                ssh
defoma                  magic.mime           ssl
deluser.conf            mailcap              sudoers
depmod.d                mailcap.order        sudoers.d
dhcp3                   manpath.config       sysctl.conf
dictionaries-common     mime.types           sysctl.d
doc-base                mke2fs.conf          terminfo
dpkg                    modprobe.d           timezone
emacs                   modules              timidity
environment             mono                 ts.conf
esound                  motd                 ucf.conf
firefox                 mtab                 udev
firefox-3.0             mtab.fuselock        ufw
fonts                   mtools.conf          updatedb.conf
foomatic                mysql                update-manager
fstab                   nanorc               update-motd.d
fuse.conf               netscsid.conf        update-notifier
gai.conf                network              usbmount
gamin                   NetworkManager       vim
gconf                   networks             vlc
gdb                     nsswitch.conf        w3m
gdm                     obex-data-server     wgetrc
gimp                    openal               wildmidi
gnome                   openoffice           wodim.conf
gnome-app-install       opt                  wpa_supplicant
gnome-system-tools      PackageKit           X11
gnome-vfs-2.0           pam.conf             xdg
gnome-vfs-mime-magic    pam.d                xml
gre.d                   pango                xul-ext
groff                   papersize            xulrunner-1.9.1
group                   passwd               xulrunner-1.9.2
group-                  passwd-              zsh_command_not_found
grub.d                  pcmcia
tadcan@tads-lappy:/etc$ cd fstab
bash: cd: fstab: Not a directory
tadcan@tads-lappy:/etc$ cd /fstab
bash: cd: /fstab: No such file or directory

```

---

### Post by dagdeniz on 2010-05-09
i thought you would navigate to /etc/fstab ;)
ok then, if you want terminal: 
```
sudo nano /etc/fstab
```
:P

---

### Post by tadcan on 2010-05-09
ah, its a file not a folder. I mostly use the GUI, I'm a faker when it comes to the internals

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=d73153ed-1e54-467b-b2a3-2890fb586918 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=064f7c03-0b76-4028-a594-8c50d27e04b0 none            swap    sw              0       0

```

---

### Post by dagdeniz on 2010-05-09
i see. i think it was the wrong place where you tried to put the partition mounting parameters. here is what you have to put in fstab: 
1. partition name (is your usb disk /dev/hda ?)
2. where you want to mount it (generally /media/bla bla bla)
3. the format of the partition (vfat in this case)
4. preferences ("user,auto" or if you want to mount it manually, "user,noauto")
5. 0 (it's always zero, i don't know what it is) 
6. password requirement (0 is no, i think)

so, if that code you've written is correct considering the above parameters, after unmounting the flashdisk, include it in the fstab (again, by sudo nano /etc/fstab) and that should solve it i think.

---

### Post by tadcan on 2010-05-09
Where would I see the partition name. 

In /media I just see usb0

Is there another place to give that info.

Is there an example somewhere of what the fstab should look like?

---

### Post by dagdeniz on 2010-05-09
```
sudo fdisk -l
```is where you can see the partition numbers. 

sorry, didn't see the last part of your question. your fstab entry will look like: 

```

# <file system> <mount point>   <type>   <options>       <dump>  <pass>
#the hdd entry 
#the swap entry
/dev/sdb           /media/usb0      vfat        user,auto         0             0

```

---

### Post by tadcan on 2010-05-09
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00028137

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       50100   402428218+   7  HPFS/NTFS
/dev/sda2           50101       60801    85955782+   5  Extended
/dev/sda5           50101       60360    82413418+  83  Linux
/dev/sda6           60361       60801     3542301   82  Linux swap / Solaris

Disk /dev/mmcblk0: 3963 MB, 3963617280 bytes
128 heads, 63 sectors/track, 960 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               2         960     3866624    b  W95 FAT32

Disk /dev/sdb: 256 MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ce01c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         979      250574+   6  FAT16

Disk /dev/sdc: 4007 MB, 4007624704 bytes
32 heads, 63 sectors/track, 3882 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20b54209

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3882     3913024+   b  W95 FAT32

Disk /dev/sdd: 16.1 GB, 16064184320 bytes
95 heads, 16 sectors/track, 20641 cylinders
Units = cylinders of 1520 * 512 = 778240 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       20642    15687671+   c  W95 FAT32 (LBA)

Disk /dev/sde: 8198 MB, 8198815744 bytes
253 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15686 * 512 = 8031232 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   ?       49608      122380   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(49607, 8, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(122379, 137, 51)
Partition 1 does not end on cylinder boundary.
/dev/sde2   ?       10755      134179   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(10754, 36, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(134178, 26, 42)
Partition 2 does not end on cylinder boundary.
/dev/sde3   ?      119208      242631   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(119207, 7, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(242630, 249, 39)
Partition 3 does not end on cylinder boundary.
/dev/sde4   ?      183966      183969       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(183965, 99, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(183968, 235, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

---

### Post by dagdeniz on 2010-05-09
from here i can't guess which is the flashdisk (sdb1, sdc1, sdd1?) you can guess from its size. simply add a line like this :

```
/dev/sd?1        /media/usb0     vfat    user,auto       0        0
```

replacing question mark with the appropriate letter.

---

### Post by tadcan on 2010-05-09
Does the text you provided replace what is already in fstab?

I added a 1 to sdb1 since that is the first one listed in the usb drives.

Do I need any more into before making the change

```
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
#the hdd entry 
#the swap entry
/dev/sdb1           /media/usb0      vfat        user,auto         0             0
```

---

### Post by dagdeniz on 2010-05-09
no, it will not replace anything; i've written the first three lines only to represent what's in the fstab, so, you'll omit them. just add the last line to the end of fstab without deleting anything, (more detailed:1. sudo nano /etc/fstab 2. write it 3. save with ctrl+O and enter 4. exit with ctrl+x) and let's see if it'll work.

---

### Post by tadcan on 2010-05-09
opps i missed your reply

I had three usb devices in so I guess these.
/dev/sdb1 
/dev/sdc1
/dev/sdd1

This was at the head of allot of text so not sure what it refers to.
/dev/sde1

I do have four usb ports, so it may refer to that. 

Do I need to have an entry for every port?

---

### Post by dagdeniz on 2010-05-09
i don't think so, because normally it can mounted and unmounted by user. this can be, as -humanaut- stated, an ocassional situation specific to that drive. so, adding that drive to fstab will be enough, i think.

---

### Post by tadcan on 2010-05-09
When I restarted I get this message

The disk for media/usb0 is not ready or is not yet present

continue to wait; or press S to skip mounting or M for manual recovery


putting in a usb restarts booting
Still not change to the permissions

Here is what the fstab looks like now with the extra line. Have I made a mistake.
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=d73153ed-1e54-467b-b2a3-2890fb586918 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=064f7c03-0b76-4028-a594-8c50d27e04b0 none            swap    sw              0       0
/dev/sdb1           /media/usb0      vfat        user,auto         0             0

```

---

### Post by dagdeniz on 2010-05-09
i can't guess what's wrong...
now, it was mounting and your problem was that it was not writable by user, right? 
then can this gui method be a solution: 
delete the line you've written, unplug and plug it, if it's mounted automatically, navigate to that drive with root privileges (gksudo nautilus), right click when in that partition, change privileges from the third tab:  if the owner and group are root, change them to tadcan, change folder accessibility to read and write. 

i started to feel stupid, this should't be hard.

---

### Post by tadcan on 2010-05-09
I did all that and was told that the owner could not be changed. My problem was with writing to the usb drive, mounting is not a problem.

I think i will just reinstall in the morning. It worked up to a few days ago

---

### Post by chappajar on 2010-05-09
The 'user' option doesn't work for FAT or NTFS, only ext* (that's why you couldn't write).
You need to use 'uid=' or 'gid=' and/or 'umask=' on FAT/NTFS.
I use 'uid=1000' and 'umask=022' --> user 1000 sets the owner of the disk to the first user on the system, umask 022 gives 755 permissions to the whole disk.


This may or may not be helpful in the future but if something refuses to mount you can force mount it:
sudo mount /dev/(yourdevice) /media/(yourMntPoint) -o force

---

### Post by Handssolow on 2010-05-11
I'm looking for a solution too with this problem, I need to be be root to do much with my USB flash memory sticks. My current solution is gksudo nautilus. This problem seems to have happened after upgrading to 10.04 (lucid)

Under gksudo nautilus I'm not able to change permissions because I'm not the owner of USB0.

/usr/share/doc/usbmount/README.gz yields the following information-

The vfat filesystem is one of the most commonly used filesystems in pen
drives. Unfortunately, due to its age, it is very poor regarding
features and, in particular, it doesn't feature the most basic access
control present in Unix systems, namely: permissions on files.

Linux works around this by creating "virtual" permissions and
restrictions based on who mounted the filesystem. As usbmount is used,
the user assigned to the vfat filesystem is, by default, root.

---

### Post by cloyd on 2010-05-11
I've been told that this should not be necessary, but I've had trouble with some pen drives, my mp3 player, and a seagate external hard drive. This works. 

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

go down the page and look under manually mounting.

If it works for you, write a script file, so you don't have to key in the long line. 
There may be another solution, but it worked for me when nothing else would.

---

### Post by Handssolow on 2010-05-11
The current situation here is when I plug for example a USB 1Gb flash drive it mounts, USB0 appears on my desktop but a right mouse click shows that permissions are held by root.

Next I go into terminal for a gksudo nautilus then to Places to right click on USB0 to select unmount. The USB0 icon disappears from my desktop but the light on my USB stick is still glowing.

Next Places then shows I've got a 1.0Gb Filesystem and soon a different icon appears on my Desktop showing this 1Gb Filesystem (my USB stick). A right click on this icon shows shows "The permission of 4917-164C could not be determined".

A left click opens the flash memory's contents which permissions show I own and that I can add and remove files.

My problem sorted but surely this needs sorting out in the bigger picture.

---

### Post by cloyd on 2010-05-11
Needs sorting in the bigger picture. I agree. I've had trouble with USB drives from the start of my short Ubuntu experience. The problems have been tolerable, but only solved as work arounds, not by finding the real problem. As yet, I do not know why some usb drives will mount, some will not, or why the solution I suggested from the Ubuntu community documentation helped me.  

However, it is a problem I can live with. It is much easier to tolerate than some of my experience with that other OS.

---

### Post by Handssolow on 2010-05-11
more information on this thread-
[http://ubuntuforums.org/showthread.php?p=9283130#post9283130](http://ubuntuforums.org/showthread.php?p=9283130#post9283130)

---

### Post by pregiopomo on 2010-05-23
I've been having the same problem for a while, and I went for the   solution posted here (modyfing the etc/fstub) then I finally went to   test it with the laptop of a friend that recently installed Ubuntu   10.04, and on his computer everything worked fine.

So I checked out the Synaptic packages he had installed by default, and I   realized that I had some more that probably were creating some   conflicts/problems.

Now it works again!!

Here is what i did:

- start the "synaptic package manager"
- insert "usb" in the quick search
- compare your installed packages with the following list (these are the   one installed by default):
:arrow: 
 usbmuxd
    usbutils
      libusbmuxd1
      libusb-0.1-4
      libusb-1.0-0
      xserver-xorg-video-sisusb
      libmtp8
      usb-creator-gtk
      usb-creator-common
      libmobiledevice0
      libgphoto2-port0
      libgphoto2-2
      media-player-info
      libhpmud0
      hpijs
      hplip
:arrow:
- remove those packages that have been added by you or that may cause   conflicts, in my case I had all the previous ones and I removed the   following that I added months ago messing up with my laptop:

     :arrow: 
usbmount  (yep it sound weird, but now is working properly in my   laptop!)
       pyton usb
       usb creator
       gnome pilot
:arrow:

I hope this example might help some people as I did receive help reading   this forum, this is not "THE WAY" you "HAVE TO" follow to solve this   problem, but this is just a way that worked for me, and I think is worth   to be shared :wink:

---

### Post by Handssolow on 2010-06-15
Currently removing pmount, a power down then a reinstall of pmount seems to have solved this problem for me, thanks go to timgood.

[http://ubuntuforums.org/showthread.php?t=1469499&page=2](http://ubuntuforums.org/showthread.php?t=1469499&page=2)

---

### Post by tadcan on 2010-06-16
the pmount solution did not work for me.

Removing usbmount solved the issue for me

---

### Post by Handssolow on 2010-07-28
> **tadcan said:**
> the pmount solution did not work for me.

Removing usbmount solved the issue for me

I noticed today that this problem had recurred. Rather than remove and reinstall pmount as the solution that I had used before, this time I removed usb mount as suggested by tadcan. I can now plug in and use a usb stick or Micro SD without the problem of me needing root permission.

---

### Post by woodyg on 2010-10-09
Thanks for this. Removing USBmount worked for me as well.

---

