---
title: "Ubuntu 10.04 &amp; Full Disk Encryption"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by GaryLittlemore on 2010-04-26
I'm getting ready for the release of Ubuntu 10.04 in a few days time. I'm looking to do a fresh install and I'm wanting to do a full disk encryption.

What's the best way to do it?

---

### Post by Jon Monreal on 2010-04-26
The alternate install CD [offers this option]("http://www.phoronix.net/image.php?id=ubuntu_hdd_encrypt&image=ubuntu_encrypt_1"), and is probably the easiest way to do it (only downside being that debian-installer can be slow).

---

### Post by wconstantine on 2010-06-23
Is it possible to encrypt the system disk Ubuntu runs on after an install?

---

### Post by Jon Monreal on 2010-06-23
To the best of my knowledge, there's no way to do full disk encryption after install, because you would have to wipe existing partitions. You could back up your home folder, do a new install and still keep your files and configuration, but you would have to reinstall programs.

On the other hand, should home folder encryption be sufficient, there are [methods to do that]("http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html") after installation, but I would ensure that my data was properly backed up before attempting something like that.

---

### Post by Argentino on 2010-07-25
Hi,

Is it possible to encrypt a drive with multiple OSs?I got Win7 and Lucid running, with a 3rd partition with data.

So is there any way to encrypt the entire drive? (encrypting the data partition alone is not enough, you can still get my drive, mount it, and boot chrome, and get all my saved passwords! FUUUUUUUUUUUUUUUUUUUUUUUUUUUUUU)

I am happy to reinstall Lucid if need be. TrueCrypt in Windows allows me to encrypt the Windows installation and the 3rd partition, but wut bout Lucid?

Thanks!

---

### Post by JustinR on 2010-07-25
Just do full disk encryption on the hard drive in windows - then everything will be encrypted, including the Ubuntu partition.

---

### Post by Zzzzzzz1 on 2010-07-26
Justin-

How do you boot Lucid if the drive is encrypted from Windows?

---

### Post by JustinR on 2010-07-26
[QUOTE=Zzzzzzz1;9637803]Justin-

How do you boot Lucid if the drive is encrypted from Windows?[/QOUTE]

If I remember correctly, you could just do full disk encryption, then TrueCrypt attaches itself to the MBR - so then just enter in your password and GRUB should come up.

---

### Post by wconstantine on 2010-07-26
> **JustinR said:**
> [QUOTE=Zzzzzzz1;9637803]Justin-

How do you boot Lucid if the drive is encrypted from Windows?[/QOUTE]

If I remember correctly, you could just do full disk encryption, then TrueCrypt attaches itself to the MBR - so then just enter in your password and GRUB should come up.

I find it very weird that a full disk encryption can be done in Windows and not in Linux (by TrueCrypt that is).

---

### Post by Zorgoth on 2010-07-26
The Alternate Install CD will encrypt every partition on your hard drive EXCEPT that it will not encrypt /boot.  If you want encrypted /boot (i.e. you are either paranoid, have a very inflexible company policy, or are dealing with classified information or whatnot), you will need to do something special.  

One of my coworkers has a CD with his kernel on it and needs that to boot up (after booting he can take the CD out); that would be good as full disk encryption since the CD cannot be altered and the rest of the stuff is encrypted.

---

### Post by wconstantine on 2010-07-27
> **Zorgoth said:**
> The Alternate Install CD will encrypt every partition on your hard drive EXCEPT that it will not encrypt /boot.  If you want encrypted /boot (i.e. you are either paranoid, have a very inflexible company policy, or are dealing with classified information or whatnot), you will need to do something special.  

One of my coworkers has a CD with his kernel on it and needs that to boot up (after booting he can take the CD out); that would be good as full disk encryption since the CD cannot be altered and the rest of the stuff is encrypted.

I'm aware that the alternate install provides full disk encryption option. However, I don't have a cd-rom drive on my laptop. The alternate image can't be installed from USB. So, either Ubuntu fixes that or they add the encryption option on the desktop install.

---

