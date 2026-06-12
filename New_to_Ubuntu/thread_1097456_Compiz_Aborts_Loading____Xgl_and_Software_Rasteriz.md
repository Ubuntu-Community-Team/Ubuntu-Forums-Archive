---
title: "Compiz Aborts Loading:    Xgl and Software Rasterizer Not Present"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-03-16
Trying to run compiz compositing manager but it stops with a bunch of errors as shown by Terminal below:


eld@House:/root$ sudo compiz
[sudo] password for eld: 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Is all the above errors easily straightened out by adding some additiional packages or what the heck is needed?

Ed

---

### Post by jocko on 2009-03-16
From the errors it looks like you have a problem with dbus.
Try starting dbus from a terminal:
```
sudo /etc/init.d/dbus start
```

---

### Post by orethrius on 2009-03-16
> **jocko said:**
> From the errors it looks like you have a problem with dbus.
Try starting dbus from a terminal:
```
sudo /etc/init.d/dbus start
```
Could this also be related to the X.Org bug that's supposed to be fixed in Jaunty?

---

