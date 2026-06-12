---
title: "cant enable desktop effect, once worked now wont."
date: 2009-11-27
forum: New to Ubuntu
---

### Post by spartanX70 on 2009-11-27
i have been using Ubuntu for some time now, but since i moved from my mentor, there are things i still don't know.

im running a 


                                            Intel®  Integrated Graphics Media Accelerator 4500MHD                                     
and the desktop effect were working rebooted my laptop and they stop can enable them now, tired every thing i know.
can some on help me

---

### Post by japhyr on 2009-11-27
Do you have compizconfig-settings-manager installed?

Are you sure compiz is turned on?

---

### Post by spartanX70 on 2009-11-29
yes, its turned on but it says desktop effects cant be enabled, i went to the appearance preferences to visual effects to turn on the extra effects on and that didn't work, 

so yeah..what do i do?
isnt there a way to stop it from not letting me enable desktop effects

---

### Post by teward on 2009-11-29
A thought:  Some hardware drivers won't let desktop effects run.  I ran into this problem with the proprietary drivers for the *nVidia Quadro NVS 160M 512MB* installed in my laptop, and also with some programs I use (they don't like compiz).  My laptop doesn't need the effects, so I just disabled them, nonetheless, it seems to be some hardware incompatibilities that might lead to the effects not working.

---

### Post by spartanX70 on 2009-11-29
thats a very sound thought, iv heard if that happening, i should have thought about that myself, but do you happen to know of a way around it?

---

### Post by SunnyRabbiera on 2009-11-29
There not be any workaround, but its not like its essential to have desktop effects.
Though it is good for effect I admit.
You may want to try other distros if bling is that important, personally I am having a grand time with openSUSE 11.2
But I am glad that with linux that if you don't get desktop effects you are still left with a fully functional OS, unlike Vista or windows 7 where if Aero doesnt work you are practically crippled...

---

### Post by spartanX70 on 2009-11-29
ah, you speak of openSUSE, thats the first time i have heard if it in a while, hows its working for you?

and another i cant use any of my 3d modeling applications i use, so i guess that related to the deaktop effects not being on?

and is there a way i can be sure what kinda of graphics card i have?

---

### Post by japhyr on 2009-11-29
If they were working on the computer you're on before, and they're not working since the last reboot, I don't think it can be a hardware issue.  To be clear, can you go to System>>Preferences>>CompizConfig Settings Manager?  Or are you using something else under System>>Preferences?

You can find your graphics card by opening a terminal and typing "lspci | grep VGA".

---

