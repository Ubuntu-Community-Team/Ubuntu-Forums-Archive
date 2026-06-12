---
title: "fdisk -l/pvs no output - live CD/USB issue?"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by mjhess on 2009-12-25
Hello Forums:

I'm running Ubuntu 9.10 off a live USB while I figure out if everything is working before I make the switch and overwrite MSW. I'm trying to connect to a linux/ext3-based NAS (HP MV2120) for backups and found some instructions for using pvs and lvdisplay to do this. I installed lvm, but when I run the fdisk -l /dev/hda (or pvs, lvdisplay) I get no output, just the prompt back.

This is a little beyond my basic understanding. If the NAS is on the network, can I run fdisk or any of the other commands like this, or would this device have to be somehow physically connected to my computer? Are there limits with the live CD that prevent these commands from being run? I know the IP of the NAS and can ssh into it, but am I going about the mounting the wrong way? Is this a NAS issue, or a Ubuntu issue? How would I check?

Thanks for any pointers to help me along. Having access to that network backup device is one of the critical steps to pass before I leap.

Mike

---

### Post by bolucpap on 2009-12-25
I think you have to run the code with sudo to get any output from devices. sudo in the LiveCD has no password AFAIR.

---

### Post by mjhess on 2009-12-25
Sorry, I had already tried that. It that makes no difference.

ubuntu@ubuntu:~$ sudo fdisk -l /dev/hda
ubuntu@ubuntu:~$ 

If I run pvs, it actually complains that I am not running as root. Is there a big difference between running under sudo, or as root. I tried doing a "sudo su" which logs you into root, but there is no difference to the commands when run this way.

Thank You,
Mike

---

### Post by bolucpap on 2009-12-25
From what I can tell, there are no physical harddisks connected to your computer, is that correct? If so, fdisk would not give any output anyway. I am not familiar with the other commands you mention. If there _**is**_ a disk physically connected, be advised that as of Gutsy (if I recall correctly) Ubuntu does not name them as /dev/hda, /dev/hdb ,etc. but as /dev/sda, /dev/sdb. It used to be that SCSI disks began with s and IDE disks with h, but that is no longer the case. in any case, you can try running ```
sudo fdisk -l
``` to see a complete list of disks the operating system is recognizing at the moment.

Hope this helps,
Boluc

---

### Post by mjhess on 2009-12-26
Hello Boluc:

thank you. I suspected as much, that's why I posted this in the beginner's forum. If I do a "sudo fdisk -l" I see all internal drives as /dev/sda, the plugged in 4GB USB as /dev/sdb1, and an external HD as /dev/sdc1.

I am still wondering though about my beginner issue. How would I (windows-like) map a drive on a remote system (like //linuxbox/Documents) on my home network so it shows up in "Places" in Ubuntu for drag and drop capability of files?

I tried: 

   $ mkdir transfer
   $ sudo mount 192.168.1.210:/share/1000/Documents transfer

which gives me:

mount: wrong fs type, bad option, bad superblock on 192.168.1.210:/share/1000/Documents,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Sorry, at this point of my Linux exposure that makes awefully little sense.
What would I be looking for with dmesg, to determine what kind of helper program I would need?

Any pointers?

Thank You,
Mike

---

### Post by bolucpap on 2009-12-28
I think one can benefit a lot from reading this excellent thread when trying to use Samba/Windows shares:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by mjhess on 2009-12-28
Thanks for the pointer - that's some good reading material that I'll need to digest and try to apply. I was hoping that I would avoid Samba, since I'm going from Linux to a Linux NAS and have something straight forward, but doesn't look like it.

Thank You Again,
Mike

---

