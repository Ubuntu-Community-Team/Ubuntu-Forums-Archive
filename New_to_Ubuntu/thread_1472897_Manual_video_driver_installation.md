---
title: "Manual video driver installation"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by makuab on 2010-05-04
i got the nvidia drivers for my card (gtx 260)
and i kill the x server or w/e (control alt backspace)
the screen goes black and it takes me back to the login screen
i've logged in as xterm, failsafe, and gnome, but it still says the x server is running
I dont know what to do :(

---

### Post by cariboo on 2010-05-04
Why not use the driver available when going to System->Administration->Hardware Drivers?

There still seems to be some problems installing the driver directly available from Nvidia. If you want to install it, press Ctrl-Alt-F1, once at the console, you have to stop gdm, to do so type at the prompt:

```
sudo service gdm stop
```

you should then be able to install the driver, there are no guarantee that the driver will work.

---

