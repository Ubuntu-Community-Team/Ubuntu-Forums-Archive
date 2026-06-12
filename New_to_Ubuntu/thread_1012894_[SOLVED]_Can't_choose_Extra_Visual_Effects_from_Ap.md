---
title: "[SOLVED] Can't choose Extra Visual Effects from Appearance."
date: 2008-12-16
forum: New to Ubuntu
---

### Post by looi76 on 2008-12-16
Yesterday, I have installed **Screenlets** and **Advanced Desktop Effects Settings (ccsm)** and later I uninstalled them because I didn't really like them. Well, today I wanted to turn the Extra Visual Effects back on but got this error: *Desktop effects could not be enabled.*

[[IMG]http://img296.imageshack.us/img296/1874/screenshotlj8.th.png[/IMG]](http://img296.imageshack.us/my.php?image=screenshotlj8.png)

Need help turning it back **ON**.

---

### Post by Michael.Godawski on 2008-12-16
Not sitting at my Ubuntu machine now ( writing this from the University and they have only OpenSuse :p)

but
are your graphic drivers still activated ?
is your compiz still installed? Perhaps it was somehow removed during the de-installation of the packages mentioned above?

---

### Post by looi76 on 2008-12-16
> **Michael.Godawski said:**
> 
are your graphic drivers still activated ?
How can I check that my graphic driver is still running?

---

### Post by Michael.Godawski on 2008-12-16
As I said from the top of my head:

System > Administration > Hardware Drivers
Your card should be listed there with a nice green light next to it.

You can also check it via the terminal:
```
sudo lshw -C display
```
Post the output please.

---

### Post by looi76 on 2008-12-16
Looks like the graphics driver is activated.

[[IMG]http://img254.imageshack.us/img254/1597/screenshot1ud4.th.png[/IMG]](http://img254.imageshack.us/my.php?image=screenshot1ud4.png)   [[IMG]http://img168.imageshack.us/img168/9979/screenshot2tj0.th.png[/IMG]](http://img168.imageshack.us/my.php?image=screenshot2tj0.png)

---

### Post by grazed on 2008-12-16
go into synaptic.

system>admin>synaptic package manager.

do a search for "compiz" without the quotes, expand the window to show the full list of results, and post a screenshot of that.

---

### Post by BDNiner on 2008-12-16
Yes it is activated, is there a reason why u are using the 173 drivers instead of the 177 drives? My guess is that compiz is no longer your window manager it may have switched back to metacity. What happens when  u try 
```

compiz --replace

```

---

### Post by looi76 on 2008-12-16
> **grazed said:**
> go into synaptic.

system>admin>synaptic package manager.

do a search for "compiz" without the quotes, expand the window to show the full list of results, and post a screenshot of that.

Looks like Compiz is still installed :tongue:

[[IMG]http://img72.imageshack.us/img72/9889/screenshot3ye2.th.png[/IMG]](http://img72.imageshack.us/my.php?image=screenshot3ye2.png)

What should I do now?

---

### Post by BDNiner on 2008-12-16
Did you try the command? Run it from a terminal window.

---

### Post by applefox on 2008-12-16
I had the same thing happen to me it turns out I had accidentally switched to metacity. Good luck :)

---

### Post by looi76 on 2008-12-17
Just before days I have installed Ubuntu. So, to resolve the problem I have just reinstalled ubuntu :P

---

### Post by Number X on 2008-12-21
**ADDENDUM:** *Never mind. I found my solution elsewhere. :)*

I have practically the exact same problem.

As near as I can figure, it happened after I tried playing a video through my LCD-TV via RGB and after I tried adjusting my Screen Resolution.

Here is my "sudo lshw -C display" output:

```
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
```

Nothing is in my "Hardrive Drivers" list but I don't think there ever was since my Laptop uses Intel Graphics.

"compiz --replace" produces these results:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
```

"Thank you's" to all who will help me. :)

---

