---
title: "Resolution problem with LG Flatron W2453SQ monitor"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by nykomling on 2011-09-03
Hi!

I have problem connecting my LG Flatron W2453SQ monitor via VGA to my HP Pavillion dv3500 laptop. There is a picture on the external monitor but the resolution is lower than it can be (I have earlier connected it to the same computer running Windows Vista, and then the resolution was higher).

This is how it look like when I'm checking in the control panel for drivers: (see picture 1) [IMG]http://ubuntuforums.org/attachment.php?attachmentid=201351&stc=1&d=1315061510[/IMG]

Translation: "Denna drivrutin är inte aktiverad" means "This driver is not activated". "Rekommenderad" means "Recomended".

And this is what it look like when I look at the "Monitors" at the Control panel: (se picture 2)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201352&stc=1&d=1315061510[/IMG]

"Okänd" means "Unknown".

I have tried to change the resolution on the external screen via the "NVIDIA X Server Settings", but only the 1152x864 resolution works (see the setting below): (se picture 3)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201353&stc=1&d=1315061510[/IMG]

When I try to change the resolution to 1360x768 (the highest avaible) i get this message: (see picture 4)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201354&stc=1&d=1315061510[/IMG]


My graphics card specs look like this: (see picture 5)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201355&stc=1&d=1315061510[/IMG]

Please help me with this.

Do I need to install some kind of driver, so the monitor will work properly? How do i do that? Is there any other solution to the problem?

I'm using Linux Ubuntu 11.04.

Thank you very much for helping me!

---

### Post by realzippy on 2011-09-03
"driver activated but not in use" is a common bug,ignore it.
Open terminal,run:

```
sudo nvidia-xconfig
```

then post xorg.conf content

```
gedit /etc/X11/xorg.conf
```

---

### Post by nykomling on 2011-09-03
Hi!
Thank you for your quick reply. However, I can't get it work (maybe because I'm totally new to Linux).

So I have run the command as you described:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201367&stc=1&d=1315069071[/IMG]

Then the xorg.conf-file appeared as a textfile. I closed the textfile and restarted the computer. But now the external monitor is deactivated (see picture below).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201368&stc=1&d=1315069071[/IMG]



So what should I do to get the external monitor back, and get the highest possible resolution?

---

### Post by nykomling on 2011-09-03
Hi again, now I did try to set it as "twin view" and it worked! The resolution is very good now! I just hope I'll remember the settings if I have to change them again after restarting the computer next time.

Thanks!

:-)

---

### Post by realzippy on 2011-09-03
You have to hit
"Save to X configuration file" after you made your settings,then it will persist a reboot...
If everything is ok,please set thread as solved (ThreadTools)
Have fun!

---

