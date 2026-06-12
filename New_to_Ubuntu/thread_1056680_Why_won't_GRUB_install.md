---
title: "Why won't GRUB install??"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by doctorbighands on 2009-02-01
I'm trying to finish up an installation using the instructions found here ([https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)). I'm to the point where I need to install GRUB, but it won't let me.

I try the following commands:```
grub-install /dev/hda
```and```
grub-install /dev/hda1
``` and it tells me that /dev/hda1 doesn't exist.

I know it exists, because I just installed Ubuntu there! It shows up in my /etc/fstab, too. Why is this happening, and how can I install GRUB?

---

### Post by Crafty Kisses on 2009-02-01
Is /dev/hda1 mounted?

---

### Post by HotShotDJ on 2009-02-01
Are you sure that your drive is /dev/hda?  Try using /dev/sda. Don't include the partition number (ie /dev/sda1).  You might also try using "grub notation" rather than the device file:```
grub-install hd0
```

---

### Post by doctorbighands on 2009-02-01
I just tried```
mount /dev/hda1
```and the reply was```
mount: special device /dev/hda1 does not exist
```

Then I tried```
grub-install hd0
```and the reply was```
/dev/hda1: Not found or not a block device.
```

As I said before, I know the root partition is /dev/hda1 because that's what it says in /etc/fstab.

---

### Post by Crafty Kisses on 2009-02-01
That's really weird, what are the results of this command?
```
dmesg | grep 'hd'
```

---

### Post by HotShotDJ on 2009-02-01
First... try using sudo grub-install hd0.  If that doesn't help and you are using the LiveCD (Ubuntu installation CD) try the following:```
sudo mkdir /mnt/root
sudo mount /dev/hda1 /mnt/root
sudo grub-install hd0
```Don't forget to umount /mnt/root before you shut down.

---

### Post by doctorbighands on 2009-02-01
The results are as follows:
```

e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:pio, hdd:pio
hda: HTS541010G9AT00, ATA DISK drive
hda: max request size: 512KiB
hda: 195371568 sectors (100030 MB) w/7539KiB Cache, CHS=16383/255/63, UDMA (100)
hda: cache flushed supported
 hda: hda1 hda2 < hda5 >
EXT3 FS on hda1, internal journal

```

---

### Post by doctorbighands on 2009-02-01
bump!

---

### Post by HotShotDJ on 2009-02-01
> **doctorbighands said:**
> bump!If none of my suggestions helped (I guess I can safely assume they didn't, your you wouldn't have bumped your thread) then I am officially perplexed.  You've run into an installation problem that I've never run across before.  I'm sorry I couldn't be more helpful.

---

### Post by doctorbighands on 2009-02-01
> **HotShotDJ said:**
> If none of my suggestions helped (I guess I can safely assume they didn't, your you wouldn't have bumped your thread) then I am officially perplexed.  You've run into an installation problem that I've never run across before.  I'm sorry I couldn't be more helpful.

I get the same message no matter what I try: "not found or not a block device." Thank you for your help, though!

I'm stumped as well. How frustrating!

---

### Post by cariboo on 2009-02-01
Did you try using /dev/sda? If you are geting the message that /dev/hda is not a valid block device, then you have a problem. What is the output of:

```
sudo fdisk =l
```

The above command will list your hard drives and partitions.

Jim

---

### Post by doctorbighands on 2009-02-01
In the installation instructions, it asks for```
mount -t proc proc /proc
```

Could that command have something to do with this problem? I know I'm probably grasping at straws, but there must be SOME explanation for this.

---

### Post by xeth_delta on 2009-02-01
Could you please post the output of:
```
sudo mount
```
```
sudo sfdisk -l
```

---

### Post by doctorbighands on 2009-02-01
> **xeth_delta said:**
> Could you please post the output of:
```
sudo mount
```
```
sudo sfdisk -l
```

The first command returns```
/dev/hda1 on / type ext3 (rw,data=ordered)
/proc on /proc type proc (rw)
```

The second command returns nothing.

---

### Post by orethrius on 2009-02-01
> **doctorbighands said:**
> The first command returns```
/dev/hda1 on / type ext3 (rw,data=ordered)
/proc on /proc type proc (rw)
```

The second command returns nothing.

He means
```
sudo fdisk -l
```

---

### Post by doctorbighands on 2009-02-01
"fdisk -l" returns nothing.

---

### Post by xeth_delta on 2009-02-01
> **doctorbighands said:**
> "fdisk -l" returns nothing.

That's odd. "sfdisk" and "fdisk" (both are valid commands) should have returned something, taking into account that "mount" shows hda1 mounted on /

Please post the output of
```
sudo parted /dev/hda print
```

---

### Post by doctorbighands on 2009-02-01
> **xeth_delta said:**
> That's odd. "sfdisk" and "fdisk" (both are valid commands) should have returned something, taking into account that "mount" shows hda1 mounted on /

Please post the output of
```
sudo parted /dev/hda print
```

That command returns "bash: parted: command not found"

Thinking it was a missing application, I tried "apt-get install parted" which returned```

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

