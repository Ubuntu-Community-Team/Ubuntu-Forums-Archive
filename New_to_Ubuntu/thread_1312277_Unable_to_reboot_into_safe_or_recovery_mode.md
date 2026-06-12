---
title: "Unable to reboot into safe or recovery mode"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by noctufaber on 2009-11-03
I just installed 9.10.  Everything worked great until I installed drivers for my Nvidia FX5200.  The driver installation seem to work fine without errors and then I rebooted my machine.  It now boots to a flickering or blinking login prompt.  I have read that during a reboot you can press ESC to get out of Grub and choose a safe recovery mode, but unfortunately I can't do that.  Pressing ESC doesn't take me to any menu.  It always boots to the blinking login screen.  I have my live CD which I'm able to boot into, but I'm not sure how I can fix things from there.

Can someone point me in the right direction?  I'm VERY new at this.

Thanks

---

### Post by RedSingularity on 2009-11-03
When you get to the point of the screen flickering try pressing Ctl + Alt + F1

---

### Post by noctufaber on 2009-11-03
Thanks for the reply.  I tried that, but it didn't work.

---

### Post by RedSingularity on 2009-11-03
Well ok you can boot the live cd though?

---

### Post by RedSingularity on 2009-11-03
Go into the live CD.  Once it is booted up we need a file manager with admin rights so........

sudo nautilus

This brings you an easy to use file manager.  Navigate to /etc/X11/xorg.conf.  

You will get to a part of that file that says something like...........

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"

```Try changing the line that says "nvidia" to "nv" and reboot.

---

### Post by Peter09 on 2009-11-03
If you have installed grub2 then you need to hold down the shift key during boot to get to recovery mode.

---

### Post by noctufaber on 2009-11-03
I gave up before receiving your responses.  I simply took the live cd and reinstalled it.  It only took about 30 minutes.   If I get stuck again I'll try the things you recommended.

Thanks.

---

