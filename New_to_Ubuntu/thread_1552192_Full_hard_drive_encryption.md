---
title: "Full hard drive encryption"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by spyxter on 2010-08-13
Hey there,

I'm not sure if this belongs in the absolute beginners' corner, but I'll give it a shot. I would like to fully encrypt my hard drive where the OS is stored. I currently have a spare 40 gb hard drive and the newest release of alternate Xubuntu burned on a CD. My goal is to have an HDD useless without a key, such as a CD or a USB flash drive.

I've tried booting up the install cd and improvise; however, it was futile. I can't get the installer to put grub and /boot on a usb and it seems, my notebook can't boot up from a flash drive.

---

### Post by surfer on 2010-08-13
download the ubuntu-alternate iso and install from there.

what i usually do (partitionwise) is:

[LIST=1]
[*]crypto partition (random key) -> swap
[*]can do the same for /tmp if you like)
[*]ext2 partition (~256MB) /boot
[*]crypto partition (passphrase)
[LIST=1]
[*]LVM volume
[LIST=1]
[*]LVG home (ext4; /home)
[*]LVG root (ext4; /)
[/LIST]
[/LIST]
[/LIST]

---

### Post by Sunseeker.ch on 2010-08-13
Truecrypt supports now fully encrypted partitions.
Maybe you want to check that as well.

---

### Post by aeiah on 2010-08-13
whilst the /boot partition cant be encrypted, there's no reason to have this on your usb drive. all you need on there is a keyfile that can be used to unlock your system

---

### Post by aeiah on 2010-08-13
> **Sunseeker.ch said:**
> Truecrypt supports now fully encrypted partitions.
Maybe you want to check that as well.

this wont unencrypt a partition that contains the operating system though, and may not even allow you to unencrypt the home partition, surely?

---

### Post by spyxter on 2010-08-13
> **surfer said:**
> download the ubuntu-alternate iso and install from there.

what i usually do (partitionwise) is:

[LIST=1]
[*]crypto partition (random key) -> swap
[*]can do the same for /tmp if you like)
[*]ext2 partition (~256MB) /boot
[*]crypto partition (passphrase)
[LIST=1]
[*]LVM volume
[LIST=1]
[*]LVG home (ext4; /home)
[*]LVG root (ext4; /)
[/LIST]
[/LIST]
[/LIST]

Wouldn't /boot partition be visible and readable that way? I would like to have the whole disk encrypted, up to (and including if possible) the MBR. Is that even possible?

---

### Post by kiridude on 2010-08-13
Why would you want to encrypt /boot, mbr, etc?

I would imagine that whatever you wanted protected would be in your /home folder. Just encrypt that. As mentioned above, truecrypt is great for that.

---

### Post by surfer on 2010-08-13
you can not encrypt the boot partition, grub needs to be able to read and boot the kernel and the initrd.

if you are excessively paranoid, you could tweak an initrd that would unlock an encrypted /boot and restart from there. not sure if that is worth the pain... the kernel and the initrd are not that confidential after all. and if you are worried about the integrity, you could still do a checksum somewhere later in the boot process.

---

### Post by surfer on 2010-08-13
> **kiridude said:**
> Why would you want to encrypt /boot, mbr, etc?

I would imagine that whatever you wanted protected would be in your /home folder. Just encrypt that. As mentioned above, truecrypt is great for that.

/var may also be a good thing to encrypt. databases and other stuff stores data there.

---

### Post by Calash on 2010-08-13
It looks like there is a version of Pointsec that will work under Linux.  Have not read into the details but it may be what you need

