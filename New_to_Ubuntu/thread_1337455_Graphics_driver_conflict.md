---
title: "Graphics driver conflict  ?"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-25
Hi,

I don't understand my situation or what i should do?

I have lost my preferred scrn res. Evidently the suitable driver for my FX5500 card is Nvidia 173.14.xx. I installed this by using Ubuntu add/remove app.

When attempting to use the "display" app, i got the message:

"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vender's tool instead?"

Yes produces a further notice:

"You do not appear to be using the nvidia X driver. Please edit your X config file (just run 'nvidia-xconfif' as root), and restart the X server."

So I:

sudo nvidia-xconfig

and reboot.

Rebooting halts at a flikering curser and i have to edit the xorg.conf in grub to get back a basic desktop res.

---

### Post by mikewhatever on 2009-11-25
Apparently, Gnome's display manager can't handle nvidia drivers' configs, but that shouldn't pose a problem, since nvidia=xconfig is there. What is the resolution you lost, and what does it have to do with conflicting drivers?

---

### Post by wojox on 2009-11-25
Once you installed it did you need to go into System > Administration > Hardware Drivers 

and activate it, then reboot.

Log back in and run 

```
gksudo nvidia-settings
```

To set your resolution.

---

### Post by nnjond on 2009-11-25
Thanks for your interest.

I have an old (great) crt monitor which i want to keep, and i used to have 1600 x 1200 @ 75/85 hz. but at pressent im running on the vessa driver which only gives me 800 x 600 @ 60 hz

---

### Post by mikewhatever on 2009-11-25
I don't know if vesa can do 1600x1200, probably not, but it should be able to go higher, if you insist on using it:

xrandr -q  -  check the list of available modes
xrandr -s 1024x768  -  set resolution to 1024x768

The obvious thing to do to get the higher resolution back it to re-enable the proprietary driver.

---

### Post by sandyd on 2009-11-25
> **nnjond said:**
> Thanks for your interest.

I have an old (great) crt monitor which i want to keep, and i used to have 1600 x 1200 @ 75/85 hz. but at pressent im running on the vessa driver which only gives me 800 x 600 @ 60 hz
I used to have the same card as you. i found that the version that ubuntu provides didnt work at all and i instead downloaded the version for nvidia's site which worked perfectly.

---

### Post by nnjond on 2009-11-25
I use vesa because i dont know any other options!

~$ xrandr -q
Screen 0: minimum 320 x 400, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600         0.0* 
   640x480        60.0  
   640x400         0.0  
   320x400         0.0  
nnjond@den-desktop:~$ xrandr -s 1024x768
Size 1024x768 not found in available modes


Re-enable the proprietery driver:

I hope my prob is that simple. If I recall; i should look around the web and dl a suitable dr  then a manual install is neccessary. Foolishly i didn't keep any advice on how to do this.

---