```

Maybe it's me, but this seems strange also.

---

### Post by orethrius on 2009-02-01
> **doctorbighands said:**
> That command returns "bash: parted: command not found"

Thinking it was a missing application, I tried "apt-get install parted" which returned```

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

```

Maybe it's me, but this seems strange also.

It almost seems like a **chroot** issue at this point, though I can't think of the remedy at the moment.

---

### Post by doctorbighands on 2009-02-01
I'd try a reboot, but I'm a little afraid to since, well...I can't install GRUB!

---

### Post by Crafty Kisses on 2009-02-01
Do you get any results from the following?
```
sudo fdisk -lu
```
If you get nothing from that, then we may have another issue on our hands, but as far as the GRUB installation goes, you can try the following and see if you get any different results:
```
chroot /mnt
grub-install /dev/hda*
```

---

### Post by doctorbighands on 2009-02-01
> **Codename said:**
> Do you get any results from the following?
```
sudo fdisk -lu
```
If you get nothing from that, then we may have another issue on our hands, but as far as the GRUB installation goes, you can try the following and see if you get any different results:
```
chroot /mnt
grub-install /dev/hda*
```

```
fdisk -lu
```returns nothing.

```
chroot /mnt
```returns```
chroot: cannot run command '/bin/sh': No such file or directory
```

---

### Post by igknighted on 2009-02-01
Can you run the command 'cat /etc/lsb-release'?

Between looking at those instructions you used, and fact that your HDD is labeled as hda (this notation was deprecated around 3 or 4 releases ago), I suspect that you are using an ancient and likely unsupported release (there was a Warty reference in your guide, and the current Debian release was Sarge).  You won't be able to install anything because the repositories for such an old release have long since been shut down (you might find a random mirror somewhere though).

Before we get ahead of ourselves, post the output of that command and we'll see what we are dealing with.

---

### Post by doctorbighands on 2009-02-01
That command returns```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

```

I substituted "intrepid" everywhere that I saw a reference to an older release, including debootstrap. Perhaps I missed something, but this is the second time I've tried installing this way and I was pretty careful.

---

### Post by xeth_delta on 2009-02-01
> **doctorbighands said:**
> That command returns "bash: parted: command not found"

Thinking it was a missing application, I tried "apt-get install parted" which returned```

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

