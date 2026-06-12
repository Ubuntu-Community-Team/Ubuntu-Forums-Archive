---
title: "Now it works, now it doesn't..."
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by diamond on 2006-07-25
I'm running Dapper on a Dell Inspiron 600m, and I'm using the built-in wireless. I used the ndiswrapper graphical front-end while still connected via the ethernet port. After install, I deactivated eth0 (the ethernet port), activated eth1 (the Wireless connection), disconnected the cable, and I had wireless.

Then I rebooted, and everything went to hell. It booted with eth0 disabled, and wouldn't allow me to enable it (even though eth0 was disabled). I switched eth0 from the its static IP config to DHCP, and it let me enable it, but the wireless utitity showed 0 signal.

What's going on here? The ndiswrapper graphical utility shows that the hardware is present, so presumably that means it recognizes my wireless card. Are there any config files I can check to see if anything is configured wrong? Any log files I can check to see what the exact error is?

---

### Post by diamond on 2006-07-26
Quick followup:

I realized that, after hooking to the ethernet, I ran the standard update utility and (among other things) it upgraded my kernel from 2.6.15-23 to 2.6.15-26. Remembering from previous experience that you have to recompile ndiswrapper against the new kernel if you upgrade, I went into /usr/src where the ndiswrapper source tarball was downloaded ( ver 1.8 ). I untarred it, did a make and make install (watching to make sure it compiled against the 2.6.15-26 kernel headers) and tried again. I started from scratch, reinstalling the driver for my wifi (the file I used is bcmwl5.inf, the same one I used under Breezy, when it worked just fine). No luck.

My syslog records the following error messages when I try to activate eth1:

```
Jul 25 22:12:41 localhost firmware_helper[5385]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:03.0' with driver 'bcm43xx'
Jul 25 22:12:42 localhost kernel: [17179698.264000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jul 25 22:12:54 localhost firmware_helper[5402]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:03.0' with driver 'bcm43xx'
Jul 25 22:12:54 localhost kernel: [17179711.008000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jul 25 22:12:54 localhost firmware_helper[5405]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:03.0' with driver 'bcm43xx'
Jul 25 22:12:54 localhost kernel: [17179711.024000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```

I looked in the /lib/firmware directory, and those files were not there. Did I miss a step?

---

### Post by Fully216 on 2006-08-03
If you went thought the necessary install steps (some examples found below),

[http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working](http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working)
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

then I am not sure why it isn't working.  You might try updating the the lastest stable version of ndiswrapper 1.21 found here.

[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

You should also let us know what the result of running ndiswrapper -l 

For example, when I run it I get the following results:
Installed ndis drivers:
netbc564 driver present, hardware present

Let us know and I hope this helps!

---

