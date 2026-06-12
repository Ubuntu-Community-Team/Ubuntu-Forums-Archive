---
title: "Kubuntu 9.04 - Desktop and Firefox fonts"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by ctav01 on 2009-05-30
I'm pretty new to Ubuntu and I'm having trouble keeping my font/resolution settings from changing after a reboot.

I set my resolution (1400 x 1050) in System Settings > Display but when I reboot, the screen resolution defaults to a much higher setting.  So I go back into System Settings and click on Display and the screen automatically resets itself to my setting.   Every time I reboot.

Firefox does sort of the same thing.  The pages themselves render with no problems, but the Firefox fonts in the Menu and Bookmarks revert to a default size after a reboot.  I can change them in Firefox preferences and they'll be the right size after I restart Firefox but a system reboot changes them back.  Plus the Firefox right-click menus will extend off the screen depending on where I right-click.

I read in some forum posts about GTK+ settings and themes but I can find anything about them in my System Settings.

Any suggestions?

---

### Post by s.fox on 2009-05-30
Hi,

Are you using the nvidea driver?  If so:

You may need to edit /etc/X11/xorg.conf. ** MAKE A BACKUP FIRST**

Then :     
```

gksudo gedit /etc/X11/xorg.conf 

```Add each resolution you need.

If anything goes wrong please post back.

-Ash R

---

### Post by ctav01 on 2009-06-14
Thanks for the reply.  If I'm reading the documentation correctly, won't xorg.conf be overwritten by an upgrade?  If so, is there some place else I can set my monitor and resolutions that will stick around( preferably through some sort of gui)?

---

### Post by mgranet on 2009-06-14
You can do it with the nvidia-settings program. Run ```
kdesudo nvidia-settings
```

On the left of the window, click on X Server Display Configuration. Select the resolution and refresh rate you want. Click apply, then click "Save to X Configuration File" Make sure theres a check in the box that says "Merge with existing X configuration File" 

Save and Reboot.

---

### Post by ctav01 on 2009-06-15
Thanks, that seems to have done it.

---

