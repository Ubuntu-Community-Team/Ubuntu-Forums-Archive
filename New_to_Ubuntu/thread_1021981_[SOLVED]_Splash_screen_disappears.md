---
title: "[SOLVED] Splash screen disappears"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by tomtom1982 on 2008-12-26
Hi all,

here's my problem:

If I start ubuntu, the ubuntu-logo and the progress bar appears. But after a few seconds it disapperas and there are the detailed boot informations.

I didn't change any boot paramenter (and the boot parameter IS quiet splash).

How can get back my progress bar?

---

### Post by northern lights on 2008-12-26
Can you run```
sudo update-grub
```and see what it says about the splash?

---

### Post by alienexplorers on 2008-12-26
Did you alter anything in the partition table.  A change in the swap file can cause this to happen.

---

### Post by drs305 on 2008-12-26
To avoid having to edit grub's menu.lst, install StartUp-Manager to tweak the settings:
```

sudo apt-get install startupmanager

```

To run: System, Administration, StartUp-Manager

In the Boot Options section, tick Show Boot Splash and untick Show Text during Boot. In the "Appearance" section you can set or change the splash theme or set a background image.

To learn about all the tweaks available via SUM or if you want to edit grub manually, here is a tutorial:
[StartUp-Manager and Editing menu.lst]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by tomtom1982 on 2008-12-26
@northern lights:
```
sudo update-grub
```

says:
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-virtual
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

@alienexplorers:
No, I didn't change any partitions.

@drs305:
startupmanager was already installed. "Show boot splash" was chosen.

So what to do?

---

### Post by alienexplorers on 2008-12-26
Are you getting any strange errors appearing when the boot splash disapears and the boot text starts?

---

### Post by northern lights on 2008-12-26
> **tomtom1982 said:**
> @northern lights:
```
sudo update-grub
```

says:
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
[COLOR="Red"]Searching for splash image ... none found, skipping ...[/COLOR]
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-virtual
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```
I figured this would happen.

The error might not be as straightforward as it says, but it very well could.

You might have somehow lost/deleted the original usplash image. I doubt it though, as I don't see how that could have happened.

Or you could possibly not have an image that works for your resolution.
Try adding a vga-framebuffer code to "defoptions" or to the kernel line in menu.lst, such as```
# defoptions=quiet splash vga=785
```or```
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=60affb29-ad45-4efe-ae44-227013df558c ro quiet splash vga=785
```

Framebuffer codes translated to resolution:
vga=785 - 640x480
vga=788 - 800x600
vga=791 - 1024x768
vga=794 - 1280x1024

---

### Post by caljohnsmith on 2008-12-26
Northern lights, I think you might be forgetting that the splash image that update-grub searches for is the Grub menu splash image, not the Ubuntu splash screen. If tomtom1982 does not get the Ubuntu splash screen, that would be a different problem. Tomtom1982, sometimes not getting a Ubuntu splash screen can happen when the UUID of your swap partition changes for whatever reason, so I think it would be worth at least checking if that is the problem:
```
sudo blkid
cat /etc/initramfs-tools/conf.d/resume
cat /etc/fstab
```
Please post the output of the above commands.

---

### Post by tomtom1982 on 2008-12-26
@alienexplorers:
No, there aren't any error messages. 

@northern lights:
I tried to change resolution, but result is the same thing.

I didn't delete anything. Yesterday evening I've had a progress bar, as I put on the PC today it wasn't there.

---

### Post by northern lights on 2008-12-26
> **caljohnsmith said:**
> Northern lights, I think you might be forgetting that the splash image that update-grub searches for is the Grub menu splash image, not the Ubuntu splash screen.
Duh.

> **caljohnsmith said:**
> Sometimes not getting a Ubuntu splash screen can happen when the UUID of your swap partition changes for whatever reason.
I believe every word of the above, however don't see the connection.
I can see the SWAP's UUID changing, but how does that affect usplash? Is the image stored in the swapspace?
Please be so kind as to elaborate.

---

### Post by tomtom1982 on 2008-12-26
@northern lights:
I tried it out with usplash-theme-xubuntu and usplash-theme ubuntustudio, but same problem.

@caljohnsmith:
sudo blkid says:

```
/dev/sda1: UUID="0E686FA3686F8873" LABEL="Windows XP" TYPE="ntfs"
/dev/sda7: UUID="e8da48b9-ce92-4ed6-b4a7-a1dbd49fae23" TYPE="ext2"
/dev/sda5: TYPE="swap" UUID="5f3f39ac-8e7f-4782-b876-4773f4b7fc83"
/dev/sda6: UUID="3c66c3da-ab1f-49d7-b901-079021841b69" TYPE="ext2"

