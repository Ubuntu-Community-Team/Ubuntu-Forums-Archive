---
title: "Blank screen with ubuntu server kernel 2.6.23"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by rreadshaw on 2009-06-06
I run Ubuntu server 8.04 on a 10 year old intel pc. If I select server kernel 2.6.22 or 2.6.23 from GRUB, after the 'Loading hardware drivers' message the screen goes blank, then displays an 'Out of range' or 'Analog Input, cannot be displayed' message - it depends on the screen, I've tried three different LCD monitors.

If I run kernel 2.6.20 the screen works normally and I can log on and run commands happily.

This is not a X server problem, I'm only running in text mode. Can someone tell me what the differnce is between kernels 2.6.20 and later versions, and how I can get the screen to display correctly.

Thanks

---

### Post by scign on 2009-08-05
Perhaps it could be a boot parameter problem?

If you can boot into it with another screen, check the /boot/grub/menu.lst file. Look for when it starts listing the various boot options. It should be several sections, with a blank line in between, each looking like this:

```
title    ...
root     ...
kernel   ...
initrd   ...
```

Check the **kernel** line of the first of these sections for the parameter **vga=** then a number. This number indicates to Ubuntu what resolution to use. The link below is a good reference to what resolutions the numbers indicate.

[http://www.linuxquestions.org/blog/lifeforce4-30748/2009/5/31/a-more-complete-vga-resolutions-list-for-grub-and-lilo.-2000/]("http://www.linuxquestions.org/blog/lifeforce4-30748/2009/5/31/a-more-complete-vga-resolutions-list-for-grub-and-lilo.-2000/")

The vga parameter could also be specified in the settings above that section but since booting with certain kernels works, I would suspect that it's option-specific and therefore in the kernel parameter set.

First try removing that parameter if it's there. If that doesn't work or it's already not present on that line, try setting it to a resolution you know that monitor can support, adding it at the end of the **kernel** line. Failing that, play around with that value to see if you can find one that works with the monitor.

sci

---

