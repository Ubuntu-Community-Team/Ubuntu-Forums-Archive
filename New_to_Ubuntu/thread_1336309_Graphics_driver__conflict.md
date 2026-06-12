---
title: "Graphics driver  conflict ?"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-24
Hi,

I have lost my preferred scrn res. Evidently the suitable driver for my FX5500 card is Nvidia 173.14.xx. I installed this and when attempting to use the "display" app, i got the message:

"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vender's tool instead?"

Yes produces a further notice:

"You do not appear to be using the nvidia X driver. Please edit your X config file (just run 'nvidia-xconfif' as root), and restart the X server."

So I:

sudo nvidia-xconfig

and reboot.

Rebooting halts at a flikering curser and i have to edit the xorg.conf in grub to get back a basic desktop res.

---

### Post by jimmy the saint on 2009-11-24
how did you install it?  Did you use the restricted driver tool?  Did you download it from nvidia?  Did you use Envy?

---

### Post by nnjond on 2009-11-24
thank for your interest.

I used Ubuntu add/remove app. Went without a hitch.

---