```

```
thomas@ubuntu-hardy:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=b7aa5f77-a6a5-4210-8ba3-b857928ed9f7
```

```
thomas@ubuntu-hardy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=3c66c3da-ab1f-49d7-b901-079021841b69 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=e8da48b9-ce92-4ed6-b4a7-a1dbd49fae23 /home           ext2    relatime        0       0
# /dev/sda5
UUID=b7aa5f77-a6a5-4210-8ba3-b857928ed9f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by caljohnsmith on 2008-12-26
OK, it looks like that is your problem; your swap partition's UUID changed. How about doing the following, and please post the output of all the commands:
```
sudo swapoff -a
sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/sda5
sudo blkid -c /dev/null
```
Reboot, and let me know what happens.

---

### Post by tomtom1982 on 2008-12-26
> caljohnsmith
  Re: Splash screen disappears
 OK, it looks like that is your problem; your swap partition's UUID changed. How about doing the following, and please post the output of all the commands:
 
Code:
sudo swapoff -a
sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/sda5
sudo blkid -c /dev/null
Reboot, and let me know what happens.


Yes, it works!

Thanks for this.

The output was:
```
thomas@ubuntu-hardy:~$ sudo swapoff -a
swapoff: kann /dev/disk/by-uuid/b7aa5f77-a6a5-4210-8ba3-b857928ed9f7 nicht kanonisieren: No such file or directory
thomas@ubuntu-hardy:~$ sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/sda5
Swapbereich Version 1 wird angelegt, Größe 3602632 KBytes
kein Label, UUID=b7aa5f77-a6a5-4210-8ba3-b857928ed9f7
thomas@ubuntu-hardy:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="0E686FA3686F8873" LABEL="Windows XP" TYPE="ntfs"
/dev/sda5: TYPE="swap" UUID="b7aa5f77-a6a5-4210-8ba3-b857928ed9f7"
/dev/sda6: UUID="3c66c3da-ab1f-49d7-b901-079021841b69" TYPE="ext2"
/dev/sda7: UUID="e8da48b9-ce92-4ed6-b4a7-a1dbd49fae23" TYPE="ext2"
```

---

### Post by caljohnsmith on 2008-12-26
Glad that fixed the problem; cheers and have fun with Ubuntu. :)

---

### Post by tomtom1982 on 2008-12-26
Thanks to all,

so I learned more about startup and swap. 

Yesterday I plugged on a bootable stick with PCLinuxOS. It has its own swap-partition, so I think this would be the failure.

---

### Post by northern lights on 2008-12-26
Yo, John, Callie wizard, if you do know, please sum up how the SWAP's UUID affects usplash.

I can't explain it to myself.

---

### Post by caljohnsmith on 2008-12-28
> **northern lights said:**
> Yo, John, Callie wizard, if you do know, please sum up how the SWAP's UUID affects usplash.

I can't explain it to myself.

Hi Northern Lights, really sorry it took me so long to get back to you--I accidentally missed your post since I stopped following the thread after it was marked solved. But to answer your question, the swap UUID gets hard-coded into the /boot/initrd images that are booted on start up, so if the swap UUID changes, then the initrd images won't be able to use the swap partition; losing the splash image seems to be at least one of the symptoms of that problem. Also, the swap partition won't be mounted on start up if the swap UUID changes (assuming you haven't updated /etc/fstab with the new UUID), but I don't think that's what causes the splash screen to disappear; I think it is the initrd images using the wrong UUID that causes it, but I could be wrong. So the bottom line is if the swap UUID changes, there are at least two methods of fixing it that I know of:
[LIST]
[*]Change the /etc/fstab and /etc/initramfs-tools/conf.d/resume files to use the new UUID, and also regenerate all your initrd images to use the new swap UUID
[*]Or the easier way I think is to simply change the swap partition UUID back to what it was before, which is what the commands in post #12 do.
[/LIST] 
Anyway, not sure if that really clarifies it or not, but that's how I think the swap UUID relates to the Ubuntu splash screen. :)

---

