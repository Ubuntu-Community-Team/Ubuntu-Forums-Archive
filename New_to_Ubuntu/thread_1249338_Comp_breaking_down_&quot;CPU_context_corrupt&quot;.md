---
title: "Comp breaking down &quot;CPU context corrupt&quot;"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by XSindy on 2009-08-25
Ubuntu froze some 2 days ago, I was listening to music and it just stopped. Restarted it and it froze again.When I pulled out all the USB stuff it started normally and I used it for an hour or so and shut it down. The next day it kept freezing, tried the liveCD, it to froze. I have an laptop with Win on that still works. Found that the new ubuntu 9.04 has some problems and that it can freeze. So I downloaded Fedora and Mint to try out, hoping that all this has to do with ubuntu. But
Fedora:
  CPU 0: Machine Check Exception: 0000000000000004
  CPU 0: Bank 1: 3610000000000081 at 0000000036187040
  Kernel panic - not syncing: CPU context corrupt
Mint just froze

Help T_T

---

### Post by cariboo on 2009-08-26
Try adding **nomce** to the end of the kernel line in grub eg:

```
kernel /boot/vmlinuz root=/dev/hdb1 **nomce** quiet splash 
```

The above line is from my computer running Antix, so it looks different from what it would be running Ubuntu, but it works the same.

---

