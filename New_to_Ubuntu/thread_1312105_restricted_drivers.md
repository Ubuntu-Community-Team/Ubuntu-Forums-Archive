---
title: "restricted drivers?"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by rosswmcgee on 2009-11-02
Install or not? I just did a clean install and option is awaiting!

---

### Post by underworld288 on 2009-11-02
What drivers are they? Video? Wireless card?

---

### Post by rosswmcgee on 2009-11-02
Nvidia drivers for 3 d I did not install them closed the window and the option is

gone. So if I need to install them where do I locate the option using 9.10.

---

### Post by cjohnston on 2009-11-02
System > Admin > Hardware drivers

I'd install them

---

### Post by rosswmcgee on 2009-11-02
and would you use the recommended?

---

### Post by dalee on 2009-11-02
Hi,

Yes I always select the recommended nVidia driver with no problem. 

dalee

---

### Post by rosswmcgee on 2009-11-02
Roger Out and thanks

---

### Post by rosswmcgee on 2009-11-02
Now that I put the drivers in I can not get screen I just get the boot up ubuntu sound.

---

### Post by rosswmcgee on 2009-11-02
Big mistake. I should have left every thing alone, cannot reboot after installing the

drivers, Ubuntu boots but no video, now I have to do another clean install.

---

### Post by iMisspell on 2009-11-03
> **rosswmcgee said:**
> Big mistake. I should have left every thing alone, cannot reboot after installing the

drivers, Ubuntu boots but no video, now I have to do another clean install.

You can try and restart (even a "hard-reboot", hitting reset button on machine) to "safe mode" (for get what its called in Ubuntu) and select the "fix video" option, should default back to your old setting (xorg.conf).

---

### Post by cariboo on 2009-11-03
IF you can get to a console. Alt-F1 at the prompt type:

```
sudo nvidia-xconfig
```

The above command will create an /etc/X11/xorg.conf file that should work for you. Once a new xorg.conf file has been created you will need to rebot, at the prompt type:

```
sudo reboot
```

If the above doesn't work, you should be able to start in recovery mode, once at the menu choose drop to root prompt with networking, then at the prompt run the above command with out using sudo, once it is finished type exit at the prompt, then choose resume from the menu.

---

