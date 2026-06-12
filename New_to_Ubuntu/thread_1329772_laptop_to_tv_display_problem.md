---
title: "laptop to tv display problem"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Kai69 on 2009-11-17
I have just started useing ubuntu and i cant connect my laptop to tv via hdmi lead graphics card is nvidia geforce 8400m gs laptop is dell xps m1330 in display i get a message 

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead? 

I choose yes card shows my tv as being avalable but no sound or vision 
please help

---

### Post by RedSingularity on 2009-11-18
Did you install the nvidia Linux Drivers?  The binary ones?

System>Admin>Hardware drivers.

---

### Post by realzippy on 2009-11-18
Think he would not have been asked for his graphics driver vendor tool...
if he had not nvidiadrivers installed...

Terminal:

**gksudo nvidia-settings**

---

### Post by Kai69 on 2009-11-18
no im very new to this sort of thing only installed ubuntu on monday because xp went nuts on me . do i have to go to nvidia for the driver

ok done what you said nvidia recognises tv when hdmi lead in model and number on graphic card screen but still no picture or sound on tv 
laptop screen is 0 tv screen is1

---

### Post by RedSingularity on 2009-11-18
Nope.  Look in System>Admin>Hardware Drivers.

---

### Post by Kai69 on 2009-11-18
updated driver saays version 185 recomended clicked to use and restarted ubuntu still the same.

---

### Post by realzippy on 2009-11-18
> **Kai69 said:**
> updated driver saays version 185 recomended clicked to use and restarted ubuntu still the same.

still same or is nvidia 185 now installed?If so,try:
[B]
gksudo nvidia-settings[/B]

---

### Post by RedSingularity on 2009-11-18
> **realzippy said:**
> still same or is nvidia 185 now installed?If so,try:
[B]
gksudo nvidia-settings[/B]


Yes now try the above in terminal to bring up the menu.

---

### Post by Kai69 on 2009-11-18
ok 185 is installed and i restarted laptop nvidia recognises tv make and model i have pressed Fn andF8 crt/lcd i now have the ubuntu display icon saying (could not set configuration for crt321 . if i go into system /preferences diplay . i still get the same message if i open display and click detect monitors nothing happens

---

### Post by teward on 2009-11-18
problem with the monitor maybe?  perhaps nvidia can't configure its resolution.

---

### Post by realzippy on 2009-11-18
you cannot configure your TV in nvidia-settings?
Is it recognized then?(Monitor1,Monitor2 or something?)

BTW,did you install **nvtv** ?!If not,do so:

**sudo apt-get install nvtv**

---

### Post by Kai69 on 2009-11-18
ok done that monitor is DPF-0 on GPU-0 tv DPF-1 on GPU-0 and on twinview still nothing i will try again tomorrow

---

### Post by spillin_dylan on 2009-11-18
I don't know if this will work for you or not, but I've got a Toshiba Satellite with an Intel card with HDMI out, and I have to log out and log back in again after plugging it in for it to work right.

Maybe that is something to try... Maybe you already have....

---

### Post by Kai69 on 2009-11-19
hi all back again i have pluged hdmi lead in and switched laptop on with the power and media buttons but still the same i have googled this problem and it seems to affect the dell xps m1330 quiet a lot but i shall persevere thanks for all the help so far you dont get this from ms

---

### Post by realzippy on 2009-11-19
You could try the newest nvidiadriver.They fixed a lot;read changelog,or just install it.  (190.42)

---

### Post by Kai69 on 2009-11-19
hi realzippy i have downloaded the new linux nvidia drver 190.42 but how do i install it i have double clicked it but comes up with a warning 
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

current locale(utf-8
tried the other option western (iso-8859-15) still no luck

---

### Post by realzippy on 2009-11-20
> **Kai69 said:**
> hi realzippy i have downloaded the new linux nvidia drver 190.42 but how do i install it i have double clicked it but comes up with a warning 
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

current locale(utf-8
tried the other option western (iso-8859-15) still no luck

To install NVIDIA driver (file is on Desktop):

1. Uninstall current (185?) Nvidiadriver with restricted-driver tool
   (System/administration)

2. Reboot

3. Log out

4. Press Alt+Ctrl+F2

5. Log in at shell

6. Stop X by typing: **sudo /etc/init.d/gdm stop**

7. Navigate to Desktop: **cd Desktop**

8. Install driver:  **sudo sh NV **(press Tab to autocomplete   NVIDIAfilename)

9. Answer asked questions during installation with "yes"

10. reboot:  [B]sudo reboot
[/B]

---

