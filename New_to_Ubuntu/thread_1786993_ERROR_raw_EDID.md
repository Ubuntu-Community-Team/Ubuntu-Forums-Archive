---
title: "ERROR raw EDID"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by Gone fishing on 2011-06-20
On 11.04 I'm finding on my laptop tty is constantly being spammed with the following error 

```
[drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but nolinvalid EDID
[drm:drm_edid_block_valid] *ERROR* Raw EDID
```

I guess its a problem with the radeon kernel module is there any fix? As everything seems to be working just turning off the error message would do.

---

### Post by Gone fishing on 2011-06-21
Bump

Anyone got a plan?

---

### Post by happymellon on 2011-06-21
I saw this to turn off the error:

[http://answerpot.com/showthread.php?940808-Re%3A++*ERROR*+HDMI+Type+A-1%3A+probed+a+monitor+but+no|invalid+EDID](http://answerpot.com/showthread.php?940808-Re%3A++*ERROR*+HDMI+Type+A-1%3A+probed+a+monitor+but+no|invalid+EDID)

> Try adding radeon.modeset=0 in /boot/grub/grub.cfg to kernel line before "quiet"

That would be a temporary solution to see if that works.

If it does you can add it to your /etc/default/grub file

---

### Post by happymellon on 2011-06-21
Sorry if that wasn't complete - when you edit your /etc/default/grub there should be a piece saying:

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

add it in there.

---

### Post by Gone fishing on 2011-06-22
Thanks - I was trying to use nomodeset - however, it didn't work. Or to be more accurate it did work (no error messages) but also disabled visual effects, Unity etc. I tried making a custom xorg.conf but I think radeon.modeset=0 basically disables the radeon driver.

So I wondering if you can disable the use of EDID by the kernel module at boot up in grub and then build a custom xorg.conf to tell X what screen etc to use?

---

### Post by Gone fishing on 2011-07-13
Solved the constant error polling firstly stopping the problem temporally can be done with ```
sudo -i
``` followed by```
echo N> /sys/module/drm_kms_helper/parameters/poll
``` for some reason sudo echo N> /sys/module/drm_kms_helper/parameters/poll doesn't work? but gives me permission denied? This stops the problem until the next reboot. 

However ```
sudo -i
``` followed by ```
echo "options drm_kms_helper poll=N">/etc/modprobe.d/local.conf
```

Fixes the problem permanently or at least stops the irritating error messages

---

### Post by Bill Z on 2011-09-15
I am getting this same error on startup.  It will not let me login.  As soon as the login prompt appears the never-ending errors start.  How do you stop the error messages to login?

Bill Z.

---

