---
title: "Intel 3945 wireless is buggy after updating Lucid."
date: 2011-03-01
forum: New to Ubuntu
---

### Post by edwardoclese on 2011-03-01
Hello Everybody!

I just installed Lucid 10.04.1 from ISO image CD to my Panasonic CF-51 Toughbook. The machine is an Intel Centrino Core Duo at 2.0ghz and uses the Intel 3945 a/b/g integrated wireless. The install was easy and fast, and everything on my laptop worked flawlessly, including Fn keys. I was stoked!

I used Update Manager, and the program finds some 240+ updates, so I installed them. Now when I stream video, my wireless shuts off after a few minutes, and I have to restart my laptop to get it back.

I suppose I could simply wipe everything and reload the CD image, (done that 3 times and it works great, but then I update and get the problem back.) I suppose I could not update, but among the updates are programs I do want, including Eclipse and OpenJDK-6, and I am so new to linux, I haven't a clue how to fix this properly.

Thanks!

---

### Post by edwardoclese on 2011-03-01
Just found this bug report that describes my problem in great detail, on similar equipment.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564376](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564376)
My machine is: Panasonic CF-51QG5EEBM, Core Duo 2ghz, 64gb SSD, Intel Centrino 3945 a/b/g.
My wireless bug manifests when playing video on fullscreen.
I am not sure what to take away from this... Any suggestions? (Speak slowly, I'm new to linux ;)

---

### Post by Perfect Storm on 2011-03-01
If it's the kernel update, you can boot up in the previous working kernel.

---

### Post by edwardoclese on 2011-03-01
Okay! So I just went and learned what the heck GRUB2 is, and used the options to boot to the older kernel, and that seems to work fine. 

Now how can I fix it permanently? I'd like to remove the old kernel, but when I look in Synaptic, I am confused by all the info: Plenty of stuff like linux-headers-2.6.32-24 (pieces of the older kernel) and linux-headers-2.6.32-28 (the newer one that doesn't function properly.)

What confuses me most is that I don't see parity between the files: I would expect that for every old file there would be a new one. Any advice for a newbie?

---

### Post by Perfect Storm on 2011-03-01
Try with startupmanager. It should be in the Ubuntu Software Center.

---

### Post by edwardoclese on 2011-03-01
Thank you for the Startup Manager. I used it, but now have discovered that booting to the old kernel does not fix the problem. 

Various bug reports describe radeon KMS conflicts with Intel Wifi and audio, and say I shoud "Boot with radeon.modeset=0" Can you explain how to do this?

Also, what is KMS and what do the radeon modes actually do? I am reading that all these problems occur because Lucid default is radeon.modeset=0, and that this changes because "  xorg-edgers kernels default to 1."  I note that there was an xorg package in that first big update. Is there anything here I should be concerned about?

---

### Post by Perfect Storm on 2011-03-01
You have to edit the bootloader manually to add the string.

```
gksu gedit /boot/grub/grub.cfg
```

[ctrl]+{o] = save
[ctrl] +[x] = exit

This is an example:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 74f8b009-9531-4320-a3e1-292a58ea2511
        linux   /vmlinuz-2.6.35-27-generic root=UUID=03501270-0b40-4e73-96f2-522d6b0099c8 ro   quiet splash
        initrd  /initrd.img-2.6.35-27-generic
}


```

to

```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 74f8b009-9531-4320-a3e1-292a58ea2511
        linux   /vmlinuz-2.6.35-27-generic root=UUID=03501270-0b40-4e73-96f2-522d6b0099c8 **radeon.modeset=0** ro quiet splash 
        initrd  /initrd.img-2.6.35-27-generic
}


```

---

### Post by edwardoclese on 2011-03-02
Artificial Intelligence,
Inserting that change into the grubfile seems to have solved this issue. I modified only the latest kernel boot file, and it seems to be working fine: I've tested on two networks, and streamed Hulu, YouTube, and other flash content at fullscreen no problem. I'll mark this Solved!

Thank you for your help!

---

### Post by Perfect Storm on 2011-03-02
My pleasure ^_^

---

