---
title: "rEFIt won't eject!!! Questions?"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by Suduntoo on 2011-06-02
Hey all, I am running ubuntu 11.04 on a external hd it works fine I just can't eject the rEFIt disk I am wondering if this is becaus I have to have it in the entire time I am using it if this is true then is there anyway of avoiding this by installing it on the external hd itself is this possible? Thank you for your help

---

### Post by mishathegoat on 2011-06-02
I'm pretty certain the rEFIT CD is only needed to boot. I haven't used it to boot from an external drive.. but you can open the Terminal and try either of these commands. The CD should just pop-out.

```
sudo eject
```

```
sudo eject /dev/cdrom
```

---

### Post by Suduntoo on 2011-06-02
Yeah i already tried that and I also tried to force eject but it doesn't work it makes no sense. Even with the force eject it should have ended any program that was using it and ejected it right?

---

### Post by mishathegoat on 2011-06-02
What is the output of:

```
sudo eject -f /dev/cdrom
```

Does it say that the device is busy?

You can also try:

```

sudo umount -l /dev/cdrom
sudo eject /dev/cdrom

```

---

### Post by Suduntoo on 2011-06-02
Okay ill try it  
Do you know of anyway boot loader that will work on a power pc? thank you for all your help

---