### Post by Argentino on 2010-07-27
> **JustinR said:**
> Just do full disk encryption on the hard drive in windows - then everything will be encrypted, including the Ubuntu partition.

Thanks Justin, but TC tells me that it does not support encrypting the entire drive with multiple OSs. :( It tells me it will only encrypt the entire drive if there is only Win... no way am I giving up Lucid!

---

### Post by tarps87 on 2010-07-27
> **wconstantine said:**
> I'm aware that the alternate install provides full disk encryption option. However, I don't have a cd-rom drive on my laptop. The alternate image can't be installed from USB. So, either Ubuntu fixes that or they add the encryption option on the desktop install.

Have you tried unetbootin an passing it the alternative CD iso?
I have no actually tried this and am not in a position to test it for a while but I see not reason why it would not

---

### Post by iponeverything on 2010-07-28
> **wconstantine said:**
> I'm aware that the alternate install provides full disk encryption option. However, I don't have a cd-rom drive on my laptop. The alternate image can't be installed from USB. So, either Ubuntu fixes that or they add the encryption option on the desktop install.

I have 10.04 with full disk encryption installed from the 10.04 alternate image. It was installed from a USB stick created with the ubuntu usbstartup disk creator on a Ubuntu 9.10 machine.

---

### Post by joel1974 on 2010-07-31
How good is this full disk encryption?  Is it AES 256?

---

### Post by iponeverything on 2010-07-31
> **joel1974 said:**
> How good is this full disk encryption?  Is it AES 256?

On my laptop, I just went for the defaults when setting it up:

```

# cryptsetup status sda5_crypt
/dev/mapper/sda5_crypt is active:
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/sda5
  offset:  2056 sectors
  size:    624637944 sectors
  mode:    read/write

```

---

### Post by joel1974 on 2010-07-31
> **iponeverything said:**
> On my laptop, I just went for the defaults when setting it up:

```

# cryptsetup status sda5_crypt
/dev/mapper/sda5_crypt is active:
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/sda5
  offset:  2056 sectors
  size:    624637944 sectors
  mode:    read/write

```

That is what I need.  So I don't have to do anything?  Just do a click click next with the alt. cd?

---

### Post by iponeverything on 2010-08-01
yep

---

### Post by wconstantine on 2010-08-01
If you're one of many trying to install the alternate version using a USB-drive and it fails: report it [here]("https://bugs.launchpad.net/ubuntu/+bug/606215").

---

### Post by rchartra on 2010-08-18
Sorry to post to a stale thread; I wasn't sure whether this is preferable to starting a new thread on the same topic.

My question is odd: how do I tell what form of encryption I have?

I recently upgraded to Lynx using a CD (managing to wipe my hard drive in the process; oops!) and I don't recall what form of encryption I opted for.  Now my employer is requiring FDE on all laptops.  So I'd like to figure out what I did, and whether I need to re-install to get FDE.

Parroting earlier posts:
```
> ls /dev/mapper/
control  cryptswap1
> sudo cryptsetup status cryptswap1 
/dev/mapper/cryptswap1 is active:
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/sda5
  offset:  0 sectors
  size:    5191680 sectors
  mode:    read/write
```But I don't know enough to be able to parse that.  Home directory, or full disk?  If just home, am I going to have to re-wipe the hard drive to encypt?  (And if it is full disk, how do I prove that to my linux-challenged managers?)

---

### Post by Zorgoth on 2010-08-18
Well where is it mounted?

cat /etc/mtab

---

### Post by rchartra on 2010-08-18
```
$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
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
none /var/lib/ureadahead/debugfs debugfs rw,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home/rick/.Private /home/rick ecryptfs ecryptfs_sig=5b27ec9b6675738b,ecryptfs_fnek_sig=0b1e6ca8172de7f4,ecryptfs_cipher=aes,ecryptfs_key_bytes=16 0 0
gvfs-fuse-daemon /home/rick/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=rick 0 0
```sorta looks like it's the home directory that's encypted, though I don't really know what I'm looking at.

I have until Sep. 30 to comply.  If I do a fresh install anyway, is it sensible to just upgrade to the beta version of Meerkat when it gets to that point next month?

---

