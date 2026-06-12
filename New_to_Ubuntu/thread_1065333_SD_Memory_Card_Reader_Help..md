---
title: "SD Memory Card Reader Help."
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Flufflebuns on 2009-02-09
I have an Acer Aspire One with built in SD Memory Card reader. The reader worked great with windows, but now seems not to function at all and won't read any card I put in. 

I have read threads with similar problems, and have even heard that this is simply a lack of driver available for Ubuntu to be remedied in the future. Is this true or is there anything I can do to fix it now?

Thanks.

---

### Post by unplugged23 on 2009-02-09
Is it mounted?

---

### Post by Flufflebuns on 2009-02-09
What exactly do you mean by mounted? And how do I figure out if it is? (Sorry I am new to this). All I can tell you is when I put any memory card in it acts as if nothing new has happened. It is an internal drive, not an external USB memory card reader. I also forgot to mention that I am using Ubuntu 8.10 if that helps.

Thanks for the quick response by the way!

---

### Post by unplugged23 on 2009-02-09
Well first off go to Places > Computer and see if you can see the device there. if you can right click and see if theres a mount option.

---

### Post by Captain_tux on 2009-02-09
I had similar problems with my HP, but found a work around...

[http://ubuntuforums.org/showthread.php?t=988716](http://ubuntuforums.org/showthread.php?t=988716)

---

### Post by webmiester on 2009-02-09
What version of ubuntu are you using?

I had the same problems with my USB car reader until I upgraded to ubuntu 8.10, which simply worked well after :)

---

### Post by kansasnoob on 2009-02-09
Try installing pmount from synaptic or:

```
sudo apt-get install pmount
```

Brief description from synaptic:

> mount removable devices as normal user
pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.

You will have to restart for the change to take effect!

---

### Post by Flufflebuns on 2009-02-09
Unplugged: The Places pull-down shows nothing new when I insert a device (have tried multiple), as well as nothing pops up on the desktop. It doesn't seem to read the SD card at all.

Webmeister: I am using 8.10 which is what I started using this computer with. It is all completely updated.

Captain Tux: Thanks for the work-around, I am sure it would work, but I would like it better if I could get my internal one to function!

Thanks everyone for the speedy responses.

---

### Post by Flufflebuns on 2009-02-09
Worked like a charm Kansasnoob, I cannot thank you enough!

---

### Post by Flufflebuns on 2009-02-12
So, just for kicks I installed Xubuntu 8.10 on this same computer (Acer Aspire One). I assumed the same fix would work for Xubuntu as did so well for Ubuntu, unfortunately no such luck. I guess I could go back to Ubuntu, but X is much faster for me.

---

### Post by louis0591 on 2009-02-14
kansasnoob: i jus installed pmount and usbmount through synaptic. now my usb drives show up but when i insert my micro sd card into my usb memory card reader nothing shows up in the usb folders.

---

