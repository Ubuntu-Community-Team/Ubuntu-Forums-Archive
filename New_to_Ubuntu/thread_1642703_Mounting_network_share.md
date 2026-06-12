---
title: "Mounting network share"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by blues2use on 2010-12-10
I have an external USB drive on my wife's XP laptop. I can mount it with no problem **-after-** the boot process to the three ubuntu desktops is complete. I have made the necessary edits to fstab to make it available at boot so that the drive icon will show on my other 3 ubuntu desktops automatically. However, the drive doesn't automatically mount and show on those desktops. I can issue **sudo mount -a** on those 3 desktops and, sure enough, the icon appears but I'd like to have it appear automatically after the systems have booted.

I think I might have to defer the actual mounting process until the systems are all booted to the network but I'm not sure how to do that. Do I need to write a script that runs -after- the system has booted to the network so that the drive can be mounted and displayed on the other three ubuntu desktops? 


If so, any and all suggestions as to how to accomplish this task would be greatly appreciated.

btw, I used these instructions: [**https://wiki.ubuntu.com/MountWindowsSharesPermanently**]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")

Thanks ...

---

### Post by blues2use on 2010-12-12
> **blues2use said:**
> I have an external USB drive on my wife's XP laptop. I can mount it with no problem **-after-** the boot process to the three ubuntu desktops is complete. I have made the necessary edits to fstab to make it available at boot so that the drive icon will show on my other 3 ubuntu desktops automatically. However, the drive doesn't automatically mount and show on those desktops. I can issue **sudo mount -a** on those 3 desktops and, sure enough, the icon appears but I'd like to have it appear automatically after the systems have booted.

I think I might have to defer the actual mounting process until the systems are all booted to the network but I'm not sure how to do that. Do I need to write a script that runs -after- the system has booted to the network so that the drive can be mounted and displayed on the other three ubuntu desktops? 


If so, any and all suggestions as to how to accomplish this task would be greatly appreciated.

btw, I used these instructions: [**https://wiki.ubuntu.com/MountWindowsSharesPermanently**]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")

Thanks ...

Bump ... anybody?

---

### Post by JKyleOKC on 2010-12-12
> **blues2use said:**
> I think I might have to defer the actual mounting process until the systems are all booted to the network but I'm not sure how to do that. Do I need to write a script that runs -after- the system has booted to the network so that the drive can be mounted and displayed on the other three ubuntu desktops?Yes; the mounting via fstab takes place long before the network is up and running.

You might find it adequate to simply copy your mount command (less the sudo prefix) into the /etc/rc.local file, just above the existing "exit 0" line. The boot process runs this file, as root, as the last step before completing the bootstrapping. By that time, the network should be operational and the mount should succeed...

---

### Post by blues2use on 2010-12-12
> **JKyleOKC said:**
> Yes; the mounting via fstab takes place long before the network is up and running.

You might find it adequate to simply copy your mount command (less the sudo prefix) into the /etc/rc.local file, just above the existing "exit 0" line. The boot process runs this file, as root, as the last step before completing the bootstrapping. By that time, the network should be operational and the mount should succeed...

I added **mount -a** to my /etc/rc.local and that seems to have done the trick. I don't recall having this problem until I upgraded to 10.10 but, that's okay. I'm learning something new every day.

Thanks for the help... :biggrin:

---