```

Maybe it's me, but this seems strange also.

I think "sudo" is missing from that call to apt-get.

Have you had a look at this great thread: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) ?

---

### Post by doctorbighands on 2009-02-01
I've been omitting "sudo" as I'm logged in as root right now.

EDIT: The info in that thread wouldn't help, unfortunately, because I don't have a functional optical drive right now. That's why I had to install Ubuntu using floppies.

---

### Post by yeats on 2009-02-01
I would consider this as an option:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#GRUB]("http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#GRUB")

It is also older and out-of-date (referring to Ubuntu 6.10), but so are floppies :-).

If you're able to create a boot floppy, that will at least give you a fallback position for booting without GRUB on your hard drive.

---

### Post by caljohnsmith on 2009-02-01
It looks to me like the tutorial you followed from the Ubuntu help pages may not be entirely complete in its directions. How about before you chroot, try doing:
```
sudo mount --bind /dev /target/dev
```
Then chroot, mount /proc, and check that your drives now show:
```
sudo chroot /target
mount -t proc proc /proc
fdisk -lu
```
By the way, when you chroot you will be root user, so there is no need to use "sudo" with the commands after chrooting. If fdisk shows your drive, then proceed with:
```
grub-install /dev/sda
```
Replace sda with hda or wichever is the drive Ubuntu is on. Let me know if that works OK or if you still run into problems.

---

### Post by doctorbighands on 2009-02-01
> **caljohnsmith said:**
> It looks to me like the tutorial you followed from the Ubuntu help pages may not be entirely complete in its directions. How about before you chroot, try doing:
```
sudo mount --bind /dev /target/dev
```
Then chroot, mount /proc, and check that your drives now show:
```
sudo chroot /target
mount -t proc proc /proc
fdisk -lu
```
By the way, when you chroot you will be root user, so there is no need to use "sudo" with the commands after chrooting. If fdisk shows your drive, then proceed with:
```
grub-install /dev/sda
```
Replace sda with hda or wichever is the drive Ubuntu is on. Let me know if that works OK or if you still run into problems.

After all of that, I'm now getting a new error message after I run "grub-install /dev/hda". Maybe that means progress! :) The message is...```
/dev/ide/host0/bus0/target0/lun0/disc does not have any corresponding BIOS drive.
```

---

### Post by caljohnsmith on 2009-02-01
Did you run the "fdisk -lu" command first, and did it show your drives and partitions? If so, how about posting the output.

---

### Post by doctorbighands on 2009-02-01
> **caljohnsmith said:**
> Did you run the "fdisk -lu" command first, and did it show your drives and partitions? If so, how about posting the output.

```

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009eda5

   Device Boot      Start         End     Blocks   Id  System
/dev/hda1   *          63   191591189   95795563+  83  Linux
/dev/hda2       191591190   195366464    1887637+   5  Extended
/dev/hda5       191591253   195366464    1887606   82  Linux swap / Solaris

```

At least it outputs something now. That's an improvement!

---

### Post by caljohnsmith on 2009-02-01
OK, you're definitely making progress. I think that error you received from grub-install may be just fine, because it was just telling you about a bogus drive. In other words, you may have Grub installed successfully to the MBR of hda if grub-install didn't output any other errors. How about checking with:
```
hexdump -n 2 -e '"%x\n"' /dev/hda
hexdump -s 1049 -n 2 -e '"%x\n"' /dev/hda
```
The first command should output "48eb", and the second command should output "ff00". If they do, reboot, cross your fingers, and see if you get Grub on start up.

---

### Post by doctorbighands on 2009-02-01
I tried the first command and received```
bash: hexdump: command not found
```

---

### Post by caljohnsmith on 2009-02-01
> **doctorbighands said:**
> I tried the first command and received```
bash: hexdump: command not found
```
Did you run that command while you were chrooted into /target? Because your Ubuntu install should have that command. If not, how about rebooting anyway and let me know if you get Grub on start up or not.

---

### Post by doctorbighands on 2009-02-01
I just tried the command "chroot /target" and received```
chroot: cannot change root directory to /target: No such file or directory
```
Should I still try to reboot?

---

### Post by caljohnsmith on 2009-02-01
Well /target was the directory they were using in that tutorial to mount your Ubuntu install to, so I assumed that's what you've been using up until now. When you previously ran the chroot command and then the grub-install command, which directory did you chroot into? Was it /target? Anyway, I definitely think it's time for a reboot whether Grub got installed or not, so how about doing that and let me know what happens. :)

---

### Post by doctorbighands on 2009-02-01
Reboot not successful. I get "error loading operating system".

EDIT: I just attempted to boot using Super Grub Disk. It dropped to a BusyBox shell after the message, "ALERT! /dev/hda1 does not exist. Dropping to a shell!"

---

### Post by caljohnsmith on 2009-02-01
Do you just have the one 100 GB HDD, or do you have other HDDs? How copying/pasting your entire terminal session where you run all the commands leading up to chrooting. Once you've chrooted, how about also posting:
```
ls -l / /usr/bin/h*
```
And again, just copy everything in your terminal session so maybe I can get a better idea what's going on.

---

### Post by doctorbighands on 2009-02-01
I can't give you anything from a terminal session or issue any commands, because I can't boot into the system. The only way I know how to get back to a terminal now is to reinstall.

---

