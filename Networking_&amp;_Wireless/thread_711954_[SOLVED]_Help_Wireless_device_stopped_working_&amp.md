---
title: "[SOLVED] Help: Wireless device stopped working &amp;amp; buffer error"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by Prefix100 on 2008-03-01
Hey,

I have an issue that is driving me crazy.

My wireless device is the usb belkin F5D7050.
I once got my wireless device working using the rt73usb drivers, [using this guide]("http://opensource.bureau-cornavin.com/belkin/index.html")

Then when i restarted my computer the device stopped working.

I tried using the same commands as i used before to get it working, but when i type 
```
sudo ifconfig wlan0 up
```

it returns the error
```
SIOCSIFFLAGS: No buffer space available
```

The device is showed as disabled when I check my network.

Any advice on this issue would be greatly appreciated, I really need this to work because I have some work that really needs done.

EDIT: Im using 64-bit Gutsy Gibbon

---

### Post by Prefix100 on 2008-03-01
Update,

I got it working with a fresh install after discovering it worked in my live cd.

For those who may have the same problem I did, [look at this thread]("http://ubuntuforums.org/showthread.php?t=603154").

Then if you find that you can ping sites but you cant surf the web follow the Ubuntu help documentation on DNS errors, something to do with turning off the ipv4 ll thing.

<3 Ubuntu again

---

