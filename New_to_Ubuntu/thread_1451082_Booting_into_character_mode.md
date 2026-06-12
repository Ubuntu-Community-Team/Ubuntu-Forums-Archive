---
title: "Booting into character mode"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by Don Bowen on 2010-04-10
My notebook computer frequently boots into character mode.  Makes me nostalgic for the TRS-80 and CPM, but it's also annoying.
   I have to reboot several times: sometimes cleanly..by pushing the power button and letting it shut down normally, or holding the power button down for 6 seconds and forcing a brutal shut down.  After about 3 iterations, it will come up in graphic mode and all is well.  
   any way to make it consistent?

---

### Post by Jive Turkey on 2010-04-10
You need to investigate the causative failiure.  Next time you end up in text mode, hit ctrl+alt+F8.  That should show you some of the messages from the boot process.  If you don't see anything there, check the logs for error messages.

Maybe try, ```
cat /var/log/messages | grep error
``` There might be a more appropriate log to check I don't know.

Another thing to try after logging in in text mode (instead of rebooting) would be ```
sudo /etc/init.d/gdm start && startx
``` that latter command should start gdm and xorg, or at least offer some helpful failiure messages.

I'm thinking it could be a hardware problem.

---

### Post by Don Bowen on 2010-04-11
it doesn't show any error messages when I press that combination, but the boot process is random as ever.
May just be a quirk of this machine....

---

