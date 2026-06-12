---
title: "no sound in flash after update to 2.6.28-16"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by wobin77 on 2009-10-23
As suggested, a new thread. 

After the kernel update (2.6.28-15 to 2.6.28-16) i have no sound while browsing with firefox with streaming media. (flash)
Other sounds do work. Like Rythmbox. 

If i boot with 2.6.28-15 this is fixed and i have sound again.

---

### Post by wojox on 2009-10-26
Reinstall Flash:

```
sudo apt-get --purge remove flashplugin-nonfree
```

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by wobin77 on 2009-11-01
hi, 

the problem was that after the update, i couldn't play two sounds at once. Like if i had rythmbox playing, my flash had no sound. If i stopped rythmbox sound was back in flash...

But, just installed 9.10 and all 's working great! 

For flash on 64bit i followed this guide:

[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

---

### Post by sheedatali on 2009-11-06
The problem still exists for me. I have standard 9.10 and occasionally flash stops giving sound output. Same is true for some other applications such as Wine (spotify etc). I just have guess which applications might be using sound and close them all and start the one I want and sounds comes back.


It is so annoying, you would think that Ubuntu/Linux developers would have addressed such a basic yet very important issue but it still persists. For novice users things like that are enough to get them confused and clueless and look for alternative operating systems!!!

---

