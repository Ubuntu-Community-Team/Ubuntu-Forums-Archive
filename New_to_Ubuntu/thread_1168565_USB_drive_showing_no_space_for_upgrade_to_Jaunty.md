---
title: "USB drive showing no space for upgrade to Jaunty"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Mick7009 on 2009-05-24
I have a 16gb USB drive I run Ubuntu 8.10. I am an absolute newbie but so far this has been really cool. I tried to upgrade to 9.04 through the system update manager. It keeps telling me I need more space and to free up 600mb or so. I do not have much data saved on the drive and the disk usage analyzershows I have used approx 5gb and have approx 10gb free. 

I did want to leave a bit of space for Window documents but basically wanted to use the majority of the drive for Ubuntu. Why is it telling me this. 

The drive is a 16gb Sandisk Cruzer.

---

### Post by drs305 on 2009-05-24
Normally lost space is the result of a backup made to the wrong location or undeleted trash but there are many other possible reasons.

This wiki guide will walk you through the process of finding out where your free space has gone:
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

Running these two commands are a good start to troubleshooting (although running through the wiki guide will cover much more):
```

df -Th
sudo du -h --max-depth=1 /  

```

---

### Post by Mick7009 on 2009-05-24
Thanks for that, I ran the commands and they are showing the cdrom as 4.9gb. Does that mean in this case the USB thumb drive?

---

### Post by drs305 on 2009-05-24
> **Mick7009 said:**
> Thanks for that, I ran the commands and they are showing the cdrom as 4.9gb. Does that mean in this case the USB thumb drive?

No, your thumb drive should have a designation like "sdXX", for instance "sdb1", "sde1", etc. The entry you posted would be your cdrom drive.

---

### Post by Mick7009 on 2009-05-24
there is nothing in the cdrom drive. yet it shows the majority of the used space. Thanks for this by the way. I'm a little frustrated.

---

### Post by Mick7009 on 2009-05-24
Here is what my disk analyser says. I am not sure if the attachment came up or not?

[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by drs305 on 2009-05-24
If you are running ubuntu off of the usb drive, try unmounting all non-system partitions with:
```

sudo umount -a

```
Non-system partitions mounted in /media or /mnt would be included in many of the command results and tend to obscure the amount of space available on the system partition(s).

I would recommend going through the wiki step by step but if you want to take the "shotgun" approach:

Please post the results of the following after unmounting non-system partitions:
```

sudo fdisk -l  # lowercase L
mount | grep "/dev/sd"
df -Th

```

---

### Post by Mick7009 on 2009-05-24
Thanks, I'll give it a try and let you know.

---

### Post by Mick7009 on 2009-05-24
Here is what I got> Not sure what it all means but I was struggling with the Wiki too.

---

### Post by snowpine on 2009-05-24
Did you actually install Ubuntu to the USB drive, or did you use the Create a USB Startup Device utility?

---

### Post by drs305 on 2009-05-24
A few things about what you posted:

Your address shows "ubuntu@ubuntu". It looks like you are actually running the LiveCD as the results don't show an ubuntu partition. 

Did you perhaps do a wubi install *inside* Windows?

The "sudo fdisk -l" command uses the lowercase L, and not a One.

It appears you typed "mount" twice. Try "mount | grep "/dev/sd"

It's usually better to copy/paste commands to avoid errors. To copy, CTRL-C, as you are used to doing. To paste into a terminal, it's a bit different: CTRL-SHIFT-V.

Check your inbox for a PM.

---

### Post by Mick7009 on 2009-05-25
Thanks for replying. Yes I definitely have it on a USB drive. I created it with the wizard on Ubuntu. I use it on my eeepc as well so there is no CDrom to get confused with on that. All my documents store on the USB drive.

---

