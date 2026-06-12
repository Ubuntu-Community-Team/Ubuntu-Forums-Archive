---
title: "Enabling Visual Effects Issue"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by designateduser on 2009-08-13
So far my experience with Ubuntu and Linux in general had been great, but something that has bugged me for the longest time is that under system>preferences>appearance>visual effects I have been unable to enable even normal visual effects.  When I attempt to enable them I see a loading bar for drivers, the screen blinks, and then the error messsage "visual effects cannot be enabled" pops up. Any way I can fix this? Thanks in advance for taking the time to look at my question.

---

### Post by halitech on 2009-08-13
what video card and what version of ubuntu?

---

### Post by designateduser on 2009-08-13
ATI Radeon HD 3200, ubuntu 9.04:)

---

### Post by halitech on 2009-08-13
check System - Admin - Hardware drivers and see if there is a driver listed there that you can enable. the default driver doesn't allow compiz to work

---

### Post by designateduser on 2009-08-13
ok, driver successfully activated the driver and I restarted the computer and tried to enable the effects again, still no luck...:(

---

### Post by halitech on 2009-08-13
ok, are you using the 32bit version or 64bit?

you could try the ati driver 
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

---

### Post by designateduser on 2009-08-13
I feel like such a newb, but I honestly don't know! My computer is using a 64-bit processor but I am not sure I installed a 64-bit ubuntu. Ill try installing that driver.

---

### Post by halitech on 2009-08-13
open a terminal and run
```
uname -a
```

look and see if it says amd64 in the output. if it is, you need the 64bit version.

---

### Post by designateduser on 2009-08-13
I was unable to install the driver because it turns out I installed the 34-bit version of Ubuntu.

---

### Post by halitech on 2009-08-13
okay, read the installer instructions here

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat97-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat97-inst.pdf)

---

### Post by designateduser on 2009-08-13
Should I maybe download the 64-bit Ubuntu 9.04 and uninstall my 32-bit version?

---

### Post by 3rdalbum on 2009-08-13
32-bit Ubuntu with a Radeon HD 3200 should be fine, especially when you have restricted drivers enabled like you have done.

Can you please go into the terminal (Applications > Accessories > Terminal) and give us the output of these two commands:

```
glxinfo
compiz --replace
```

That second command attempts to start Compiz, which is the window manager that provides the "visual effects".

---

