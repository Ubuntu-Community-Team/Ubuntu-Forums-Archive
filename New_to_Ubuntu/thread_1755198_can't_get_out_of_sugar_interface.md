---
title: "can't get out of sugar interface"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by agdesilva on 2011-05-10
I recently upgraded from 10.10 to 11.04.  I can't remember exactly what I did but I was looking at the login system settings I think; experimenting with logging directly into one user with and without the password.  I think there was an option giving me the option for Sugar (it was currently at Ubuntu).  I selected it, rebooted, and I was then in Sugar.  But how do I get *out* of Sugar and return back to my regular 1104 stock interface?  It would appear this mode has very few options.

Ajit

---

### Post by jerome1232 on 2011-05-10
if you can open a terminal and type the following command it should get you the dialogue to change your login preferences (like auto login)
```
gksu gdmlogin
```

---

### Post by agdesilva on 2011-05-11
it starts up right into Sugar; there must be a way IN sugar to get out but I can't figure it out.  I can get to a text prompt via cntrl alt f1 but if i type gksu gdmlogin i get the message (gksu:1905) Ttk-WARNING cannot pen display:

---

### Post by agdesilva on 2011-05-11
I have attempted to use gdmlogin and gdmsetup but i can't get display.  Is there a way to adjust the login settings at the command prompt?  I can get to the command line from Sugar by typing  Cntl Al F1.

---

### Post by jerome1232 on 2011-05-11
I would suggest perusing their site to find a how to, I have zero experience with it.

[http://en.flossmanuals.net/sugar/](http://en.flossmanuals.net/sugar/)

---

### Post by agdesilva on 2011-05-11
Thank you.  I think my mistake was removing passwords and directly logging into my user account.  I think I am really stuck; the Sugar interface is cute and I suppose worth exploring because I have kids but it is not really designed to operate the computer.  If I cannot adjust the settings in some text file I will be reinstall the OS.

---

### Post by jerome1232 on 2011-05-11
I'm sure you can change a setting in gconf, no reinstall required, let me give it a bit of googling.

---

### Post by jerome1232 on 2011-05-11
From this rather old thread
[http://ubuntuforums.org/showthread.php?t=1023326](http://ubuntuforums.org/showthread.php?t=1023326)


There may be a file at /etc/gdm/custom.conf

Try editing it from a cli with nano, change the autologin option to false or possibly post the contents of the file if your confused.

---

### Post by el_koraco on 2011-05-11
> **agdesilva said:**
> Thank you.  I think my mistake was removing passwords and directly logging into my user account.  I think I am really stuck; the Sugar interface is cute and I suppose worth exploring because I have kids but it is not really designed to operate the computer.  If I cannot adjust the settings in some text file I will be reinstall the OS.

```
sudo nano /etc/gdm/custom.conf
```you'll see sth like this: 


> [daemon]
AutomaticLoginEnable=true
AutomaticLogin=username
TimedLoginEnable=false
TimedLogin=username
TimedLoginDelay=1
DefaultSession=sugarEither change AutomaticLoginEnable to false, or DefaultSession to gnome.

CRTL + O (the letter) to save, CTRL +x to exit. sudo reboot to reboot. No need to reinstall :D

---

### Post by agdesilva on 2011-05-11
THank you el koraco and jerome.  That worked.

Ajit

---

### Post by agdesilva on 2011-05-11
Jerome:  I will also read this back thread carefully.  Again, thank you for your help.  ajit

---

