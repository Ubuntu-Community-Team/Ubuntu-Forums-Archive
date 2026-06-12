---
title: "Suddenly no sound"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by @rizz on 2010-06-26
Hi,

  The sound as disappeared from my laptop. There is not sound applet in the panel

  there is no volume control in system preference.

 When i go to my movie player the volume icon is grayed out.

 Now i run 9.10 and have been doing so with out a problem

This has happened recently

is there anything that can be done (tried deleting the .pule dir, did not help) 

plz help:confused:

---

### Post by Evanescence on 2010-06-26
Am not sure if this will work: I think (I could be wrong) that your sound card is not being seen for some reason. It could be due to a resent upgrade that required additional sound drivers (proprietary ones, that is). You can confirm if there are any drivers available through: System>Administration>Hardware Drivers. 

As for the sound applet icon on the panel, just right-click on it and click on 'add to panel...' then see if there's an option to add for sound and volume control.

Still, you can try to reconfigure your desktop by hitting ALT+CTRL+F1 
then enter the requested details and run:

sudo dpkg-reconfigure gnome-desktop

then exit with: ALT+CTRL+F7

then reboot. Hope it works for you!

---

### Post by @rizz on 2010-06-26
hey dude thanks it works now!!!):P

---

