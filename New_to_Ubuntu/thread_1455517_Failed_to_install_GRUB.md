---
title: "Failed to install GRUB"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Loki57701 on 2010-04-16
I tried to install ubuntu 9.10 along side windows 7. About 94% into the install I get a messaging saying: 

The grub failed to install into /target/. Without the GRUB boot loader,  the installed system will not boot.

I've googled this issue and I've seen a few threads on it, but there were no answers as to why this happens. It seems that most people who experience this issue have some sort of RAID setup, however, I do not.

Is there some sort of fix for this issue?

(system specs)
ASUS Laptop
intel core 2 duo 2.53Ghz
4Gb memory
250Gb HD
nVidia 9800GT 512mb

---

### Post by zakeen on 2010-04-16
I was about to say it could be related to a Raid setup. But you said you dont have that.......

---

### Post by Ben Crisford on 2010-04-16
It *could* be a faulty CD, so I think it would be best to rule that out before we try anything else.

I would try burning the CD again at a slower speed, and try the install again.

If that doesn't work you could try installing grub through a live CD.

---

### Post by Loki57701 on 2010-04-16
I burned the iso at 8x, which is pretty slow, or at least I thought.

I selected the option at the boot screen to check the disc for errors and it found none.

I've come up with the same error with (2) separate disc's burned from the same iso. I guess I'll download another iso and re-burn, hopefully that fixes the issue.

I'm not sure how to install 'just' grub from a liveCD... lol I suppose google is my friend there.

---

### Post by Loki57701 on 2010-04-16
Ok, well.. just to be safe, I download and burned a new iso on a different computer. Unfortunately the same thing happened, the installer gets to 94% and than I get a message saying GRUB failed to install. 

Is it possible that windows 7 won't allow GRUB to overwrite its own boot loader? I've never tried a dual boot setup with windows 7, so I'm not sure.

Anyone have some ideas?

--setup--
During setup I select the option for ubuntu to be installed side by side with windows. Then I use the slide bar at the bottom to give ubuntu 30Gb of space from the local hard drive.

---

### Post by undecim on 2010-04-16
Check the MD5 of the iso.

---

### Post by Loki57701 on 2010-04-16
Using mac->Terminal
```

openssl md5 ubuntu-9.10-desktop-i386.iso

```Which came back with
```

MD5(ubuntu-9.10-desktop-i386.iso)= 8790491bfa9d00f283ed9dd2d77b3906

```And this matches the md5 I got from [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
**8790491bfa9d00f283ed9dd2d77b3906 **

(Im **no**t installing on a mac, I just used my mac to download and burn the iso for my laptop)

---

### Post by oldfred on 2010-04-16
Some BIOS have a lockout on the MBR. You can change a setting to let it write a new boot loader into the MBR.

---

### Post by Loki57701 on 2010-04-16
I checked my BIOS and under the I/O security section everything is set to (UNLOCKED).

---

### Post by Ben Crisford on 2010-04-16
> **Loki57701 said:**
> I'm not sure how to install 'just' grub from a liveCD...

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

That might help.

Also, you could try installing with the alternate CD:
[https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD](https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD)

---

### Post by Loki57701 on 2010-04-16
I had a spare hard drive sitting around so I decided to just swap out drives, seemed easier than trying to configure GRUB. 

First, I tried to install through the liveCD session but the installer just stops after 10min or so, no errors or any odd behavior, it just stops.

Then, I tried the straight install route without loading the liveCD but the same thing happens, the installer just stops with no error messages.

I tried the alternate install CD which is text only, that also failed.

I've tried burning the iso from different computers, using different discs and downloading ubuntu from a different mirror, nothing worked.
edit: The hard drive is a western digital scorpio, I used WD's diagnostic tool to check the drive for problems and it found none.

So, either I have some crazy hardware issue or... lol I dunno. I've been able to install ubuntu before (even 9.10) on that laptop with no problems. Currently the laptop in question has windows 7 installed on it with no problems, everything works fine.

I guess ubuntu just wasn't meant to be installed on that particular laptop (again).

I'm glad my server running ubuntu didn't have this many problems.. lol

---

### Post by oldfred on 2010-04-16
You were quick to mention that you do not have raid, but were the drives you are using ever in a raid config. We have found raid settings hidden on drives that interfere with an install.

---

### Post by Loki57701 on 2010-04-16
No, neither drive was ever in a raid setup. I've also used DBAN to wipe the drives in the past, so if there were some weird manufacturer RAID settings on there they would have been erased.

---

### Post by Loki57701 on 2010-04-18
I'm going to post this in case anyone else out there has the same problem.

If, for some reason, ubuntu just won't install on your system try installing ubuntu from a USB flash drive. Even if you've never had any problems with your cd/dvd drive, try the flash drive option, it worked for me and it could work for you.

I followed this guide: [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

- The guide only works IF your computer can boot from a USB flash drive. (as far as I know)
- If you get a 'boot error' make sure you read the instructions for activating the partition on the flash drive.

---

