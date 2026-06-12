---
title: "Computer Wont Boot :("
date: 2009-05-11
forum: New to Ubuntu
---

### Post by steve101101 on 2009-05-11
I have ubuntu 9.04 on my other machine and it is no longer booting. I tried to hiberante it and it immediately turned back on. after booting back up I then turned the computer off. However it will no longer boot, even using safe mode. It gets stuck on this line

[      5.963935] usb 5-1:configuration #1 chosen from 1 choice 

and never moves from this position. Is there some hibernation file that it is hanging on. 

thanks

---

### Post by b@sh_n3rd on 2009-05-11
When you say won't boot, you mean, it won't load Ubuntu?

---

### Post by steve101101 on 2009-05-11
yes

---

### Post by steve101101 on 2009-05-11
I really need to boot this computer b/c i have 2 other computers backed up on its hard drive which was shared on my local network. please help. :(

---

### Post by steve101101 on 2009-05-11
tried doing this [http://ubuntuforums.org/showthread.php?t=317038](http://ubuntuforums.org/showthread.php?t=317038) which makes you unplug the computer. now the computer says ...

trying to resume from ....
no resume image, doing normal boot

then it failed to the hibernate image
failed to mount /dev
failed to mount /sys
failed to mount /proc
target file system doesn't have /sbin/init

then busybox and it stays here forever

---

### Post by b@sh_n3rd on 2009-05-11
err...would it be possible to check if your drives are being detected? It could be possible for the PC to get confused or something coz of a bug in hibernation mode and a driver issue with Jaunty and your pc. Then again, I haven't really encountered errors as this...

**EDIT:** What if you boot your pc with the LiveCD? Is it possible to mount your drive then??
PS: When you say you've backed up, you mean you've just kept copies of files on this hdd for backup purposes and you mean to say you don't wanna loose em? Umm...If there IS a problem, you can always store that data someplace else if needed thanks to the LiveCD. I've come up with similar breaks :D. Baad ones...or let's say, "scarier" :D

---

### Post by belikralj on 2009-05-11
You can always boot of the live CD but I really don't know where to begin helping you solve this, maybe some more information would help the others kick things off. Boot the live CD and show us the contents of the system log file on your hard disk.

---

### Post by steve101101 on 2009-05-11
this just annoys me b/c the computer was completely stable, but i believe hibernation killed it. I was in the process of using the live cd to boot it. WHY DONT THEY FIX HIBERATION OR REMOVE IT FROM THE SHUTDOWN OPTIONS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by steve101101 on 2009-05-11
it wont let me mount or unmount the drive.

---

### Post by b@sh_n3rd on 2009-05-11
[FONT=Tahoma]> **steve101101 said:**
> this just annoys me b/c the computer was completely stable, but i believe hibernation killed it. I was in the process of using the live cd to boot it. WHY DONT THEY FIX HIBERATION OR REMOVE IT FROM THE SHUTDOWN OPTIONS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Well, It's not Ubuntu dude, it's your PC. I've an 11yr old PC a DELL OptiPlex GXa that hibernates perfect. Then again, I have problems with suspend and I encountered an error when hibernating on a different PC. Most unfortunately ubuntu has some problems with drivers that they can't seem to solve and I'm pretty sure you know that better than I do, seeing you've been on the forum longer than I and so used Ubuntu longer than I.

Back to the topic at hand,
Can you boot into the LiveCD on the same PC?  If not, can you access the BIOS setup program? What kind of mobo do you have? One of my two dells has a jumper to automatically boot the PC into the BIOS. I've gotta set the jumper to "configuration mode". I've an Intel D845GVSR mobo that also has this option. If you have that available, you could boot into the BIOS with everything intact and remove the hdd from the boot options and set CD-ROM only. Then you should be able to boot into the livecd and read your HDD from there...Since hibernation mode doesn't allow you to boot back into the PC normally, err...you might have to consider a reinstallation...but maybe someone else has better advice if you don't like that and I'm pretty sure you don't coz I don't either :D.
[/FONT]

---

### Post by yaknowwat on 2009-05-11
I fear hard drive failure if you're having trouble force mounting the drives from a liveCD

Attempt to check the partitions with fsck possibly too.

Only issue i see is if you were using an `unstable or non-mainstream` filesystem i use ext3/ext4 combo mainly solid but i know ext4 isnt reliable, without the patch in the 2.6.30 kernel, why its being used for the system and /home is in ext3 .

As far as hibernation goes.  You could reformat your swap partition, since thats where hibernation data is stored.

If you do reformat/change your swap edit the /etc/fstab and /boot/grub/menu.lst so that the UUID of the swap is changed to the new swap partition.

---

### Post by steve101101 on 2009-05-11
i get an error 13: invalid or unsupported executable format when i run grub with super grub disk now,

---

### Post by steve101101 on 2009-05-11
i can get into ctrl + f1 when i boot normally now but it goes to a busybox and i don't know how to use it.

if i boot into a live cd running the following commands i get:

$ sudo swapoff /dev/sda5
(this assumes that sda5 is a swap partition)
$ sudo mkswap /dev/sda5
$ sudo update-initramfs -u

i get an error on the file one b/c it says it cannot run b/c its running on read-only media.


and also when i ran a disk check from a live cd it came out with no issues.

---

### Post by steve101101 on 2009-05-11
ran this with the live cd: fsck -y /dev/sda1

and now after fixing it, it is clean i believe. im trying to boot. :)

---

### Post by steve101101 on 2009-05-11
it booted. :)

---

### Post by b@sh_n3rd on 2009-05-11
congratulations dude...:D

---

### Post by Linux_Kid66 on 2009-05-11
Lets just imagine there's nothing wrong with Ubuntu, and it's your hard drive, maybe a few bad clusters in places, or your computer could generally be broke.
Try the HDD in another computer and see what happens, if its no good, its ur HDD.
Oh you could also try a live cd boot up.

---

### Post by steve101101 on 2009-05-11
it is working now as im on the forums with my previously nonbooting computer. BUT there is def. a bug with the hibernation as it got hung up during the process and then it could not resume.

---

