---
title: "adjusting resolution in VirtualBox for Ubuntu in Windows"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-04
HI,
I was wondering how to adjust resolution in VirtualBox for Ubuntu installed in Windows XP? Thanks in advance!

---

### Post by skymera on 2009-03-04
If you go to Virtual Box settings, is there an option to set screen size?

There's one similar in VMware i use.

If you can't, is it possible to change the resolution of the guest OS?

---

### Post by Sirron on 2009-03-04
This can be difficult, as the previous poster suggested, you should start by installing the guest additions.

Changing the resolution then (according to some sources) should be as simple as resizing the window. However, I have never seen that actually work with a non-windows guest.

Instead, I believe you'll need to edit your xorg.conf file to force the resolution you want to use. After installing the additions you may find that you can set ubuntu to 1024x768, so if that's good enough you might be able to avoid editing anything further.

---

### Post by flylehe on 2009-03-04
Thank you everyone!
I followed [http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/), however when I clicked Devices > Install Guest Additions..., a CD file called "VBOXADDITIONS_2.1.4_42893" is downloaded under Desktop of guest Ubuntu, and it is not autorunable. What shall I do next?

---

### Post by Locke_99GS on 2009-03-04
Mount it and run the file specific to your guest OS and arch.

Guest additions works perfectly for me, with mostly Linux guests, resizing is as simple as resizing the window. The mouse capture is great too, btw.

---

### Post by andrew.46 on 2009-03-04
Hi flylehe,

> **flylehe said:**
> [...]a CD file called "VBOXADDITIONS_2.1.4_42893" is downloaded under Desktop of guest Ubuntu, and it is not autorunable. What shall I do next?

you will have to run the file manually:

```
$ cd /media/cdrom
$ sudo sh ./VBoxLinuxAdditions-x86.run
```

and then you should be right. Different file for 64bit.

Andrew

---

