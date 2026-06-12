---
title: "Switched from Gnome to KDE now locks up at startup"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by Ububtubobl on 2010-06-07
I changed the log in screen to KDE from Gnome to try it but now the system locks up. Could some one please explain how I can change back to Gnome.
Thanks

---

### Post by Ububtubobl on 2010-06-07
I rebooted with a Live usb and entered the following command in Terminal to restart Gnome

"sudo/etc/init/gdm restart - restart GNOME" (I found this command in an article at the debian admin site .)

response from Terminal was " no such file or directory"

Any suggestions for restarting Gnome would be appreciated.

---

### Post by Mariane on 2010-06-07
On your login screen you have a menu with options, there you can set it to go to kde or gnome or xfsce (or whatever it's called) provided they are installed. 

The "default" option is to login into the last session you used, so if the last time you tried to login to kde it will keep trying kde. 

So on the user login screen you tick menu > session > Gnome.

Mariane

---

### Post by Ububtubobl on 2010-06-07
Thank you Mariane, for your response. My Logon screen had no options (probably KDE not really installed, hence the hang up.) However I held down the shift button at startup and there was an opportunity to switch to Gnome at the bottom of the screen. I then went to administration , "logon screen" and fixed what I had changed. 
Thanks again for your reply.

---

### Post by Mariane on 2010-06-07
Good it works now :). 

If you want to have another go at KDE without  losing Gnome you can install it from within gnome:

sudo apt-get install kdebase

The only problem is the display manager, you have to choose either gdm or kdm, you cannot have both. But Gnome runs on kde and maybe kde runs on gdm. 

I try to always have several, so if one fails I can always use another one. At least during the time it takes me to go online and find out how to troubleshoot the one which went wrong. 

Mariane

---

