---
title: "Retaining NVidia settings on bootup &amp; renaming primary user"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by H.Callahan on 2010-10-14
Ok, I have a couple of questions that have been bugging me for a while.  Since I just upgraded to 10.10, I thought I would see if I can get some answers.

I have a box that has an NVidia card in it.  I use the "NVIDIA X Server Settings" utility to set resolutions.  I have a monitor that is capable of 1280x1024.  Setting the resolution in the NVidia utility successfully switch the display to 1280x1024.  In the utility, there is an option to save the settings to the xorg.conf file (which I have done -- many times!!!).  However when I reboot, the display goes back to 1024x768.  While it is an easy switch after the boot, I would like to get Ubuntu to boot into the 1280x1024 resolution.  What am I missing?

Secondly, when I set up this machine, I absentmindedly (read: stupidly) took Ubuntu's default recommendation for user name.  I would like to change the name of the primary user to something else, but I can not see where to do that.  I know I can create a second user, but I don't really want to do that, I'd rather just rename the current one.  How?

---

### Post by robsoles on 2010-10-18
To make persistent changes to display properties
```
gksudo nvidia-settings
```
will prompt for your password and then open the "NVIDIA X Server Settings' utility as root, when you click 'save changes' it can actually overwrite the /etc/X11/xorg.conf file successfully and settings should persist through restarts.



[http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/](http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/) seems comprehensive enough although they don't mention that **it is surely best to do it while the user being modified is logged out** - before logging in as the changed user be sure to check that the user's home folder has been renamed to the new username you chose - post back to this thread if it doesn't change your username or something about it bombs on you.

---

### Post by H.Callahan on 2010-10-19
> **robsoles said:**
> To make persistent changes to display properties
```
gksudo nvidia-settings
```
will prompt for your password and then open the "NVIDIA X Server Settings' utility as root, when you click 'save changes' it can actually overwrite the /etc/X11/xorg.conf file successfully and settings should persist through restarts.

I've already done that and it doesn't take.  I've actually looked at xorg.conf and the changes actually appear to be in the file.  It just will not invoke on boot-up.

> **robsoles said:**
> [http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/](http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/) seems comprehensive enough although they don't mention that **it is surely best to do it while the user being modified is logged out** - before logging in as the changed user be sure to check that the user's home folder has been renamed to the new username you chose - post back to this thread if it doesn't change your username or something about it bombs on you.
I don't understand, then, how I can rename a user if I only have one user on the system.  Can I use root to do that?

---

### Post by cariboo on 2010-10-19
Check the screens section of xorg.conf, om ,y system it looks like this:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
```

Make sure you have the same metamodes option set. With the above setting all users on my system have the same resolution.

---

### Post by JamButty on 2010-10-19
I had this problem after every new kernel update. [This solved it. ]("http://phun-ky.net/2008/10/fix-for-failed-to-load-the-nvidia-kernel-module-on-ubuntu")
Adapt as needed for your situation.

---

### Post by robsoles on 2010-10-19
> **H.Callahan said:**
> ...

I don't understand, then, how I can rename a user if I only have one user on the system.  Can I use root to do that?

If you break a security rule, assign root a password and then log in directly as root without logging in as your main user then you could but to be flat out honest I wouldn't assign root a password these days - I'd make a new user, give them sudo/admin privs and then use them to change 'me', then I'd delete the new user if I couldn't stand leaving it around.

---

