---
title: "Need help with Launching perl scripts"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by nvalese on 2009-04-14
Hi.  I am new to Ubuntu, and am pulling my hair out after spending a week with configuring a touchscreen driver on my Fujitsu P Series Lifebook P1510d.  So far, i got the touchscreen working and I can rotate the screen using the following terminal command:

sudo perl /opt/touchscreen/rotate.sh 90

The rotate.sh script kills the touchscreen driver, rotates the screen, and then reinitializes the touchscreen driver again.  If I don't use the 'sudo' command, the touchscreen process doesnt kill and the touchscreen gets all buggy.

So, now to my question:

I would like to create a launcher on my panel to run this command:

sudo perl /opt/touchscreen/rotate.sh 90

Is it possible?  Am I going about this the wrong way? 

If anyone knows a better way to rotate the screen using my model laptop, please let me know.

Thanks,
Nick

---

### Post by Temposs on 2009-04-14
1) right click on a panel
2) click "Add to Panel"
3) select "Custom Application Launcher"
4) click "Add"
5) Fill in the information. You can choose an appropriate icon by clicking the icon.
6) click OK

You should have an icon on your panel that does what you want now.

---

### Post by nvalese on 2009-04-14
I have tried that already, but because the command needs SUDO privileges, it doesn't work.  Any other ideas?

Has anyone tried to launch a command that requires SUDO privileges?

---

### Post by achase79 on 2009-04-14
use gksu instead of sudo for launchers

---

### Post by nvalese on 2009-04-14
Thanks for the help!!!  It works now.

---

