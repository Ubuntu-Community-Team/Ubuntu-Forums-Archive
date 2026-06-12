---
title: "[SOLVED] login screen resolution"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by nerdking on 2008-12-19
my normal screen resolution is 1024x768 (4:3). how ever my login screen is a different resolution and incredibly of the resolution it is supposed to be., how do i fix this?

---

### Post by Michaelg14 on 2008-12-19
What video driver are you using?  Is your resolution ok after you log in?

---

### Post by donkyhotay on 2008-12-19
What version of ubuntu are you using? If your using hardy then manually editing the xorg.conf files will fix this (just remove all reference to other resolutions). I've heard that they've gotten ready of this in intrepid so that might not be applicable.

---

### Post by nerdking on 2008-12-19
> **Michaelg14 said:**
> What video driver are you using?  Is your resolution ok after you log in?

i have a sis with a fully updated driver after i log in it is the resolution it is set at so it normal. its only the login screen.

---

### Post by nerdking on 2008-12-19
> **donkyhotay said:**
> What version of ubuntu are you using? If your using hardy then manually editing the xorg.conf files will fix this (just remove all reference to other resolutions). I've heard that they've gotten ready of this in intrepid so that might not be applicable.


i have 8.10, so i cant edit that.

---

### Post by starcannon on 2008-12-19
You can still edit the xorg.conf on the new xserver, add to:
Section "Screen"
SubSection "Display"
     Virtual 1024 768
EndSubSection

On some hardware combinations this has fixed my login screen resolutions, your mileage may differ; worst that happens is you just remove the modification and reboot if it causes things to be worse.

GL and have fun

---

### Post by Michaelg14 on 2008-12-19
I'm afraid I can't help much, I use automatic log-in so I never see a log-in screen.  If you use an nvidia display driver you can try loading nvidia-settings from synaptic package manager.

Good luck

---

### Post by graceful1 on 2008-12-20
> **starcannon said:**
> You can still edit the xorg.conf on the new xserver, add to:
Section "Screen"
SubSection "Display"
     Virtual 1024 768
EndSubSection

On some hardware combinations this has fixed my login screen resolutions, your mileage may differ; worst that happens is you just remove the modification and reboot if it causes things to be worse.

GL and have fun

Thank you so much! I was having the same problem, and this did the trick! Thanks!  :P

---

