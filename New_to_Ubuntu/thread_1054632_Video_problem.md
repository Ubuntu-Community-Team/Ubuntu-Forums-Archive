---
title: "Video problem"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by jugodrax on 2009-01-29
Ok, I am new and old to this. The last time I used Linux was Mandrake 7.0. I installed Ubuntu 8.04 on a Gateway MX3215 and had it up and running fine. Somehow, last night, I deleted the taskbar. After searching the forums and nothing worked, I decided to reinstall since it was an experiment anyway. Now I cannot even get the screen resolution to the proper display so that I can see the full screen from left to right. It has S3 pro graphics. I have tried a few different things in the OpenChrome searches and nothing worked. When I first installed, over a Windows XP Pro install, the graphics were fine. Now I can do nothing with them. Does anyone have the answer?

Thanks:mad::o

---

### Post by spcwingo on 2009-01-30
Nine times out of ten on S3 cards I've had to use the VESA driver to get the video to display correctly (that or replace the video card).  Just reboot into recovery mode and drop out to the root terminal and enter:

```
nano /boot/grub/menu.lst
```

scroll down to the kernel line (it should look like this):

```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,1)
[COLOR="YellowGreen"]kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
```

and input:

```
xforcevesa
```

so that it now looks like this:

```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,1)
[COLOR="YellowGreen"]kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro [COLOR="Red"]xforcevesa[/COLOR] quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
```

Save (Ctrl+o) and exit (Ctrl+x).  Let us know if that helps or not.

---

### Post by jugodrax on 2009-01-30
I appreciate the help and tried it. Unfortunately it did not have any effect. Changing out the video in not an option because it is a laptop. S3 Pro onboard. What I don't understand is why it was fine on the first install and the resolution incorrect on the second. Any more ideas anyone?

Thanks

---

