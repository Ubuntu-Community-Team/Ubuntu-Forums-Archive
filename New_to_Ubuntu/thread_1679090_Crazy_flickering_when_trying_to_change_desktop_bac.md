---
title: "Crazy flickering when trying to change desktop background"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by phubert28 on 2011-01-31
64 bit Ubuntu 10.10 -upgraded- from 10.04.

This morning when I tried to change my screen background, both (dual 24" monitors, Nvidia card on Dell Optiplex 360 w. 4GB RAM) monitors began wild flickering on broad horizontal bands (each about 1/4 to 1/3 the screen's height) with almost complete lockout of all other actions.

Finally, it appeared the behavior starts when a new background image is selected AND that during the behavior the new image is being VERY VERY gradually drawn behind (or over) the existing image.

I never waited it out to completion. Hard powered down each time.

**

I suppose I SHOULD be adding:

How do I go back to an older driver???

There WAS a recent upgrade TO the Nvidia drivers and I think that' s LIKELY to be the source of the problem.

Just wondering if anyone else is having such a problem.

---

### Post by cariboo on 2011-01-31
Start in recovery mode, and once at the menu select netroot, once at the prompt, type:

```
nvidia-xconfig
```

the above command will create a new /etc/X11/xorg.conf file. Once the new file has been created, type:

```
reboot
```

---

### Post by phubert28 on 2011-01-31
Thanks for the response, will print that one out.

One question:

is there a space after nvidia or is that a contiguous string "nvidia-xconfig" ??

---

### Post by phubert28 on 2011-02-01
cariboo907,

The instructions worked, thanks. I wound up issuing them twice. The first time, I encountered a list of error messages, at least one in relation to the mouse.

When I ACCESSED the change background dialog and changed it, it worked fine, but when I tried to add a long list of files (as I had been able to do in the past), it locked up again.

That is why I went back to a recovery mode boot and reissued the command, that time with no errors. However, NOW I will not try to add a LIST again, although it HAD worked before. I'll just be content with adding one at a time.

I DO have some strange jpg's from NASA's APOD site. That is to say, some with unusual dimensions at very high resolution. In the screen saver, these work FINE.

????

I still suspect the upgrade to the Nvidia driver.

Thanks again,

Paul

(I always SAVE solutions like this in Tomboy notes!)

---

