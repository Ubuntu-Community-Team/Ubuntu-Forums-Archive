---
title: "Screen resolution"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Smudger on 2009-05-06
I have my screen resolution set at 1024 x 768, all runs fine.

However, whenever I reboot the PC, the screen resolution reverts back to 640 x 400 and I have to go into System > Preferences > Display and reset it to 1024 x 768. Is there anyway to prevent this from happening; i.e: being able to save the current configuration?

---

### Post by doas777 on 2009-05-06
what kind of video card do you have, and have you installed a restricted driver for it?

you can find your card type by opening a terminal and pasting in:
```
 sudo lshw -C display 
```

---

### Post by Smudger on 2009-05-06
I have an Nvidia Geforce 6200, and the restricted driver has been installed.

---

### Post by doas777 on 2009-05-06
> **Smudger said:**
> I have an Nvidia Geforce 6200, and the restricted driver has been installed.

ok then. you want to set your res in the nvidia-settings application. you should be able to find it in your System -> Administration -> Nvidia X Server Settings applet.

if it's not there, run 
```
gksu nvidia-settings
```

if nvidia-settings doesn't ask for your password, you need to run it with gksu like above.

after you have set your resolution, apply it, and then save it to your x config file (you'll see the button). hopefully that will address the problem persistently.

good luck

---

### Post by Smudger on 2009-05-06
Thats done the trick, thanks for your help.

---

### Post by Smudger on 2009-05-06
Well, it's sorted out the screen resolution problem, only thing is now none of my Desktop Effects work anymore :confused:

---

