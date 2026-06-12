---
title: "Trouble booting after Ubuntu 11.04 upgrade."
date: 2011-07-29
forum: New to Ubuntu
---

### Post by sccrstud92 on 2011-07-29
I was running Ubuntu (not sure what version but it was pretty recent) and it suggested that I upgrade to 11.04. I download and install, but after it finished, I could not reboot. It shows me the GRUB 2 Boot menu, but none of the options result in a successful boot. They all wait indefinitely after reporting a "cannont find device 'sda1' error. After further investigation with the GRUB console, the 'ls (hd0,msdos1)/dev/' command doesn't show any files starting with 'sd' (or 'hd' for that matter.) Does anyone know what is going on and how to fix it?

---

### Post by sccrstud92 on 2011-07-30
bump

---

### Post by whitethorn on 2011-07-30
Looks like maybe your grub got messed up a bit.  Do you have a live cd? This is what I would do

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Follow this guide to get it remove and reinstall grub2.

---

### Post by sccrstud92 on 2011-07-30
No, I don't have a LiveCD or LiveUSB because I got the computer with Ubuntu preinstalled. However, I did download the 11.04 image and I will create a LiveUSB so I can try out your advice.

---

### Post by sccrstud92 on 2011-07-30
I created the LiveUSB but I don't know what to do now. I can't boot from my hard drive or my LiveUSB (if I'm doing something wrong I don't know what it is), and I don't know how to reinstall GRUB (or anything for that matter) without booting an OS. What should I do?

---

### Post by sccrstud92 on 2011-07-30
bump

---

### Post by Rex Bouwense on 2011-07-30
Calm down.  The world is not ending yet.  First a couple of questions.  When you downloaded the 11.04 ISO did you run an MD5SUM on the download?  What procedure did you use to create the bootable flash drive?  After you created the flash drive, inserted into your computer, turned on your computer, and tried to boot from the flash drive, did you change the boot order in your computer's BIOS (making the flash drive boot before the hard drive)?  In some cases a computer will not recognize the flash drive as a flash drive but another hard drive so you will have to move it ahead of the hard drive of your computer to successfully boot.

---

### Post by sccrstud92 on 2011-07-30
I didn't MD5SUM the download. It was one of those automatic things that came up offering to upgrade. I created the USB with the 11.04 image and UNetbootin. In the BIOS setup the USB did show up under the harddrive list, and I believe I selected it, but I might have not saved the change before continuing the boot (or the like), so I'll try that again.

And sorry, I don't mean to appear frantic. I'm just trying to fix this because all my sister's summer homework is on it.

---

### Post by Rex Bouwense on 2011-07-30
Hey, having all the Summer homework on a computer and not being able to boot is probably cause for at least a little panic.:popcorn:

---

### Post by sccrstud92 on 2011-07-30
Okay, I am able to boot from the USB, however, I'm not sure what to do next.

---

### Post by Rex Bouwense on 2011-07-30
If you can boot from the flash drive, select try Ubuntu without making changes to your system.  Does everything work?  While you are in there, back up your sister's stuff so she won't disown you.

---

### Post by blesbok on 2011-07-30
Do this after live media boot:[http://ubuntuforums.org/images/editor/html.gif](http://ubuntuforums.org/images/editor/html.gif)


```
cd /
sudo mkdir disk
sudo mount /dev/sda9 /disk	# replace sda9 with installation's partition
sudo grub-install --root-directory=/disk/ /dev/sda
sudo shutdown -r now  # remember to remove physical media
```

---

### Post by sccrstud92 on 2011-07-30
To do the backup, is there a way to save the archive of her documents onto the USB and have it persist? I'm assuming that's where I should backup to because backing up to the actual hard drive seems pointless.

---

### Post by Rex Bouwense on 2011-07-30
Depending upon how much stuff she has to back up, just insert another flash drive into your computer and copy the files to it.  You do not want to back copy it to your live flash drive since that is the only way you have to boot now.  If you read post #3 to your thread, you will see that Whitehorn has given you a possible solution.  Back up your sister's stuff first because you do not want to lose that.

---

### Post by sccrstud92 on 2011-07-30
blesbok, by installation's partition, do you mean the USB installation partition or the hard drive installation partition?

---

### Post by sccrstud92 on 2011-07-31
bump

---

### Post by linuxman94 on 2011-07-31
You are only allowed to bump once every 24 hours.  If you bump to frequently your thread will be closed.

As for your problem, please run this script (attached) from the live cd and post the output in code tags (# sign in editor).

[Boot info script]("http://dl.dropbox.com/u/7800678/boot_info_script.sh")

---

### Post by whitethorn on 2011-07-31
Just follow the guide I linked to in my first post. The only problem I can really see if figuring out which partition is your installation partition. I usually start with

```
sudo fdisk -l
```

This gives you a list of all the partitions and what filesystem are on them, your probably going to be looking for one with linux. I then start mounting the partitions to some folder and checking what's inside

```

sudo mkdir /media/disk    # create a folder where we will attach (mount) partitions to
sudo mount /dev/sda1 /media/disk  # mount the first partition on disk sda to the just created folder
ls /media/disk  # lets have a look what's in there

sudo umount /media/disk   # not what was needed let's unmount it and try the next one

```

What you're looking for is
```

 ls /media/usb
bin    dev   initrd.img  lost+found  opt   sbin     sys  var
boot   etc   lib         media       proc  selinux  tmp  vmlinuz
cdrom  home  lib64       mnt         root  srv      usr

```
That would be /dev/sda5 on my computer. Just for the sake of making sure everything will work in the guide I wrote we'll check to make sure you don't have a seperate /boot partition. So leaving the partition we just found mount let's go to

```

cd /media/disk/etc
cat fstab

```

Now it should look pretty odd. Now the important part is directly after the UUID=...   look for a /boot if you have than then you need to run the extra commands in the guide.  
> 
UUID=... / 
UUID=... /home


---

### Post by sccrstud92 on 2011-07-31
I fixed the problem by reinstalling 10.04 from a USB, erasing 11.04. Thanks for your assistance, and I apologize for the frequent bumping, it won't happen again.

---

### Post by Rex Bouwense on 2011-07-31
Glad to hear you got it fixed.  I trust that you sister's homework is still safe.  Enjoy Ubuntu.:popcorn:

---

