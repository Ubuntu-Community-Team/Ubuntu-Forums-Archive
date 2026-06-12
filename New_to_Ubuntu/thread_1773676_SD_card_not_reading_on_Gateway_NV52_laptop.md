---
title: "SD card not reading on Gateway NV52 laptop"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by perlgoodies on 2011-06-02
I just put Ubunto on my Gateway NV52 laptop and everything so far is working good EXCEPT the media card reader. I have an MicroSD card inside the SD card connector thing inside the computer and it doesn't do anything. No popups, no errors, no nothing.
 
It's not a USB media card connector, the laptop has an onboard SD card reader I'm using with the little Micro-to-SD card adapter that comes with micro cards. Anyway I put it in and nothing happens.
 
I'm new to linux and Ubuntu so I don't know where to go to find the MY COMPUTER equiv. of Windows to see all the drives attached to the computer. And if it doesn't show up there, what do I have to do?

---

### Post by frankbooth on 2011-06-02
> **perlgoodies said:**
> I'm new to linux and Ubuntu so I don't know where to go to find the MY COMPUTER equiv. of Windows to see all the drives attached to the computer. And if it doesn't show up there, what do I have to do?

The "My Computer" equiv. would be Nautilus, the default file browser in Ubuntu.

You can launch it by either opening your Home Folder or press ALT+F2 and type *nautilus*.

It looks something like this and the drives, as you can see, are on the left side.
[img]http://farm4.static.flickr.com/3116/2846377880_4dbfd1655d.jpg[/img]

The eject arrow indicates that the drive is *mounted*, if there is no eject arrow the drive is *unmounted*. The drive will try to mount if you try to access it.

If it doesn't show up in Nautilus I'm afraid I can't help you get it running. I don't have any experience with problematic card readers. The one I have on my netbook worked out of the box.

---

### Post by Jerinaw on 2013-04-03
> **frankbooth said:**
> The "My Computer" equiv. would be Nautilus, the default file browser in Ubuntu.

You can launch it by either opening your Home Folder or press ALT+F2 and type *nautilus*.

It looks something like this and the drives, as you can see, are on the left side.
[img]http://farm4.static.flickr.com/3116/2846377880_4dbfd1655d.jpg[/img]

The eject arrow indicates that the drive is *mounted*, if there is no eject arrow the drive is *unmounted*. The drive will try to mount if you try to access it.

If it doesn't show up in Nautilus I'm afraid I can't help you get it running. I don't have any experience with problematic card readers. The one I have on my netbook worked out of the box.

This worked for me [http://goinggnu.wordpress.com/2009/11/12/read-your-sd-card-with-your-ubuntu-laptop/]("http://goinggnu.wordpress.com/2009/11/12/read-your-sd-card-with-your-ubuntu-laptop/")

1. Backup the file /etc/modules
sudo cp /etc/modules /etc/modules.bak
2. Add one line to /etc/modules
gksu gedit /etc/modules
or
sudo vi /etc/modules
3.Tag this on to the end of the file in a new line:
tifm_sd

When you restart, you’re card reader will be functional. You’ll see that when you slap an SD card into the reader, it will automount.

But wait, don’t want to have to restart your machine? Go back to the terminal you impatient person and type:

sudo modprobe tifm_sd

---

### Post by wildmanne39 on 2013-04-03
Thanks for sharing, old thread closed!
Thanks

---

