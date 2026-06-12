---
title: "Edit fstab for permissions?"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by BikeHelmet on 2009-10-13
Hi. I need to change my fstab so that my mounted partitions are owned by the current user. It's highly annoying going onto my storage drive, and not being able to save anything with gedit.

```
UUID="Really_Long_UUID" /media/Storage ext3 defaults 0 0
```

I searched Google for the answer, but it kept taking me to threads where people said they knew the answer, and didn't provide any examples or further posts.

Cheers!... if you can help. :)

---

### Post by oldfred on 2009-10-14
Some references:
[http://ubuntuforums.org/showthread.php?t=283131.https://help.ubuntu.com/community/Fstab](http://ubuntuforums.org/showthread.php?t=283131.https://help.ubuntu.com/community/Fstab)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I copied this from some thread:
in case of an ext4 partition that would be:
UUID=26c15cb4-55f8-44da-acb2-0f363040192e   /home    ext4  defaults 0    1

# The fourth field, (fs_mntops), describes the mount options associated with the filesystem.
defaults = rw, suid, dev, exec, auto, nouser and async

Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async

So, I would replace defaults with relatime:
[COLOR=DarkRed]UUID=26c15cb4-55f8-44da-acb2-0f363040192e   /home    ext4  relatime    0    1
[/COLOR]
For more details please read man mount.

# The sixth field, (fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time. The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2.

These are some of my entries which from above have redundant parameters but work:
# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05 /home/fred/data ext3 auto,users,rw,relatime 0 2
# Entry for /dev/sda2 :
UUID=13a684e4-2849-4566-9528-21cd07028a9a /home/fred/backup ext3 auto,users,rw,relatime 0 2

---

### Post by BikeHelmet on 2009-10-15
Well, apparently that was only half my problem. I no longer get locks on files, but gedit still refuses to save. The folder is owned by the current user, but... nope! :P

---

### Post by tarps87 on 2009-10-15
Can you create/rename files/folders?

---

### Post by aheckler on 2009-10-15
Try this:

```
sudo chown -R user:user /media/Storage
sudo chmod -R 755 /media/Storage
```

Replacing "user" with your username, of course.

---

### Post by BikeHelmet on 2009-10-15
> **tarps87 said:**
> Can you create/rename files/folders?
Yes.
> **aheckler said:**
> Try this:

```
sudo chown -R user:user /media/Storage
sudo chmod -R 755 /media/Storage
```

Replacing "user" with your username, of course.
Done. Still can't save with gedit.

---

### Post by Paqman on 2009-10-15
What are the permissions set as on the file you're trying to save? The commands you were given should have given you ownership and read/write/execute permissions on everything.

---

### Post by kayvortex on 2009-10-15
In your fstab file, you will need to specify the group and umask for the partition. I use the following options in the options list:

> /dev/sda6  /mnt/sda6 ntfs **defaults,rw,nodev,auto,noexec,nosuid,user,umask=007,gid=46**  0  0

Yes, it's a bit superfluous to have defaults and all that other stuff, and it's for an ntfs partition, but the pertinent information is "umask=007" and "gid=46".

The umask option tells mount to exclude those file permissions by default. So, my umask=007 sets a default file permission of rwxrwx--- for files/directories. You can set a dmask value specifically for directories. The gid option sets the group owner for the files. A gid value of 46 is for the group "plugdev", which is what I use for my ntfs partitions, but you can use "gid=1000", which will set the group to your username. You can also specify a uid value for the file owner group. So, your fstab entry could be:

UUID="blah_blah"  /media/Storage  ext3  defaults,umask=133,dmask=022,uid=1000,gid=1000  0  2

which will set the files in /media/Storage to have the same file permissions and owners as for files/directories in your home folder.

---

### Post by tarps87 on 2009-10-16
The post above should solve the problem, if you are still having problems can you please post the output of
```
ls -l /*pathToDevice/*
```

---

### Post by BikeHelmet on 2009-10-16
> **Paqman said:**
> What are the permissions set as on the file you're trying to save? The commands you were given should have given you ownership and read/write/execute permissions on everything.

The permissions were set the same before and after running the commands.

> **kayvortex said:**
> UUID="blah_blah"  /media/Storage  ext3  defaults,umask=133,dmask=022,uid=1000,gid=1000  0  2

which will set the files in /media/Storage to have the same file permissions and owners as for files/directories in your home folder.

I tried those mount options, and then similar ones, and then a dozen combinations of them. It fails to mount with any combo, and just complains about "Invalid Mount Option". After an hour of fighting with it, I had to use MountManager to un-corrupt my fstab.

> **tarps87 said:**
> The post above should solve the problem, if you are still having problems can you please post the output of
```
ls -l /*pathToDevice/*
```

brw-rw---- 1 root disk 8, 0 2009-10-16 17:46 /dev/sda

Could this help?

[http://img48.imageshack.us/img48/6724/failuresavinggeditubunt.png](http://img48.imageshack.us/img48/6724/failuresavinggeditubunt.png)

---

### Post by oldfred on 2009-10-17
give us a list of mounted partitions:

```
mount
```

and 

```
ls - l /media/Storage
ls -l /dev/disk/by-uuid
```

---

### Post by kayvortex on 2009-10-18
OK, let's go back a step. First, could you unmount the partition: enter
```
sudo umount -v /dev/disk/by-uuid/*YOUR_UUID*
```

(This won't work if the partition is being used -- so make sure it's not being used -- and will warn you if it's not already mounted, which is OK).

Now, when the partition has been unmounted, enter:
```
sudo mkdir -v -p /mnt/test && sudo mount -v -t ext3 -o rw,gid=1000,uid=1000,umask=133,dmask=022 /dev/disk/by-uuid/*YOUR_UUID* /mnt/test
```

(Note: there should be no spaces between the commas: just copy and paste the whole command in and **put your UUID in place of** "*YOUR_UUID*").

Post any error messages from that command. If it's successful, then your partition should now be writeable from your usual login account: try it and post the output of:
```
mount
```
*if* any problems occur about not being able to save changes to files.

If, however, you *can* make changes to your files, then unmount and remove that directory:
```
sudo umount -v /mnt/test && sudo rmdir -v /mnt/test
```
and could you post your "fstab" file and I'll post back what changes you need to make and where.

---

### Post by BikeHelmet on 2009-10-18
```
sudo mkdir -v -p /mnt/test && sudo mount -v -t ext3 -o rw,gid=1000,uid=1000,umask=133,dmask=022 /dev/disk/by-uuid/YOUR_UUID /mnt/test

->

sudo mkdir -v -p /mnt/test && sudo mount -v -t ext3 -o rw,gid=1000,uid=1000,umask=133,dmask=022 /dev/disk/by-uuid/e8830231-78af-4736-b722-b19ac9123617 /mnt/test

mkdir: created directory `/mnt/test'
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

->

dmesg | tail

[168421.074586] EXT3-fs: Unrecognized mount option "gid=1000" or missing value
```
?

---

### Post by ikisham on 2009-10-18
All you need is replace **defaults** for **auto,users,exec,relatime** in the line of your first post.

Then if for some reason it's still owned by root, open nautilus as root ```
gksudo nautilus
```, navigate to the partition, right click in a blank space, properties, permissions and set yourself as owner with permission to read and write and for all the subfolders to inherit that.

---

### Post by BikeHelmet on 2009-10-18
> **ikisham said:**
> navigate to the partition, right click in a blank space, properties, permissions and set yourself as owner with permission to read and write and for all the subfolders to inherit that.
Still can't save with gedit. But thanks for repeating what other people suggested, and what I had already done.

---

### Post by LeChacal on 2009-10-18
How about if you open gedit as root can you save things to the storage drive?
```
gksu gedit
```

---

### Post by BikeHelmet on 2009-10-18
> **LeChacal said:**
> How about if you open gedit as root can you save things to the storage drive?
```
gksu gedit
```

Yes. That works fine. But that's the issue I'm trying to figure out: *Why do I have to be root for folders that I own?*

[http://img48.imageshack.us/img48/6724/failuresavinggeditubunt.png](http://img48.imageshack.us/img48/6724/failuresavinggeditubunt.png)

Why does it say saving has been disabled by the admin? Google isn't bringing anything up.

---

### Post by oldfred on 2009-10-18
Post fstab contents and sudo fdisk -l

It is behaving as is your partition is ntfs or fat not ext3. You can only set ntfs permissions at mount.

---

### Post by kayvortex on 2009-10-18
> mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Is the partition formatted as ext3? Because, apparently, *mount* seems to be saying it is not. This is a little confusing, since it contradicts the fstab entry that was posted at the start, which is what I've been working off.

Let's start from square one: before I give you any commands to enter or changes to make, could you first tell me what the partition you're trying to mount is, how it is currently mounted, and what's in your /etc/fstab file. (You can just post the output of
```
sudo fdisk -l && mount && cat /etc/fstab
```
if you can't be bothered to write it all down yourself!).

---

### Post by BikeHelmet on 2009-10-19
```
bikehelmet@via-Ubuntu:~$ sudo fdisk -l
[sudo] password for bikehelmet: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000020

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb6bdb6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6607fee8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008695c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641   83  Linux

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00019cfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            6142        6206      522112+  82  Linux swap / Solaris
/dev/sde2   *           1        6141    49327551   83  Linux

Partition table entries are not in disk order

```
I formatted these in gparted to ext3. I remember it well, because Ubuntu had just barfed on my old NTFS partitions. I wiped the drives completely and started over.

```
/dev/sde2 on / type ext3 (rw,noatime)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /media/Storage_D0 type ext3 (rw,noatime)
/dev/sdb1 on /media/Storage_C1 type ext3 (rw,noatime)
/dev/sdc1 on /media/Storage_B2 type ext3 (rw,noexec,nosuid,nodev,noatime)
/dev/sdd1 on /media/Storage_A3 type ext3 (rw,noatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

```
UUID=65cb94a7-5ab0-4e14-8ebd-9077b49a6d2b /media/Storage_D0 ext3 noatime 0 2
UUID=e54893a9-2de7-46c1-bef3-5c7aa4002cf7 /media/Storage_C1 ext3 noatime 0 2
UUID=e8830231-78af-4736-b722-b19ac9123617 /media/Storage_B2 ext3 noatime,users	0 2
UUID=3fdb17ae-8ed4-4a71-87a4-46544e2c2b6e /media/Storage_A3 ext3 noatime 0 2
UUID=622ee070-054f-4f17-b06a-e680cc34a330 swap swap sw 0 0
UUID=0ca3f120-361c-4c5b-a9a1-f50a95c7d5fe / ext3 noatime 0 0
```

B2 is the drive I've been testing different options on. A heck of a lot of them cause it to disappear and become unmountable.

I'm still not convinced this partition stuff is related to gedit misbehaving. Nothing else is malfunctioning... :confused:

---

### Post by hopelessone on 2009-10-19
Can you create NEW folders on this drive?

From the community Docs:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

read from **Mount The Drive**

---

### Post by BikeHelmet on 2009-10-19
Yes. I can create folders and new files just fine - except in gedit.

---

### Post by kayvortex on 2009-10-19
I'm beginning to think the problem lies with your user/group settings. Could you post the output of:
```
ls -ld /media/Storage_B2
```
so that I can make sure your directory permissions are OK.

The error message from dmesg:
> [168421.074586] EXT3-fs: Unrecognized mount option "gid=1000" or missing value
is VERY suspicious.

Let me check your user/group settings -- could you post the outputs of:
```
env
```
```
cat /etc/group
```
```
cat /etc/passwd
```

I'm willing to bet that if you created a new user account, you'll be able to write with gedit OK (that's one "solution" that you might have to take, but it'll involve a bit of work).

---

### Post by BikeHelmet on 2009-10-19
```
bikehelmet@via-Ubuntu:~$ ls -ld /media/Storage_B2
drwxr-xr-x 6 bikehelmet bikehelmet 4096 2009-10-17 03:01 /media/Storage_B2
```

```
bikehelmet@via-Ubuntu:~$ env
ORBIT_SOCKETDIR=/tmp/orbit-bikehelmet
SSH_AGENT_PID=3042
GPG_AGENT_INFO=/tmp/seahorse-Toueq4/S.gpg-agent:3065:1
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=35fc667639fd90646b29f8b949fcaf22-1255950847.819586-243220410
GTK_RC_FILES=/etc/gtk/gtkrc:/home/bikehelmet/.gtkrc-1.2-gnome2
WINDOWID=48234545
GTK_MODULES=canberra-gtk-module
USER=bikehelmet
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
SSH_AUTH_SOCK=/tmp/keyring-m55Z83/socket.ssh
GNOME_KEYRING_SOCKET=/tmp/keyring-m55Z83/socket
SESSION_MANAGER=local/via-Ubuntu:/tmp/.ICE-unix/2927
USERNAME=bikehelmet
DESKTOP_SESSION=default
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
GDM_XSERVER_LOCATION=local
PWD=/home/bikehelmet
LANG=en_CA.UTF-8
GDM_LANG=en_CA.UTF-8
GDMSESSION=default
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/bikehelmet
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=bikehelmet
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-7qUiTqV0IJ,guid=0be11723cb75cda90536d1724adc4a01
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/bikehelmet/.Xauthority
_=/usr/bin/env
```

```
bikehelmet@via-Ubuntu:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:bikehelmet
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:bikehelmet
fax:x:21:
voice:x:22:
cdrom:x:24:bikehelmet
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:bikehelmet
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
fuse:x:104:
ssl-cert:x:105:
lpadmin:x:106:bikehelmet
crontab:x:107:
mlocate:x:108:
ssh:x:109:
avahi-autoipd:x:110:
gdm:x:111:
netdev:x:112:
saned:x:113:
pulse:x:114:
pulse-access:x:115:
pulse-rt:x:116:
messagebus:x:117:
polkituser:x:118:
avahi:x:119:
haldaemon:x:120:
admin:x:121:bikehelmet
bikehelmet:x:1000:
sambashare:x:122:bikehelmet
winbindd_priv:x:125:
ntp:x:126:
```

```
bikehelmet@via-Ubuntu:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
hplip:x:103:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:105:111:Gnome Display Manager:/var/lib/gdm:/bin/false
saned:x:106:113::/home/saned:/bin/false
pulse:x:107:114:PulseAudio daemon,,,:/var/run/pulse:/bin/false
messagebus:x:108:117::/var/run/dbus:/bin/false
polkituser:x:109:118:PolicyKit,,,:/var/run/PolicyKit:/bin/false
avahi:x:110:119:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:111:120:Hardware abstraction layer,,,:/var/run/hald:/bin/false
bikehelmet:x:1000:1000:BikeHelmet,,,:/home/bikehelmet:/bin/bash
ntp:x:113:126::/home/ntp:/bin/false
```

Creating a new user account is more trouble than it's worth. I can just use another text editor. :P

---

### Post by oldfred on 2009-10-20
You do not have write permissions, rwx for the group and others only for the owner? are you not the owner? are you logged in as something other than bikehelmet?:

drwxr-xr-x 6 bikehelmet bikehelmet 4096 2009-10-17 03:01 /media/Storage_B2
Try changing permissions to 777 everyone has rwx read, write , execute

sudo chmod -R 777 /media/Storage_B2

---

### Post by BikeHelmet on 2009-10-20
I think you got that backwards. Owner has write, group doesn't.

Okay, I applied those permissions. It's correctly showing up as enabled for all of them.

Still can't save in gedit.

---

### Post by tarps87 on 2009-10-20
Sorry when I said path to device I meant path to mount.
Looking at you posts it should be:
ls -l /media/Storage_B2/
or
ls -l /media/Storage_B2/*

Basically I want to check that the files have the correct permission.

---

### Post by kayvortex on 2009-10-20
> Creating a new user account is more trouble than it's worth. I can just use another text editor.

Man, I don't know what to tell you: there's nothing in any of the stuff you posted that looks odd. Maybe just using a different editor is the easiest "solution". (I use vim, personally -- you can install gvim if you want to try a GUI version out.)

The problem doesn't *seem* to be any file/directory permissions issue for two reasons: first of all, the permissions all look OK; and secondly, the gedit error is "You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again." for permissions issues (I've even looked at changing chattr attributes, and it's the same message; and for a read-only mount it's "You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again.").

Bearing in mind the error in trying to mount the partition, all I can think is try running a fsck on /dev/sdc1 to see if there are any problems with the partition. But, it's a wild stab in the dark that still doesn't explain why only gedit can't save files. There *may* be an issue in some gedit/GNOME configuration file (although I didn't find anything really pertinent in gconf-editor), but I don't know enough about the low-level GNOME stuff in order to suggest anything I'm afraid.

Incidently, if we're going down the road of wild stabs, you could also try:
[LIST=1]
[*]Does editing with superuser account allow you to save? Open gedit as:```
gksudo gedit
```
[*]You could try reinstalling gedit: ```
sudo aptitude reinstall gedit
```
[*]Err, that's all I can think of right now.
[/LIST]

The only other thing I can suggest is simply to post the error in a GNOME forum and ask what issue could be the source of that *particular* error message, because I'll be buggered if I can work this one out.

Sorry I couldn't be any more help, really.

---

### Post by tarps87 on 2009-10-20
> **BikeHelmet said:**
> 
Creating a new user account is more trouble than it's worth. I can just use another text editor. :P

Hang on I missed this, it sounds like it is a problem with gedit
```
sudo apt-get purge gedit && sudo apt-get update && sudo apt-get install gedit
```

---

### Post by BikeHelmet on 2009-10-21
> **kayvortex said:**
> [*]Does editing with superuser account allow you to save? Open gedit as:```
gksudo gedit
```
Yes.
> **kayvortex said:**
> [*]You could try reinstalling gedit: ```
sudo aptitude reinstall gedit
```
[*]Err, that's all I can think of right now.
[/LIST]
Tried that just now. No luck. :(

> **kayvortex said:**
> 
The only other thing I can suggest is simply to post the error in a GNOME forum and ask what issue could be the source of that *particular* error message, because I'll be buggered if I can work this one out.

Sorry I couldn't be any more help, really.
Alright. I'll head over there sometime and see if any of them have the answer. Thanks anyway! :)

> **tarps87 said:**
> Hang on I missed this, it sounds like it is a problem with gedit
```
sudo apt-get purge gedit && sudo apt-get update && sudo apt-get install gedit
```

No luck - didn't work.

---

