---
title: "Nvidia xconfiguration"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Binny88 on 2009-01-27
I used the graphical interface for saving the nvidia x server settings.The default screen resolution was 800x480 but i wanted 1024x768. I applied the settings & they were applied but i couldnt save the settings. I did mange to save them after visiting the forum by launching the program as root(sudo).
But when i restart i still go back to the default value 800x480. What could be wrong?

---

### Post by overdrank on 2009-01-27
> **Binny88 said:**
> I used the graphical interface for saving the nvidia x server settings.The default screen resolution was 800x480 but i wanted 1024x768. I applied the settings & they were applied but i couldnt save the settings. I did mange to save them after visiting the forum by launching the program as root(sudo).
But when i restart i still go back to the default value 800x480. What could be wrong?

Hi and what is the model of the graphics card what version of Ubuntu are you using?
Have you tried the xfix option by booting into recovery mode, recovery mode is usually the second option from the grub when booting.
Edit: I just saw your other post and you are using Hardy 8.04, you may make sure your driver is enabled under system, administration, hardware.
Also you may try the command ```
gksu displayconfig-gtk
``` and adjust your monitor.

---

### Post by Binny88 on 2009-01-27
I am using the nvidia en7200gs.I tried the command & it tells me that i am currently using a 1024x768 resolution. It happens when i restart the pc it goes back to 800x480.

Thanks

---

### Post by overdrank on 2009-01-27
> **Binny88 said:**
> I am using the nvidia en7200gs.I tried the command & it tells me that i am currently using a 1024x768 resolution. It happens when i restart the pc it goes back to 800x480.

Thanks

Ok you may try and uninstall the nvidia drivers and reboot, after reboot try to enable the driver again. This is a issue on Hardy.

---

### Post by Binny88 on 2009-01-27
Thanks, But no thanks I had a lot of installing the current driver. I had upgraded from Gutsy (which ran smoothly)to hardy a few days ago.The upgrade wasnt fully successful & i had to fully install hardy & the nvidia drivers were troublesome.
I will wait for some other fix.
Thanks for the help anyway

---

### Post by rafaelsousa on 2009-01-27
Try to replace your xorg.conf...

If you run

```
X -configure
```

as root, you should get a new one in /root directory. But you must do it with your gdm down. 

stop gdm, the run X -configure as root

---

### Post by overdrank on 2009-01-27
> **Binny88 said:**
> Thanks, But no thanks I had a lot of installing the current driver. I had upgraded from Gutsy (which ran smoothly)to hardy a few days ago.The upgrade wasnt fully successful & i had to fully install hardy & the nvidia drivers were troublesome.
I will wait for some other fix.
Thanks for the help anyway

Ok I understand you may try the xfix option in post #2.

---