[http://www.checkpoint.com/products/datasecurity/pc/](http://www.checkpoint.com/products/datasecurity/pc/)

Pointsec changes the MBR and then does a full drive encryption.  Your operating system needs a filter driver to decrypt on the fly.

Not a free solution but it may be what you need.


Side note, I would not recommend this for a personal PC unless you are just experimentation.  Getting around encryption if something goes wrong can be a several day nightmare, if it is possible at all.

---

### Post by bodhi.zazen on 2010-08-13
> **Sunseeker.ch said:**
> Truecrypt supports now fully encrypted partitions.
Maybe you want to check that as well.

Truecrypt will not support installing Linux into a fully encrypted partition, only windows.

---

### Post by bodhi.zazen on 2010-08-13
> **aeiah said:**
> whilst the /boot partition cant be encrypted, there's no reason to have this on your usb drive. all you need on there is a keyfile that can be used to unlock your system

Well ... for the ultraparaniod

If /boot is not encrypted, the kernel can be hacked, so I guess the thinking is to keep it on a separate USB.

---

### Post by spyxter on 2010-08-13
> **bodhi.zazen said:**
> Well ... for the ultraparaniod

If /boot is not encrypted, the kernel can be hacked, so I guess the thinking is to keep it on a separate USB.

how do I put /boot on say a CD and make grub boot from the same CD?

---

### Post by Paddy Landau on 2010-08-13
I don't know the answer, but I'm really curious. Why would you want to encrypt the root partition? It's only programs, right?

If it's /tmp that worries you, you could put that into its own encrypted partition (using ecryptfs just as /home does, or using TrueCrypt). Or, you could put it into your encrypted /home folder and mount it as /tmp.

---

### Post by ASchweitzer on 2010-08-13
Check out [this guide]("http://www.redmezzanine.com/?p=92&lang=en").
It's what I used to learn to encrypt my machines. If you want to make the machine bootable only off the usb stick, consider key files as mentioned above. I suppose you could try making the boot partition on the usb stick...

---

### Post by spyxter on 2010-08-13
No particular reason. It's more like an exercise to see if it's possible to have an HDD that is a mystery (not possible to deduce its partitioning, o even filesystems on partitions) without an external key.

---

### Post by surfer on 2010-08-13
i'd still recommend a dm-crypt container with LVM (linux volume manager) inside. just what the alternate installer cd lets you do. the alternate cd is then also a great tool if you run into trouble and need to fix things in the encrypted volumes.

---

### Post by bodhi.zazen on 2010-08-13
> **spyxter said:**
> how do I put /boot on say a CD and make grub boot from the same CD?

I am not sure how hard or easy it would be for you to do that. You will need to be willing to learn how to customize the live CD boot scripts and boot the hard drive.

In theory it should work, but I can not give you all the steps off the top of my head.

I simply use the defaults which gives me a /boot partition and a crypt, which is then configured with LVM into additional partitions.

Using keys and moving the boot partition can be done, and there are a number of guides on the LUKS home page, but they seem more hassle then it is worth. In order to crack the default set up one needs both physical access and a high skill level.

If you are worried, md5sum sha1sum ect the contents of /boot , or at least the kernels. Write a script to check the sums or use tripwire.

---

### Post by shadow120 on 2010-08-13
> **Paddy Landau said:**
> I don't know the answer, but I'm really curious. Why would you want to encrypt the root partition? It's only programs, right?

it contains more than programs but even if it didnt you can learn a lot about a pc from just the programs on it.  like if there are any programs with known vulnerabilities.  plus your password hash is stored there.

---

### Post by spyxter on 2010-08-26
> **ASchweitzer said:**
> Check out [this guide]("http://www.redmezzanine.com/?p=92&lang=en").
It's what I used to learn to encrypt my machines. If you want to make the machine bootable only off the usb stick, consider key files as mentioned above. I suppose you could try making the boot partition on the usb stick...

Thanks you for the link. I've managed to encrypt the system disk successfully while moving the /boot partition to a usb drive. Ubuntu boots perfectly and all, however; I've tried booting the same computer from a Ubuntu Live USB and I was able to see the encrypted volume and even unlock it with the passphrase. So I have a question, which part of the harddrive remains unencrypted as Ubuntu can still tell that said harddrive is encrypted?

---

### Post by ASchweitzer on 2010-08-26
Well, the partition tables cannot be encrypted, as they have to be read in order for the boot mechanism to mount the encrypted drives, and then decrypt them. However, unless you have the necessary tools (ie the programs on the Ubuntu liveCD) and the passphrase, you can't read the drives.

If you're really paranoid, check out some of the advanced features of TrueCrypt. They have some mechanisms to install systems that are in theory undetectable.

But of course there are always far more obvious vulnerabilities (not necessarily in security, but in exposure and privacy) than partition tables, like your browser.

---

### Post by ASchweitzer on 2010-08-26
> **spyxter said:**
>  So I have a question, which part of the harddrive remains unencrypted as Ubuntu can still tell that said harddrive is encrypted?

To be exact, I believe it's just the MBR that's unencrypted. That would contain your boot loader (not in your case, since it's on a boot partition on USB), and your partition tables.

---

