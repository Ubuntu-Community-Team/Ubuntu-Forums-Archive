---
title: "Wireless not working on HP Stream Ubuntu 16.04 for wireless device [14e4:4365]"
date: 2017-08-04
forum: Networking &amp; Wireless
---

### Post by pg38528 on 2017-08-04
bcmwl-kernel-source is up to date.

PasteBin Link: [http://paste.ubuntu.com/25243089/](http://paste.ubuntu.com/25243089/)
Not super technical... but the point of installing Ubuntu/Linux for the first time is to learn!

Thanks,
Patrick

---

### Post by chili555 on 2017-08-04
However, the driver isn't loaded. Let's load it and see what happens:```
sudo modprobe wl
```Does it reply this?> modprobe: ERROR: could not insert 'wl': Required key not availableIf so, check here: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

### Post by pg38528 on 2017-08-04
Since I posted this, I uninstalled bcmwl-kernel-source based on another post I found. Should I reinstall ? 

I'm out and won't be able to try until later tonight. I'll post back once I attempted your suggestion. 

Thanks!

---

### Post by chili555 on 2017-08-04
>  I uninstalled bcmwl-kernel-source based on another post I found. Should I reinstall ? Yes, please. 

The other post you read is incorrect.  [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by pg38528 on 2017-08-04
AWESOME! That worked. Thank you so much Chili555. I'm no longer stuck in the bathroom! (where the router is)

Have a great weekend!

---

### Post by chili555 on 2017-08-05
Glad it's working as expected. Please use thread tools at the top to mark Solved.

---

