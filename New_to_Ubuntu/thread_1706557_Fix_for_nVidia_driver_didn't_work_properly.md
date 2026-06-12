---
title: "Fix for nVidia driver didn't work properly"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by LAtrumpet on 2011-03-14
I used this fix:

[http://ubuntuforums.org/showpost.php?p=9955270&postcount=6](http://ubuntuforums.org/showpost.php?p=9955270&postcount=6)

to solve a graphics problem (preventing low graphics mode) on my system, but the nVidia options under preferences aren't working and saying they're not configured properly. I do what the prompt says and then I'm back to the tty1 prompt with no xserver..

The fix gives me the proper resolution, but dual monitor setups crash X. 

Any ideas? Thanks!

---

### Post by mikewhatever on 2011-03-14
Don't think you've been using the right instructions for your problem. When Maverick was released in October 2010, the nvidia-96 driver for older cards didn't work with xserver 1.9, which made upgrading fail. Nvidia has updated the driver since so that there is no need to resort to nv. 
Try re-enabling the nvidia driver suggested for your card. If it doesn't work properly after a reboot, try the following:

```
**ctrl+alt+f1** - will drop you to a tty

login with your username and password

**sudo service gdm stop** - will stop xserver

**sudo nvidia-xconfig** - will write a new config file

**sudo service gdm start** - will restart xserver
```

---

