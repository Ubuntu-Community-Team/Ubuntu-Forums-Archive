---
title: "Permanant fix for sound?"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by mikethebike on 2009-09-06
After upgrading to Jaunty I have had sound problems. The intro sounds work but then nothing else. I have fixed the problem using 
pulseaudio -k ; start-pulseaudio-x11
but this needs to be redone each time I start my machine. I have tryed every fix that I have found so far but to no avail. Does anyone know how to permanently fix this bug?

---

### Post by Petertje on 2009-09-06
I don't know how to permanently fix it but you can do this to get the sound fixed at every boot.

```

sudo nano /etc/rc.local

```
and add this line to bottom
```

pulseaudio -k ; start-pulseaudio-x11

```
Save and done, now it will be executed on each boot. As for a permanent fix, have you checked your sound drivers and pulseaudio bug report?

---

### Post by mikethebike on 2009-09-06
Brilliant thanks, that will do for now.

---

### Post by mikethebike on 2009-09-06
Actually that doesn't work mate. Thanks anyway.

---

### Post by Bodsda on 2009-09-06
> **mikethebike said:**
> After upgrading to Jaunty I have had sound problems. The intro sounds work but then nothing else. I have fixed the problem using 
pulseaudio -k ; start-pulseaudio-x11
but this needs to be redone each time I start my machine. I have tryed every fix that I have found so far but to no avail. Does anyone know how to permanently fix this bug?

Have you tried looking into this [guide]("http://ubuntuforums.org/showthread.php?t=789578")? 

If that command works then whack it in a bash script and place it in your sessions dialog from the menu's to get it to run that command whenever you log in.

Hope this helps,
Kind regards,
Bodsda

---

### Post by mikethebike on 2009-09-06
FIXED... (actually not fixed but worked around)
I added the command:-

pulseaudio -k ; start-pulseaudio-x11

as a start up application in

System/ Preferences/ Start up applications

The sound now starts muted but at least it starts.

---

