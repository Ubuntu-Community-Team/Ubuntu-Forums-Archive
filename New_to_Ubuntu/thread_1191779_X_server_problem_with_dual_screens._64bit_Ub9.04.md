---
title: "X server problem with dual screens. 64bit Ub9.04"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by wetinwales on 2009-06-19
I cannot get NVIDIA X server settings to 'save to X configuration file' when setting up with NVIDIA driver. Perhaps this is why the screens have to be re-set up in NVIDIA each time I boot.

Error message was "...cannot create a backup file in xorg (xorg.conf.backup) 

So in my madness I created an empty one... '/etc/X11/xorg.conf.backup' hoping it might be found.
Didn't work so...

the error message I now get when I try to save the X server configuration is "..unable to remove old 'xorg.conf.backup'..."

History:- Using 9.04 on an AMD-A8N with Nvidia 7800 GTX (180) Twin LCD screens.
Installation of 9.04 with twin screens went very well using the 'twinscreen' option. All works well.

I then tried the 'separate x screen (requires restart)' option...just because I'm inquisitive... I used the 'save x server configuration' tab. 
That's when it went belly up.
Getting twin screens and resolution back to working was fraught and now will not save its settings.

Any help appreciated.

---

### Post by Ocxic on 2009-06-19
run "gksu nvidia-settings" from the terminal or edit the menu entry an put gksu in from the the command. this will give you root access. 
if necessary you can manually remove the backup files it is complaning about from /etc/X11.

you may also need to do this "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf"  then "sudo touch /etc/X11/xorg.conf" before you save the config file.

---

### Post by wetinwales on 2009-06-19
Ocxic .. thank you very much. I think I understand that gksu puts me in as root.. which means that it was a 'permission' issue all along.
The only trouble with Linux (Ubuntu) is permissions.
I have not yet found a well written article which explains what how if when ... then makes the coffee.

Thanks again. Twin screens rock!:D!

---

