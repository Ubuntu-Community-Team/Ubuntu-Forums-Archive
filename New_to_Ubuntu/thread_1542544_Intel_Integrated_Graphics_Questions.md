---
title: "Intel Integrated Graphics Questions"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by glad. on 2010-07-30
Hey all, newbie here...
I have an intel integrated card (more precisely,

 description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
)

But I'm not really sure what this means. Do I have to worry about keeping its drivers updated? If so, how do I do that/how do I see what my current driver version is? Also, if I'm running a game that uses, say, DirectX, I'm under the impression that some cards can "handle" DirectX9.0 and some can't (although I could be wrong about that), but I can't find out if mine can or can't. 

Thanks in advance.

---

### Post by j7%&lt;RmUg on 2010-07-30
How old is your computer? Also just did a quick google search on your chipset, no problems by the looks of it.

No you shouldnt have to keep its drivers updated, im on Intel Integrated here and Ubuntu just picks the right driver for me.

---

### Post by cavalier911 on 2010-07-30
There is an open bug report for a flickering/flashing problem with the intel driver for Mobile 4 Series Chipset Integrated Graphics Controller.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/574449](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/574449)

---

### Post by jerenept on 2010-07-30
> **cavalier911 said:**
> There is an open bug report for a flickering/flashing problem with the intel driver for Mobile 4 Series Chipset Integrated Graphics Controller.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/574449](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/574449)

That seems to be a very minor issue.

---

### Post by glad. on 2010-07-31
> **nisshh said:**
> How old is your computer? Also just did a quick google search on your chipset, no problems by the looks of it.

No you shouldnt have to keep its drivers updated, im on Intel Integrated here and Ubuntu just picks the right driver for me.
About 9 months old. Is there any way to *check* my drivers? I.e. maybe I somehow changed a setting, and the drivers aren't updated, even if they're supposed to update automatically (although I can't think of anything I would have done...)?

---

### Post by cavalier911 on 2010-07-31
Open synaptic,click reload button, search for xserver-xorg-video-intel,

Mine shows:     Installed/Latest   2:2.9.1-3ubuntu5

On:  Linux lubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

---

### Post by Sef on 2010-07-31
> Also, if I'm running a game that uses, say, DirectX, I'm under the impression that some cards can "handle" DirectX9.0 and some can't (although I could be wrong about that), but I can't find out if mine can or can't. 

DirectX is a Microsoft product, so it would not work with Linux, unless you have WINE installed.

---

### Post by glad. on 2010-07-31
> **cavalier911 said:**
> Open synaptic,click reload button, search for xserver-xorg-video-intel,

Mine shows:     Installed/Latest   2:2.9.1-3ubuntu5

On:  Linux lubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
Mine says Installed/Latest 2:2.6.3-0ubuntu9.3 -- does that mean that mine is not up-to-date? Or do you have a different "set" of drivers than me?

> DirectX is a Microsoft product, so it would not work with Linux, unless you have WINE installed.

Yes, I do have WINE installed.

---

