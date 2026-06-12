---
title: "HOWTO get an Airport Extreme card working on an Apple laptop"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by nixscripter on 2008-05-21
Hello everyone.

I just set up wireless on a new Ubuntu machine, which has an Airport Extreme card. It was slightly more manual, but it is a procedure I have repeated before. It is an older PowerBook G4, and these instructions are intended for vintage machines. I have also done this procedure under Gentoo on other machines. It is something once I saw documented, but has since disappeared. That's why I posted it.

The machine: Ubuntu 7.04 on a PowerBook G4 with an Apple Airport Extreme card.

Now this is a manual procedure, which was done right after installation.

You will need:

1. A (wired) internet connection.
2. A parallel Macintosh OS install, version 10.4 here. The procedure also has worked on Mac OS 10.3, but I don't know about 10.5.
3. A root terminal. All of these commands should be done as root. The shell is assumed to be in a safe directory, such as the home directory of the logged in user. If you open a terminal and just type ```
sudo -s
``` and then your password, you will satisfy this requirement.
4. The Broadcomm firmware cutter, downloadable here: [http://bu3sch.de/b43/fwcutter/bcm43xx-fwcutter-006.tar.bz2](http://bu3sch.de/b43/fwcutter/bcm43xx-fwcutter-006.tar.bz2). This tarball will be downloaded in the course of the instructions.

Procedure:

1. Mount the Macintosh partition and copy over the proprietary Apple driver.

First, determine what device your hard disk is.

```

mount

```

You should get a table something like this:

```

[color=red]/dev/hda6 on / type ext3 (rw,errors=remount-ro)[/color]
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-powerpc/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

The device on this machine is /dev/hda. Next, idenitfy the macintosh
partition using mac-fdisk:

```

mac-fdisk /dev/hda

```

In fdisk, do this. Bold things are input.

```

/dev/hda
Command (? for help): **p**
/dev/hda
#                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap bootstrap               1600 @ 64        (800.0k)  NewWorld bootblock
/dev/hda3              Apple_Free Extra                 260544 @ 1664      (127.2M)  Free space
[color=red]/dev/hda4               Apple_HFS Apple_HFS_Untitled_5 112984064 @ 262208    ( 53.9G)  HFS[/color]
/dev/hda5         Apple_UNIX_SVR2 swap                 2097152 @ 113246272 (  1.0G)  Linux swap
/dev/hda6         Apple_UNIX_SVR2 root                40958064 @ 115343424 ( 19.5G)  Linux native

Block size=512, Number of Blocks=156301488
DeviceType=0x0, DeviceId=0x0

Command (? for help): **q**

```

So, the partition in this example is /dev/hda4. Mount it with gnome (to avoid having to set up a mount point and other stuff).

```

gnome-mount -d /dev/hda4 --mount-options ro

```

This should make the volume appear on the desktop. The read only is just to avoid accidents.

Now, copy over the proper driver file. Assuming the volume name is "Macintosh HD":

```

cp "/media/Macintosh HD/System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2" .

```

2. Extract the firmware from the driver file.

This will require building the tool from source. If this is a new installation (it was in my case), or build errors occur, then the build tools will need to be installed first.

```

apt-get update
apt-get install build-essential

```

Say yes to the build if asked. Now, build the firmware cutter.

```

wget 'http://bu3sch.de/b43/fwcutter/bcm43xx-fwcutter-006.tar.bz2'

```

Now, continue with the unpacking and building.

```

tar xjf bcm43xx-fwcutter-006.tar.bz2
cd bcm43xx-fwcutter-006
make

```

Lastly, run the utility and cut up the firmware.

```

./bcm43xx-fwcutter -w /lib/firmware ../AppleAirPort2

```

The output should include near the end of a long list of stuff:

```

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...

```

You may need to reload the module for the driver in order to make it to work. Once this is done, the card should begin working immediately:

```

modprobe bcm43xx

```

Configure it as a normal network interface (like with the wireless applet or whatever). That's it!

---

