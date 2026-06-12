---
title: "How do I change/add 1024x768 to my display preferences. &lt;8.10&gt;"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by whoscheesemine on 2008-12-25
Okay, well it seems that xorg.conf isn't used anymore. Once again I have a Sony Vaio that I must put Xubuntu on and I'm having my typical issue of having to customize to create an environment that can be view in 1024x768. Now that I no longer have a xorg.conf I cannot figure out how to do this. I'm going to go ahead and sale this computer to my friend in 800x600, but I promised him I'd fix that as soon as I could.

If it helps at all. My display adaptor is an on-board SIS 630/750. Either or doesn't matter. I happened to find a linux driver from the SiS website in .tgz format, but I couldn't figure out how to run its contained file or an application that lets me add/edit drivers. Unfortunately the application named "Hardware Drivers" merely scans for any restricted hardware drivers that one may want.

Any idears?

---

### Post by linux_tech on 2008-12-25
Try
```
 xrandr
```
see if it shows up as available resolution
if so type
```
xrandr -s 1024x768
```

---

### Post by linux_tech on 2008-12-25
You can also try
```
gksudo displayconfig-gtk
```

what file is extracted from the .tgz file?

---

