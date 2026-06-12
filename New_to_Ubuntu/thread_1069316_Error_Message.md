---
title: "Error Message"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Shozzking on 2009-02-13
I tried to open a new application to change my touch pad settings but I get this error message:
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg/conf or XF*^Config to use GSynaptics


What do I do? If its impossible for me to use this application then is it possible to disable my touch pad while I have a mouse plugged in?

---

### Post by zvacet on 2009-02-15
First make backup of your xorg.conf file

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```  

open the file

```
gksudo gedit /etc/X11/xorg.conf
```

and as message said find the line and change the value to true.Save file and reboot.

---

### Post by Nepherte on 2009-02-15
Most likely the line isn't there at all. You can then add
```
Option "SHMConfig" "True"
```
to the input device section of synpatic . If you're running Intrepid (8.10), then you will have to work with fdi files instead. See [https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig) for more information.

---

