---
title: "Login loop after being fine for months"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Sponge Cat on 2010-08-26
Hi, I have an Asus EEE PC 900a with Xubuntu 9.10. I believe I installed Xubuntu at the end of 2009. Awhile back I had some problems with a Login Loop, and found out it only occurred when I had certain things like a USB hub or a monitor hooked up when booting. Other than that it has been fine until today. 

This morning when starting up I noticed the login screen had a flat screen monitor logo that isn't normally there (I think the Xubuntu logo is normally there) and instead of waiting a few seconds before letting me enter my password like normal, it let me enter it almost instantly after clicking my name. Then after loging in, it would flash through a few screens, and send me back to the login. 

Thinking it might be for the same reasons as last time, I unhooked everything, and it still happened. I even tried going in the BIOS and disabling the USB controller, still happened. Next I  tried looking up some info as to why it might be happening, and found low disk space might be a reason. (And with a 4GB SSD, pretty likely.) I went into recovery mode and selected clean, and it didn't seem to do anything, and didn't fix the problem. I tried loging in with the terminal, and that worked, but when going back the GUI, I end up back at the login screen. None of the other solutions I can find make any sense to try, as this is not a fresh install, and I haven't done anything to screw with it lately. Any ideas on how to fix this?

---

### Post by jflaker on 2010-08-27
log into a command line and do
```

rm -rf /home/YourUser/.gconf

```
or 
```

mv /home/YourUser/.gconf /home/YourUser/gconf.old

```
Then reboot.  You will be back to out of the box desktop which should solve the loop as it is likely something in your display setup....

---

### Post by Sponge Cat on 2010-08-27
I tried both, and it still isn't working.

Edit: Ok, I found out that the problem was not enough space. It took quite awhile to find stuff I knew was safe to delete, but I guess I'm a bit more used to the terminal now.

---

