---
title: "Browsing to a Windows XP share"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by oygle on 2014-02-20
From Kubuntu, I can browse okay to a Windows XP computer , using either Mozilla or Dolphin, by using this Samba share - smb://192.168.1.100/ .

Where is the Samba share located on the Kubuntu computer ? I looked in /home/username/.gvfs

---

### Post by sudodus on 2014-02-20
There is no samba share in Ubuntu flavour operating systems unless you install a samba server. And then you can configure it to be the directory (and subdirectories) that you want.

Browse the internet for tutorials, and find more links like these

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

---

### Post by Morbius1 on 2014-02-20
Don't use KDE enough - in fact I try to avoid it - but unless they've changed things KDE doesn't mount the share the way Gnome and Gnome-ish desktops do. There is no ".gvfs" mount point equivalent. 

I think that's why they invented smb4k which creates a mountpoint for these shares in your home directory.

---

### Post by SeijiSensei on 2014-02-20
If you want to mount a Windows share permanently, add an entry to /etc/fstab as described [here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently").

---

### Post by oygle on 2014-02-20
> **sudodus said:**
> There is no samba share in Ubuntu flavour operating systems unless you install a samba server. And then you can configure it to be the directory (and subdirectories) that you want.

Browse the internet for tutorials, and find more links like these

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

Thanks, I did read quite a few of those docs, and actualy installed a Samba share. However I still could not "see" the share via the file system, only via Firefox, Nautilus, Dolphin, KMail, OpenOffice,etc). I think all I did was to make the Ubuntu share available to the Windows XP box, which I don't want actually.

I only need to only see the Win XP share/s from Ubuntu, copy files to XP, but not let XP see Ubuntu. Possibly doing a mount will fix it for good. There was a doc there on mounting.

> **Morbius1 said:**
> Don't use KDE enough - in fact I try to avoid it - but unless they've changed things KDE doesn't mount the share the way Gnome and Gnome-ish desktops do. There is no ".gvfs" mount point equivalent. 

I think that's why they invented smb4k which creates a mountpoint for these shares in your home directory.

Seems KDE is working okay, it shows the Win XP share in the "open file" dialogue. Yes, a mount point is the way to go I think.

> **SeijiSensei said:**
> If you want to mount a Windows share permanently, add an entry to /etc/fstab as described [here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently").

Thanks, I was wondering where that doc was to do a mount permanently. I assume if the WinXP box is turned off, the mount command can be done manually when I turn the WinXP box on. If it's on when booting Ubuntu, then should be able to see it.

Thanks everyone for your help.

---

### Post by oygle on 2014-02-20
> **SeijiSensei said:**
> If you want to mount a Windows share permanently, add an entry to /etc/fstab as described [here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently").

I did as per those instructions and got this message

> mount error: could not resolve address for servername: Unknown error

$ **smbtree**
Enter ********* password: 
HOME
        \\ASUS32-XP                     asus32-xp

---

### Post by oygle on 2014-02-20
I changed a few things, but it didn't help. The Ubuntu computer is asus64 and the WinXP computer is asus32 (192.168.1.100)

fred@somewhere:~$ **cat /etc/hosts**
127.0.0.1       localhost
127.0.1.1       asus64
192.168.1.100   asus32

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
fred@somewhere:~$ 
fred@somewhere:~$ **nmblookup -A 192.168.1.100**
Looking up status of 192.168.1.100
        ASUS32-XP       <00> -         B <ACTIVE> 
        HOME            <00> - <GROUP> B <ACTIVE> 
        ASUS32-XP       <20> -         B <ACTIVE> 
        HOME            <1e> - <GROUP> B <ACTIVE> 
        HOME            <1d> -         B <ACTIVE> 
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 

        MAC Address = 00-00-00-00-00-00

fred@somewhere:~$ 
fred@somewhere:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=somenumbers /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=somenumbers /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=somenumbers none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//asus32/Win95B  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8  0  0

fred@somewhere:~$ 
fred@somewhere:~$ **sudo mount -a**
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
fred@somewhere:~$ 

The path /media/windowsshare is owned by root and the group is root. It is 755

Hmm, I can't paste a file into /media/windowsshare. Do I need to change the ownership of /media/windowsshare ?

---

### Post by oygle on 2014-02-20
Read quite a lot of posts. One mentioned that using the IP address got over some problems, so replaced this ..

> 
//**asus32**/Win95B /media/windowsshare cifs guest,uid=1000,iocharset=utf8 0 0


with

> 
//**192.168.1.100**/Win95B /media/windowsshare cifs guest,uid=1000,iocharset=utf8 0 0


and the sudo mount -a returned no errors. The mount worked okay. Why can't the host name be used though

---

### Post by oygle on 2014-03-17
I have this in /etc/fstab 

> 
//192.168.1.100/Win95B  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8  0  0


$ **sudo mount -a**
[sudo] password for ********: 
mount: wrong fs type, bad option, bad superblock on //192.168.1.100/Win95B,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

should the "cifs" be ntfs ?

---

### Post by oygle on 2014-03-17
Have got the share working again from Kubuntu 13.10. Obviously as I has a fresh install of Kubuntu, some things were not re-applied.

1. Modify /etc/hosts

**$ sudo kate  /etc/hosts**

add this line ..

192.168.1.100   asus32

2. Make sure ownership and group are not root 

**$ sudo chown -R boygle:boygle /media/windowsshare**

3. Installed the package cifs-utils

4. Try the mount again

**$ sudo mount /media/windowsshare**

it works !!  :D

---

