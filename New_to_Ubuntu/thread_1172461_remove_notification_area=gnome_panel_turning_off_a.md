---
title: "remove notification area=gnome panel turning off and on non stop"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by klemperal on 2009-05-28
I removed the notification area from the gnome panel and now its turning off and on non stop about every second.  I would try to put the notification area back to see if it fixed things, but since the panel is there one second and gone the next this isn't possible.  This is a pretty big bug/problem--please let me know if you know a fix.  I'm going crazy with the panel blinking off and on.

Thanks in advance

ps--I'm using jaunty

---

### Post by ptn107 on 2009-05-28
Right-click the panel and select properties.  You sure you don't have 'Autohide' checked?

---

### Post by celticbhoy on 2009-05-28
You might try logging out then back in again.

---

### Post by klemperal on 2009-05-28
right clicking the panel doesn't work because the whole thing keeps cutting off then on.  Logging off then coming doesn't make a difference either.  any other ideas?

---

### Post by Elfy on 2009-05-28
Do you have show desktop turned off in gconf-editor? There was a bug in jaunty during development - [https://bugs.launchpad.net/ubuntu/jaunty/+source/nautilus/+bug/325973](https://bugs.launchpad.net/ubuntu/jaunty/+source/nautilus/+bug/325973)

---

### Post by klemperal on 2009-05-28
I unchecked the box, restarted x, and the problem persists. Any other ideas?

---

### Post by Elfy on 2009-05-28
No - the bug was there if show desktop was turned off - turning it on again allowed me to restore the notification area.

---

### Post by klemperal on 2009-05-28
I got tired of looking at the panel turning on and off, and interrupting my typing so I completely removed gnome-panel, fast-user-switch-applet, gnome-applets, gnome-applets-data, indicator-applet, indicator-message.  Durring the uninstall process I got this error
```
The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet".
Do you want to delete the applet from your configuration?
```
I deleted the entry, and the panel stopped blinking--I assume that the next time I log in it will be gone all together.  Still, this is only a temporary solution--I do want to use gnome panel.  Please let me know if you have any ideas on how I can get things working again.

---

### Post by klemperal on 2009-05-28
> **forestpixie said:**
> No - the bug was there if show desktop was turned off - turning it on again allowed me to restore the notification area.

I turned it back on and it didn't make a difference.  In case it wasn't clear from my original post, its not just a matter of the notification area turning off an on--its the entire panel turning off and on once I removed the notification area.

---

### Post by Elfy on 2009-05-28
> **klemperal said:**
> I turned it back on and it didn't make a difference.  In case it wasn't clear from my original post, its not just a matter of the notification area turning off an on--its the entire panel turning off and on once I removed the notification area.

Sorry can't be of more help - but I know exactly what you mean it drove me nuts ... 

Looking at my old jaunty bash history I believe that I rest the gnome panles to default.

[http://ubuntuforums.org/showpost.php?p=7049593&postcount=3](http://ubuntuforums.org/showpost.php?p=7049593&postcount=3)

Try that to reset to default - if you can't get to a terminal - Ctrl+Alt+F1 run the commands - Ctrl+Alt+F7 to get back to gnome and logout


Edit - possibly also I appeared to have used ```
gconftool-2 --recursive-unset /apps/panel
``` at about the same time, but can;t be completely sure

---

### Post by klemperal on 2009-05-28
Thanks a bunch forestpixie.  Following the commands you posted I got the panel back.  Seems like the notification system in general is a complete mess in jaunty.

Thanks again

---

### Post by Elfy on 2009-05-28
Glad I could help - in the end.

Perversely I actually like the new notifications - just wish that Amarok could use them

---

