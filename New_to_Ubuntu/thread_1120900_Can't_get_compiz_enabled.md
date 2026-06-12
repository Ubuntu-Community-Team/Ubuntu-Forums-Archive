---
title: "Can't get compiz enabled"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by Fedexpress on 2009-04-09
Hey Friends,
I have tried out compiz command and here is the output

abhishek@Matrix:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:05.0 0300: 1002:5a61 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x2c0bb83 specified for 0x2c0bba2 ().


Output of lspci|grep VGA

abhishek@Matrix:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]

Any suggestions or hint from here on

Thanks

---

### Post by Therion on 2009-04-09
Open the restricted drivers manager in System/Administration/Driver Manager or Hardware Manager (whatever it's called now) and select the ATI restricted driver.

Then you'll need to install the **xserver-xgl** package:```
sudo apt-get install xserver-xgl
```
That should get you up and running.  Should.

---

### Post by DigiTan on 2009-04-09
Also, the mistake I made after installing that stuff was forgetting to enable advanced effects in the desktop settings.  :P

---

### Post by lavinog on 2009-04-09
> **Therion said:**
> Open the restricted drivers manager in System/Administration/Driver Manager or Hardware Manager (whatever it's called now) and select the ATI restricted driver.

Then you'll need to install the **xserver-xgl** package:```
sudo apt-get install xserver-xgl
```
That should get you up and running.  Should.

xgl is no longer required, nor is it recommended
the restricted driver supports aiglx

---

