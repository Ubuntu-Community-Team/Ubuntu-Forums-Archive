---
title: "CPU temp monitor?"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by insanity99 on 2009-10-15
hey guys i just OC'd my q6600 to 3.2GHz and need to monitor my temps. 

i have im sensors and the applet but it say 'No Sensors Enabled!' even after doing the sudo detect-sensors' command and saying add lines automatically. i also understand i can add this to my conky but i am not good with that stuff.

thanks!

---

### Post by doas777 on 2009-10-15
did you run 
```
sudo sensors-detect
```
and add the required modules after installing lmsensors?

---

### Post by insanity99 on 2009-10-15
i did that command yes and said yes to all questions. do i need to do anything else?

---

### Post by doas777 on 2009-10-15
no, it seems like you may not have any accessible sensors. try a reboot, but you may be out of luck.
also when you add the modules via the script, the default answer to that question is 'no' not yes. are you sure you answered that one as yes (not trying to call you a liar; i've just made that mistake before)?

---

### Post by insanity99 on 2009-10-15
i just type in yes so i dont se how i could have made such an error really. but i can monitor my temps in windows no problem.

---

### Post by doas777 on 2009-10-15
> **insanity99 said:**
> i just type in yes so i dont se how i could have made such an error really. but i can monitor my temps in windows no problem.

nope that would do it. give her a reboot (the pannels always need to be reloaded before the applet responds).

---

### Post by insanity99 on 2009-10-15
i didn't restart but i did log off then on again. cant access my pc now though on dads laptop. hope this fixes it i really need this or i will have to stay on crappy windows.

---

