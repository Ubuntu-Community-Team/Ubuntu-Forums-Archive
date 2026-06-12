---
title: "firefox touchpad shortcuts help!"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by oralphie on 2009-06-20
i need help in disabling the touchpads shortcuts.
every time i tap the top right corner it sends me to a recently closed tab

thanks in advance

---

### Post by tarps87 on 2009-06-22
I don't know the answer but it probably can be resolved by edditing the firefox config page. You can try googleing firefor about:config
Becareful when editing this as it may brake your firefox install, oh and look out for the dragons (it will make sense soon).
I will have a look when I get home and let you know if I find anything

---

### Post by oralphie on 2009-06-27
I couldnt understand it, still need help please

---

### Post by tarps87 on 2009-06-29
Unfortunalty I can find anything in the config file about the touchpad, what version of firefox are you using. Also can you post the contents of your xorg file
```
gedit /etc/X11/xorg
```

---

### Post by oralphie on 2009-07-08
im using firefox 3.0.11, as for the code, does it go in the terminal, sorry for late reply

---

### Post by tarps87 on 2009-07-09
Yep, if you copy and paste the contents into code tags the # button on the toolbar.
I haven't yet found a way to enable this on my system, was this default behaviour for your install?

---

### Post by tarps87 on 2009-07-09
Just done a bit more reading, it sound like the settings are RTCornerButton. This may be set in the xorg file or using the new hal config.
Can you also post the output of
```
ls /etc/hal/fdi/policy
```

Thanks

---

### Post by oralphie on 2009-07-12
preferences.fdi is the output

---

### Post by tarps87 on 2009-07-13
In that case the xorg.confg file is our best bet, if you could post that we can see if that is where it is set

---

