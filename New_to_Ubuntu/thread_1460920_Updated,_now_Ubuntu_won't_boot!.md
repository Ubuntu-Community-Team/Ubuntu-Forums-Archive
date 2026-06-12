---
title: "Updated, now Ubuntu won't boot!"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by playing_with_matches on 2010-04-23
Hello,

I currently run 9.10, and I downloaded the recommended updates from Update Manager.  Now ever since the updates (I believe the kernel was one of them) Ubuntu won't even start up for me.  It simply goes to a screen saying that file/folder is not found.  

My Windows partition boots fine without a problem, and attempting to launch an old kernel or recovery mode brings me to the same prompt.  Help!

---

### Post by bcbc on 2010-04-23
> **playing_with_matches said:**
> Hello,

I currently run 9.10, and I downloaded the recommended updates from Update Manager.  Now ever since the updates (I believe the kernel was one of them) Ubuntu won't even start up for me.  It simply goes to a screen saying that file/folder is not found.  

My Windows partition boots fine without a problem, and attempting to launch an old kernel or recovery mode brings me to the same prompt.  Help!

Boot from live CD and chroot to your ubuntu install, and then download updates and refresh your grub menu.

From a terminal prompt (replacing sda5 with your ubuntu partition):
```
sudo mount /dev/sda5 /mnt
for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
sudo cp /etc/resolv.conf /mnt/etc
sudo chroot /mnt
apt-get update
apt-get upgrade
update-grub
exit
for i in dev/pts dev proc sys /; do sudo umount /mnt/$i;done
```

Then exit terminal and reboot. Hopefully that's sorted out your problem.

---

### Post by playing_with_matches on 2010-04-25
I tried to do what was recommended and run some commands from live cd, but when I type the first command I get 

"mount: wrong fs type, bad option, bad superblock on /dev/sdb2, missing codepage or helper program, or other error.  In some cases useful info is found in syslog - try dmesg | tail or so.


When I type dmesg|tail I get a bunch of errors.

JBD: Failed to read block at offset 2051
JBD: IO error -5 recovering block 2051 in log
JBD: recovery failed
JBD: EXT3-fs error loading journal.

did my hard drive just crash? :cry:

---

### Post by playing_with_matches on 2010-04-25
Also, i tried to run fsck on it, and I get:

/deb/sdb2: recovering journal
Error reading block 2578 (Attempt to read block from filesystem resulted in short read ignore error <y>?

---

### Post by k3lt01 on 2010-04-25
> **playing_with_matches said:**
> did my hard drive just crash? :cry:If Windows is booting up fine I doubt it (I'm assuming they are on the same physical drive. To me it is more likely that something has corrupted in the update process.

---

### Post by playing_with_matches on 2010-04-25
good point.  any advice how to get my files back?  It won't let me open the drive or mount it in anyway.

---

### Post by k3lt01 on 2010-04-25
The only thing I can think of at the moment is you force a check on the Ubuntu partition(s) by using the LiveCD.

---

### Post by bcbc on 2010-04-25
I'd try testdisk or maybe something on this link (perhaps gddrescue?): [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

It's worth a shot - although this things seem to be hit and miss.

---

### Post by playing_with_matches on 2010-04-26
Ok, so after running fsck a few more times manually (sooo tedious), I was FINALLY able to temporarily mount the drive.

I was able to grab some files (some were corrupt and wouldn't copy over) and salvage most of my files.  I have to run fsck manually a bunch of times before it will let me boot into ubuntu... and once it finally does and I shut down, i need to repeat the process all over again.

Does this definitely sound more like a hard drive issue or OS issue?  I don't want to buy a new drive and have the same issue happen.  

I should also mention that right after the update originally I was able to boot into ubuntu, but it ran PAAAAAINFULLY slow, and just froze up (acting really weird) before I shut down and had all these problems.

---

### Post by impert on 2010-04-26
> **playing_with_matches said:**
> Hello,

I currently run 9.10, and I downloaded the recommended updates from Update Manager.  Now ever since the updates (I believe the kernel was one of them) Ubuntu won't even start up for me.  It simply goes to a screen saying that file/folder is not found.  

My Windows partition boots fine without a problem, and attempting to launch an old kernel or recovery mode brings me to the same prompt.  Help!
Have you tried booting with the old kernel? Maybe it's just that upgrade-initramfs didn't run properly during the update, meaning that you don't have the right intramfs for the new kernel. That's what "file not found" suggests to me. If so, boot the old kernel and run ```
sudo update-initramfs

```

---

### Post by playing_with_matches on 2010-04-26
hey impert,

I tried to boot the old kernel and unfortunately i had the same errors.

---

### Post by k3lt01 on 2010-04-26
> **playing_with_matches said:**
> I should also mention that right after the update originally I was able to boot into ubuntu, but it ran PAAAAAINFULLY slow, and just froze up (acting really weird) before I shut down and had all these problems.That's ureadahead doing that. Last time I used it it took 2 hours and I rebooted without it even finishing.

Like I said before if Windows is starting fine then it is highly unlikely you have a hdd failure. It is obvious you have a corruption somewhere. From the information you are giving us I see 2 courses of action, keep fsck-ing until you can get in and repair the corruption (who knows how long that will take) or do a clean install when you are happy you have the files you can't afford to lose.

Btw, this is just another unfortunate example of the reasons everyone should keep a backup. The time it is taking trying to retrieve files could have been used just reinstalling.

---

### Post by durand on 2010-04-26
Uhm, are you sure it's not on a different hard drive? You seem to have ubuntu on sd**b**2, which means that you have at least 2 hard drives.

---

### Post by playing_with_matches on 2010-04-26
well, windows is on a different drive (i just noticed), but the other partition of the drive that ubuntu shares works just fine.  used to just store files.

---

### Post by durand on 2010-04-27
So did you try recovering the partition? This problem doesn't look like something caused by an update as it's more lower level than ubuntu can be. Your best bet is to clone the partition using dd, store it on an external hd or somewhere safe, then reinstall ubuntu and try to repair your dd image. Just don't do what I did and write to the corrupted partition. That will cause more problems.

---

