---
title: "grub rescue"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by GVT76 on 2010-07-11
Help me please, I am very new to linux and not good with the cli, I had been running 10.04 NBR via a USB, I decided today to install it as dual boot with Windows XP, went through the wizards, allowed it to do the partition etc, so it all seemed to install fine. I took out the USB and went to restart, it shut down and then restarted with:

error: no such device: e39b3877 -blah-blah
grub rescue

Now the thing is I cannot reboot into the BIOS or anything, I shut it down and start it up and it just goes back into the same prompt, I have tried some threads reagarding this but come unstuck as it does not seem to recognise the filesystems which are listed by ls

Anybody have any ideas??

Thank you all :)

---

### Post by cariboo on 2010-07-12
Unfortunately there isn't a graphical tool to repair your problem. It looks like grub didn't get installed to the mbr.

Boot from your usb device, and once at the desktop open an Applcations->Accessories->Terminal and type:

```
sudo mount /dev/sda2
```

substitude your root partition for the one in the example above. Next in the same terminal type:

[list]
[*] sudo mount -o bind /dev /mnt/dev
[*] sudo mount -o bind /proc /mnt/proc
[*] sudo mount -o bind /sys /mnt/sys
[/list]

Next type:

```
sudo chroot /mnt
```

You should now be at a root prompt, type:

```
grub-install /dev/sda
```

then type:

```
update-grub
```

exit from chroot by pressing Ctrl-d. You should now restart, remove your usb device and boot to your desktop.

---

### Post by GVT76 on 2010-07-12
Hi cariboo907,
 
thanks for the advice, I have ended up taking the chickens way out, I had a live copy of 10.04 on a USB, so I booted off this then installed to the HD erasing all previously installed data on the HD,
 
I then from here updated the OS checked it worked and then booted to the XP recovery disk which has inturn overwritten the HD again and reformatted, so I am kind of back where I started with XP working as normal and then booting from my USB when I want to use Ubuntu.
 
It just seemed a little easier at the time with me, when I hae a bit of time I am definitely going to try and make it dual boot again.
 
Thanks again :)

---

