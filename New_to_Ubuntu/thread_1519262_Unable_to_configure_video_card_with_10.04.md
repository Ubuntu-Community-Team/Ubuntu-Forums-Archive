---
title: "Unable to configure video card with 10.04"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by benjamin.s.vaccaro on 2010-06-27
Hi,

I used ubuntu 8.04 and 9.04 in the past and I never had any trouble configuring my Nvidea graphics card (check my signature for computer specs). 

I just installed 10.04 64bit Desktop OS on my Dell Inspiron and I'm having trouble with the graphics card. 

Process: System->Administration-> Hardware Drivers
Options: NVIDIA accelerated graphics driver (version 173)
         NVIDIA accelerated graphics driver (version  96)
         NVIDIA accelerated graphics driver (version current) [recommended]

I installed and rebooted with version 173 originally, it was advised by my very good friend.

Issues with version 173:
decrypt page was too large for screen.
Desktop cube malformed when spun. (the rectangles that appear on the sides and edges as you move. 
Inconsistency with desktop cube while rotated (black lines would appear)

With the recommended version I am still experiencing identical issues. And every once in a while my screen will "blink".

I hope other people have had this problem and there is a very easy way to correct it and properly configure my graphics card!

---

### Post by cariboo on 2010-06-27
I would suggest using the current version, as it is recommended for your video card. Once you have installed the proper driver, you shouldn't have any problems. If you do have a problem, open a terminal and type:

```
sudo nvidia-xconfig
```

This will create a working /etc/X11/xorg.conf file, and then reboot.

---

### Post by benjamin.s.vaccaro on 2010-06-27
> **cariboo907 said:**
> I would suggest using the current version, as it is recommended for your video card. Once you have installed the proper driver, you shouldn't have any problems. If you do have a problem, open a terminal and type:

```
sudo nvidia-xconfig
```

This will create a working /etc/X11/xorg.conf file, and then reboot.

Okay I just did that. I'm not quite sure what it exactly does.

---

### Post by benjamin.s.vaccaro on 2010-06-28
That did not help. The issues before creating the /etc/X11/xorg.conf file are still present.

---

