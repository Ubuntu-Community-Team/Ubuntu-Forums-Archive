---
title: "file browser crashes"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by psyk117 on 2009-11-15
I go to open my Documents folder, and it loads, but then crashes. I'm using Ubuntu 9.10, help?

---

### Post by Paqman on 2009-11-15
Go to Applications > Accesories > Terminal and launch the file browser by giving the command:
```
nautilus
```

Then try to get it to crash again, and when it does, post the output from the terminal here.

---

### Post by psyk117 on 2009-11-15
(nautilus:2081): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2081): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2081): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2081): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentation fault

---

### Post by psyk117 on 2009-11-15
bump

---

### Post by philinux on 2009-11-15
As this problem has not been resolved. See your previous threads. If you got home on its own partition I would reinstall.

You may have tweaked something inadvertently that can never be tracked down.

---

### Post by psyk117 on 2009-11-15
alright...
how can I reinstall?

---

### Post by mprince on 2009-11-16
-

---

### Post by psyk117 on 2009-11-16
I got this output:
bash: /home/psyk117/.gconf/apps/nautilus: No such file or directory

---

### Post by brij on 2009-11-16
just delete the whole .gconf folder under your home direcotory that will fix the problem but you will lose all your pref. though

---

### Post by itsbrad212 on 2009-11-16
try installing thunar. its like nautilus but quicker :D

[http://thunar.xfce.org/index.html](http://thunar.xfce.org/index.html)

---

### Post by mprince on 2009-11-16
-

---

### Post by tunznath on 2009-11-19
I have a problem, I cannot get to home documents home music or any harddrives would deleting
~/.gconf/apps/nautilus
help and if so what can i type into a terminal to delete it seeing as i cannot access home at all
I can access it from windows tho, should i delete it in windows?????

---

### Post by slumbergod on 2009-11-19
I'd recommend Thunar too. I think it is excellent and very fast.

---

### Post by tunznath on 2009-11-19
i get this output typing nautilus into terminal
(nautilus:1958): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-dropbox 0.6.1
Initializing nautilus-gdu extension

** (nautilus:1958): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1958): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1958): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentation fault (core dumped)


BTW how do I install Thunar, and wuill that fix it?????

---

### Post by tunznath on 2009-11-19
Muito Obrigado Slumbergod, i can now access things with thunar , deleted the .gconf apps nautilusthing and nautilus still doesnt work, but at least I can get to things - karmic not great for me should have stuck with hardy

Thanks plenty tho
Regards
from the Açores

---

