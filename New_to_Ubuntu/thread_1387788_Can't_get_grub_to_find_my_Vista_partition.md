---
title: "Can't get grub to find my Vista partition"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Pascal11110 on 2010-01-22
I recently installed Ubuntu 9.04 on my desktop with an install of Vista Business 32 bit. After I rebooted, Vista did not show up in the grub boot list. So next, I ran a update-grub. Still didn't show. I then tried grub-install /dev/sda1 and that said it finished without errors, but vista still did not show up. Any help is appreciated, and any other information you need to know I'll be here for a while.

---

### Post by drs305 on 2010-01-22
First I would reinstall Grub 2 to sda rather than sda1. While sda1 installs will work, there is more chance of breakage if partitions/files are moved around on your system.

If you can't get os-prober to find your Vista partition, you could add an entry to /etc/grub.d/40_custom. Open it as root for editing and insert the following after the commented lines already existing. Change the device to the correct location (first drive=0, first partition=1).
> cat << EOF
menuentry &#8220;Vista&#8243; {
set root=[COLOR="DarkRed"](hd0,1)[/COLOR]
chainloader +1
}
EOF

Added: If you have problems *running* Vista, as opposed to finding it, here is a good link for restoring things:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

Update the Grub 2 menu with the following command:
```
sudo update-grub
```

---

### Post by Pascal11110 on 2010-01-22
Sorry, but I am very new to dual booting and grub, how do I change the partition grub is installed on? And my vista partition is all set up with my programs installed, so I'd really rather not lose it, but it's not the end of the world if I do.

---

### Post by drs305 on 2010-01-22
Edit - added : Only for Grub 2, which you probably aren't using.

You can reinstall Grub to the MBR by running the following (Ubuntu on your first drive):```

sudo grub-install /dev/sda
```

You can also make sure /etc/grub.d/30_os-prober is executable. If it isn't it wouldn't search your drive for other OS. You can right click on the file from a file browser, select Properties, and make sure it is executable. Or run this command and make sure your's has the dark red portion:
```
ls -la /etc/grub.d/30_os-prober
```
You should see the "x" meaning it's executable.
> -rw**[COLOR="DarkRed"]x[/COLOR]**r-**[COLOR="DarkRed"]x[/COLOR]**r-**[COLOR="DarkRed"]x[/COLOR]** 1 root root 5456 2009-12-30 20:58 /etc/grub.d/30_os-prober


---

### Post by oldfred on 2010-01-22
If you are running 9.04 you are running grub legacy (0.97) not grub2 (1.97 beta4) unless you upgraded to grub2 separately. Old grub was not as good at finding other installs as grub2 is. We often have to add a windows entry to menu.lst.

To confirm what Grub version:
grub-install -v

Typical entry for menu.lst but partitions have to match where your install is. Partition numbering starts with 0 in old grub. sda2 = hd0,1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader) on sda2
rootnoverify    (hd0,1)
savedefault
chainloader    +1

---

### Post by drs305 on 2010-01-22
Heh, I've worked so much with users who can't get Grub 2 to find OSs I totally missed that this was probably Grub legacy. But see, Grub legacy wasn't perfect either.  ;-) 

Thanks oldfred.

---

### Post by Pascal11110 on 2010-01-26
Sorry it took me a while to reply, but after a lot of screwing with menu.lst and such, I popped in a Hirens boot disk and use the partition tools to check out the partitions, somehow my Vista partition is being recognized as NTFS, but is also unrecognized, so something must have gone wrong with my partitioning at some point, so I am just going to recover my vista partition, and then reinstall Ubuntu. Thanks for your help anyway!

---

