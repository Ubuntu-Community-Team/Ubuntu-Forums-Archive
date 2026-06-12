---
title: "Compiz problem"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by openbox1 on 2009-07-19
I am new in ubuntu can you help me guys!

i already install my compiz but nothing happens, i already install my Nvidia Geforce 6100 still nothing happen? what seems to be the problem.:confused:

---

### Post by wojox on 2009-07-19
Did you install CompizConfig Settings Manager?
Also go to System > Prerence's > Appearance  And click the Visual Effects then click the Extra radio button.

---

### Post by openbox1 on 2009-07-19
Error! Desktop effects could not be enable... hmm

---

### Post by andrea000 on 2009-07-19
run compiz from the terminal

applications>>accessories>>terminal
compiz

post output on here

---

### Post by openbox1 on 2009-07-19
openbox@openbox-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by openbox1 on 2009-07-19
im using laptop and my  video card is Nvida Geforce Go 6100 but it seems that virtual effects is looking for a driver. what seems to be the problem? is ubuntu supports NVidia drivers?

---

### Post by overdrank on 2009-07-19
Threads merged. :)
Hi and what is the version of Ubuntu are you using?
Have you installed the nvidia drivers?

---

### Post by openbox1 on 2009-07-19
im using the ubuntu 9.04 that i ordered last week frm this site. this that for Intel processor only bcoz im using AMD 64 athlon x2. is there conflict?

---

### Post by overdrank on 2009-07-19
> **openbox1 said:**
> im using the ubuntu 9.04 that i ordered last week frm this site. this that for Intel processor only bcoz im using AMD 64 athlon x2. is there conflict?

No that should not be a issue. I feel the nvidia driver is the issue. 
You may look at [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by openbox1 on 2009-07-19
sir is this right?

openbox@openbox-laptop:~$ compiz-check
bash: compiz-check: command not found
openbox@openbox-laptop:~$

---

### Post by openbox1 on 2009-07-19
> **openbox1 said:**
> openbox@openbox-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

When i try compiz this is what happen always..

---

### Post by pytheas22 on 2009-07-20
You might have better luck if you installed the driver for your graphics card using a program called envy.  You can install envy by typing:
```

sudo apt-get update
sudo apt-get install envyng-gtk
```

Then start it by typing:
```

sudo envyng-gtk
```

Follow the instructions on your screen for installing the nvidia driver.  When it's done, reboot, then try running compiz again.  Does this help?  If not, what is the output of:
```

lspci -nn | grep -i nvidia
```

---

### Post by openbox1 on 2009-07-20
Sir i just downgraded my 9.04 to 8.10, i think i just installed my nvidia right but, 3d cube is now working. but when i type compiz

> Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
> nothing happens here....


what must be the right output?

do you know this error?

---

### Post by pytheas22 on 2009-07-20
If the cube is working, then compiz is working.  The error messages you posted may be the result of trying to start compiz when it's already running; I'm not sure.  But are you able to enable desktop effects now?

---

### Post by openbox1 on 2009-07-20
yeah! compiz is already working. and my friend told that is already done.

---

