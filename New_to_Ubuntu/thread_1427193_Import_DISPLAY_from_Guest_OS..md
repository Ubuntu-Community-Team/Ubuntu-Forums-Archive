---
title: "Import DISPLAY from Guest OS."
date: 2010-03-11
forum: New to Ubuntu
---

### Post by jirudayaraj on 2010-03-11
Hi Guys,
I am very new to Ubuntu and currently have Ubuntu 9.10 on my Dell INISPIRON 1525.
 
The installation was a breeze and everything worked well.
 
I am a Oracle DBA by profession and I used VMWare in the past on WindowsXP to setup Oracle10gR2 RAC on them.
 
Now on Ubuntu I have installed SunVirtualBox 3.1 and installed RHEL5 as Guest OS.
Once again everything went fine until I got to a stage where I need to export DISPLAY from the Guest OS to my Ubuntu 9.10 Desktop. I am using GNOME.
 
I tried various things like:
a) run xhost + as root from GNOME and exported DISPLAY from Guest OS to the primary NIC on Ubuntu.
b) run xhost 192.168.56.10(IP address used on the Guest OS) as root from GNOME and exported DISPLAY from Guest OS to the primary NIC on Ubuntu.
 
But either of these work. When ever I run 'xclock' or 'xeyes' from the Guest OS I get a message 'Can't Open Display 192.....:0.0'
 
Also I would like to mention from GNOME Desktop I connect to Guest OS using ssh.
 
I login as 'root' to the Guest OS.
 
Please let me know how to enable Ubuntu to allow incoming DISPLAY from Guest OS.
 
Thanks for all your help.
 
 
Regards,
Raj.

---

### Post by NT4usB on 2010-03-11
(wag) You using x forwarding?```
$ ssh -X bla...
```

ed: I did notice x forwarding would not work for me when I ssh -X from my 9.04 machine to a new install of 9.10. Something's not configured on the 9.10 box. Enabling x forwarding or something...
Haven't dug into it yet.

---

### Post by jirudayaraj on 2010-03-11
Thanks a lot.

That worked. ssh -X <Guest OS Name> worked....

Thanks once again for your timely help.:p

Raj.

---

