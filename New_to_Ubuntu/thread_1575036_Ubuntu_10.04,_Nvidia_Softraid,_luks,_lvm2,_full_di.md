---
title: "Ubuntu 10.04, Nvidia Softraid, luks, lvm2, full disk encryption"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by robrob22 on 2010-09-15
I love Ubuntu 10.04 and will be my main system from now on. That said, it always amazes me how much reading you have to do and time you have to waste to get linix running.

**Make sure you are connected to the Internet so that the Ubuntu installer can download the old grub.**

**Make sure you have Alternative CD and the Live CD ready.**

[COLOR="Red"]The issues.....[/COLOR]

1. Grub2 does not play well with lvm2, luks and soft raid.

2. On 10.04 Grub is not on the LIVE CD or the Alternative CD.

[COLOR="Green"]**The solution....**[/COLOR]

You will have to chroot to your installed partition and install dmraid and grub if not installed.

I have found that making the first partition on your nvidia raid a 200 mb /boot for linux makes your life simpler.

**Here are the steps to install the Alternative 10.04 CD with a FULL disk encryption.**

**1.** Using your Alternative 9.10 CD make the first partition on your nvidia raid a 300 mb /boot partition. Remember to choose to format.

**2.** Using your Alternative 9.10 CD install a full disk encryption as usual to a large partition. Install will finish. Rebooting now only gives a blank blinking cursor. We fix that next.

**3.** Reboot to the LIVE ubuntu 9.10 CD.

**4.** Open terminal and decrypt the partition where / is.

**sudo apt-get install lvm2 cryptsetup dmraid**

**ls /dev/mapper**  (shows us nvidia  partitions)

**sudo cryptsetup luksOpen nvidia_bcabaicg1 crypt_root_rob** (open your encrypted base partition)

**ls /dev/mapper** (shows us decrypted partitions)

**5.** Mount your / decrypted partition to /mnt and mount your /boot partition

**sudo mount /dev/mapper/robvg-rootrob /mnt**

**sudo mount /dev/mapper/nvidia_bcabaicg1 /mnt/boot**

**6.** Chroot to /mnt as usual.

**sudo mount --bind /dev /mnt/dev/**

**sudo mount -t proc proc /mnt/proc/**

**sudo mount -t sysfs sys /mnt/sys**

**sudo cp /etc/resolv.conf /mnt/etc/resolv.conf**

**sudo chroot /mnt /bin/bash**

**7.** You will find that dmraid, LVM2 and decryption debs should all be set-up. The only thing missing is GRUB. So install GRUB.

**apt-get install grub**

**8.** Cp all of /usr/lib/grub/i386-pc/* to /boot/grub (64bit versions need) /usr/lib/grub/x86_64-pc)

**cp all of /usr/lib/grub/i386-pc/* to /boot/grub **

**9.** Setup grub for your hard drive. ls /dev/mapper/ and write down the base name for your nvidia raid, mine was nvidia_bcabaicg

**grub**

**device (hd0) /dev/mapper/nvidia_bcabaicg**

**find /grub/stage1** (make sure this works and finds the file)

**root (hd0,0)**

**setup (hd0)** (You should see grub writing to /boot and writing to the mbr)

**quit**

**sudo update-grub** (If you see success your good to go)

**exit** (leave chroot)

**10.** Reboot and you should see Ubuntu asking for the
password to decrypt your hard drive.

Your welcome !
Rob

---

