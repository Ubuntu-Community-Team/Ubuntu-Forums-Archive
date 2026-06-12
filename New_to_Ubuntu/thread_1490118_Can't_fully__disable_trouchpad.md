---
title: "Can't fully  disable trouchpad"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by Newbie2910 on 2010-05-21
I have a Dell laptop.  I want to fully disable the touchpad. In System/Preferences/Mouse I have turned off everything, but it still moves the cursor around.  This is very annoying when trying to type.

Is there something else I need to do to remove this from the system?

---

### Post by seenthelite on 2010-05-21
You could try Pointing Devices or Touchpad they are in Ubuntu Software Centre.

---

### Post by mixmastamyk on 2010-05-22
Hi, try this: 

[http://ubuntuforums.org/showthread.php?t=11299](http://ubuntuforums.org/showthread.php?t=11299)

---

### Post by Newbie2910 on 2010-05-22
Well, that leads me to this instruction:

Edit /etc/X11/XF86Config-4, and in the Synaptics section, add 'Option  "TouchpadOff" "1"'.

I can drill down to X11 but there is no XF86.... etc.

---

