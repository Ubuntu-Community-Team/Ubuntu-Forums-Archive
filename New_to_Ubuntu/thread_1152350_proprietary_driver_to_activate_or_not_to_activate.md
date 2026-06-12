---
title: "proprietary driver to activate or not to activate"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by crew51m on 2009-05-07
I have a proprietary driver for my mobile ati 3650, is this the same as a restricted driver? Last time I loaded a restricted driver, my laptop crashed. If I activate it and I crash, how do I get back to my desktop? It loaded in Mandriva gnome 2.26
This is basically what it says:

Tested by Ubuntu developers
License proprietary

3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.

Will it be safe to load this?

---

### Post by jacksinn on 2009-05-07
Backup your existing xorg.conf file. If you must have the restricted driver, give it a whirl. If it crashes the GUI, you can go in command line and restore your backed-up xorg.conf file.
So you could do something like:

cp /etc/X11/xorg.conf ~/xorg.conf.bak

Then try your new driver. If it fails:

cp ~/xorg.conf.bak /etc/X11/xorg.conf

and your old setting will be restored (provided the driver changed no other stuff).

---

### Post by Didius Falco on 2009-05-07
> **crew51m said:**
> I have a proprietary driver for my mobile ati 3650, is this the same as a restricted driver? Last time I loaded a restricted driver, my laptop crashed. If I activate it and I crash, how do I get back to my desktop? It loaded in Mandriva gnome 2.26
This is basically what it says:

Tested by Ubuntu developers
License proprietary

3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.

Will it be safe to load this?

I'd suggest you go to [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) and check for what driver it offers you from there. If it offers the 9.4 driver, then you should be able to use the Restricted (which is also proprietary - same thing) driver.

Just in case you have problems (some people are still reporting problems with that card, but it works fine for others), boot into Recovery mode, choose command line with networking and type ```
sudo /usr/bin/aticonfig -initial
``` and then ```
sudo reboot
```

Boot normally. If you still have problems, boot back into  Recovery with Networking, as above and type  ```
sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install xserver-xorg-video-ati
sudo reboot

```

Those are three separate commands, BTW. That will put the 2d Xorg driver back into place, and you should be right where you are now. 

I hope this helps...

Regards,

Didius

---

### Post by crew51m on 2009-05-07
Thanks, I will copy the backup and when I get the courage I will try the driver.

---

### Post by Didius Falco on 2009-05-07
> **crew51m said:**
> Thanks, I will copy the backup and when I get the courage I will try the driver.

Post and let us know how it goes - it might help others with that video card.

Good Luck!!

Regards,

Didius

---

