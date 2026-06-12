---
title: "weird wicd problem"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-16
when rebooting out of windows 7 beta i am unable to browse the web with wicd.  all other applications that require the internet work fine.  i don't want to use network manager because it doesn't seem to connect automatically when waking from suspend has this ever happened to anyone else?

---

### Post by handydan918 on 2009-01-16
Some windows drivers leave some network cards in an "un-stopped" state. Try a full shutdown rather than a reboot, and see if that changes it. 

Unfortunately, I don't believe there is an actual "fix" for this, other than ```
rm -rf /mnt/windows
```

:P

---

### Post by mamamia88 on 2009-01-16
cool ill try and see if that works

---

### Post by handydan918 on 2009-01-16
Try the full shutdown, not the "rm" thing. That's a joke, son.

---

### Post by mamamia88 on 2009-01-16
nope can't get on the internet at all in ubuntu now and i know it's not my internet because i am in windows now and it works fine any ideas? never tried the nm thing

---

### Post by handydan918 on 2009-01-17
> **mamamia88 said:**
> when rebooting out of windows 7 beta i am unable to browse the web with wicd.  
if you are actually trying to browse the web with wicd....Well, try firefox instead.

If all other apps are connecting OK, then the problem is not wicd, it may be a firefox config error. FF3 had an issue where it will go to "offline" mode if it doesn't detect a connection with network manager. 
Hope that helps.

---

### Post by albinootje on 2009-01-17
> **handydan918 said:**
> if you are actually trying to browse the web with wicd....Well, try firefox instead.

If all other apps are connecting OK, then the problem is not wicd, it may be a firefox config error. FF3 had an issue where it will go to "offline" mode if it doesn't detect a connection with network manager. 
Hope that helps.
I've come across that Network Manager problem too some time ago.
But if you have Network Manager uninstalled (which I think happens when you install wicd), Firefox should work fine without jumping to offline mode.

To the OP, please post the output of the following :
```

sudo lshw -C network
lspci
ifconfig -a
route -n
cat /etc/resolv.conf
ping -c4 62.108.1.65

```

---

