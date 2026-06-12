---
title: "Visioneer OneTouch 5300 USB Scanner"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2010-03-20
Hi I have a Visioneer OneTouch 5300 USB Scanner and ubuntu doesn't recognize it. Can anyone advise?

I have installed the [libsane-extras packages]("https://help.ubuntu.com/8.04/printing/C/scanning.html") as instructed but it is still not detected.

---

### Post by ellgor on 2010-03-21
Hi,

Try running xsane from a terminal :

sudo xsane

if it works ignore the warning message and carry on.

Regards, Ellgor.

---

### Post by Mega_Fauna on 2010-03-21
> **ellgor said:**
> 

Try running xsane from a terminal :

sudo xsane


Hi, thanks for the reply. It doesn't detect the scanner. Here is the bash output before the Xsane window appears.

> user@computer:~$ sudo xsane
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:255: Invalid symbolic color 'selected_fg_color'
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:255: error: invalid identifier `selected_fg_color', expected valid identifier
[umax_pp_low] sync610p failed (got 0x78 expected 0x38)! (umax_pp_low.c:3733)
[umax_pp_low] sync610p failed! Scanner not present or powered off ...  (umax_pp_low.c:6363)
[umax_pp_low] initTransport610p() failed (umax_pp_low.c:6673)
[gphoto2] init_gphoto2: error: serial:/dev/ttyd1 is not a valid gphoto2 port.  Use "gphoto2 --list-ports" for list.

---

### Post by Mega_Fauna on 2010-03-22
bumpity bump bump.

---

### Post by Mega_Fauna on 2010-03-25
Bump!

---

