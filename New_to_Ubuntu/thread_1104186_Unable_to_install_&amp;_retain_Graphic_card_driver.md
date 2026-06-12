---
title: "Unable to install &amp; retain Graphic card drivers in USB bootable Ubuntu"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by SandyM on 2009-03-23
I have been using Ubuntu 8.10 and recently came to know about USB bootable persistent drive where any alteration during a live session is stored and we get the same altered desktop in the next live session.

The concept is excellent but I am facing graphic cards driver problem.

While each and every setting seem to retain for the next session but graphic driver are unable to load. Moreoverer in **Ubuntu 8.10** Drivers were not even installing (neither automatic nor manual) but in new ***9.04 alpha 6*** they install but the next time I boot I am again asked for the drivers which  can only be manually installed as automatic route fails.

Please help so that ubuntu don't forget my NVIDIA settigs or ask for drivers to enable desktop effects every time I boot to live session.

I am using NVIDIA 880GT.

PLEASE HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Gresley on 2009-04-08
Having exactly the same problem. I'm using Intrepid on a USB stick so I can boot my work laptop into linux to do personal stuff. The persistent idea works fine (I even have virtualbox installed on the USB).

I have tried to use some advanced graphics, and this is where things go wrong. Changing the appearance, using the visual effects tab causes intrepid to try to install drivers. Once these are downloaded the system needs a restart. Following the restart the drivers dont load. In the hardware drivers menu option the driver is shown as inactve. Trying to activate again results in a request to reboot. 

Moreover, things that previously worked, such as AWN no longer function, with an error message screen not composited.

I cant work out a) how to get the proprietary graphics driver to load, or b) how to get back to the position i had originally from the standard drivers in the distro, where at last comiz was working and awn was running.

Any idears?.

---

### Post by Gresley on 2009-04-17
Have now solved this by doing a full install to the USB rather than a live session. Works like magic!

---

### Post by alanh on 2009-04-27
I'm having the same problem.   How did you carry out the full install?

---

