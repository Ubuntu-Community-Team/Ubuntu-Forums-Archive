---
title: "I'm stuck in the F1 console. ctrl-alt-F7 isn't working."
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Arazu on 2011-03-06
I'm sure it's graphics related but I'm not sure how to fix it. Ctrl-alt-F7 hangs on "checking battery". Rebooting brings me back to the console. Sudo /etc/init.d/gdm start and sudo service gdm start both indicate it's running.

I don't know what to do.

---

### Post by kimberlite on 2011-03-06
Try sudo /etc/init.d/gdm restart instead of sudo /etc/init.d/gdm start. Just a guess...

---

### Post by cprofitt on 2011-03-06
Is this immediately after an install or update?

---

### Post by Arazu on 2011-03-06
I tried restart as well.

I was trying to install Nvidia's drivers. I went into the console, stopped gdm, ran Nvidia's script which failed, and now I can't get back to a GUI.


I have some other problems as well. I'm just going to reinstall.

---

### Post by khelben1979 on 2011-03-06
You can always try with starting up the graphics on a second X server display by typing:

```
startx -- :2
```

And if that fails, you can report back what graphics card/chipset you got so we have a chance to see something from that: ```
lspci | grep VGA
``` to analyze if it's a driver issue and what can be done from that.

---

