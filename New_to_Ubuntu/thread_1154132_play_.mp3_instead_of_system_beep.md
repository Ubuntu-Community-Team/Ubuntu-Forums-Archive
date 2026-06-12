---
title: "play .mp3 instead of system beep?"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Odd_sam on 2009-05-09
How can I replace the system beep with an mp3 file so whenever the system beep is normally triggered the mp3 file is played. Is there an app already out there to simplify this process or is this not typically done or not possible. Also I'm running gnome 2.26.1 incase that's important.

---

### Post by ashmew2 on 2009-05-10
Hi , 

I dont really know if this is going to be the best solution for your problem , but Just make a script and add it to the run at startup ? But that's for the login sounds..

Have a look here : [http://ubuntuforums.org/showthread.php?t=634295](http://ubuntuforums.org/showthread.php?t=634295)

---

### Post by uncannybuzzard on 2009-05-10
that probably would be quite tricky since the system beep is a module. not sure how you would replace it. if you just want to kill it add this to /etc/modprobe.d/blacklist
```

#stupid system beep
blacklist pcspkr
```

---

