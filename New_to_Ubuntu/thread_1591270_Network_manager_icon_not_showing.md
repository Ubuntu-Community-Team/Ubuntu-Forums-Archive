---
title: "Network manager icon not showing"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by jodonald on 2010-10-09
Hey all, newbie here.  Sometimes (about 25% of the time) when i start ubuntu, the network manager icon doesn't appear in the panel so i can't connect to the internet.  How can i make the icon appear if it doesn't appear during start up?

---

### Post by 0N3 on 2010-10-09
Have you got the Notification area added to the panel? Click an empty space on your panel and select add to panel look for Notification area and add it.

---

### Post by jodonald on 2010-10-09
I have the notification area but if i click 'add to panel', the network manager isn't one of the icons i can add.  Is there a way i can start it by using terminal?

---

### Post by 0N3 on 2010-10-09
nm-applet

---

### Post by 0N3 on 2010-10-09
Check to see if its in your startup programs
System > Preferences > Startup Applications

---

### Post by owners4life5 on 2010-10-09
are you performing user switching?

eg;
does more than one person (besides you, of course), have an account on the computer?

---

### Post by andrewthomas on 2010-10-09
If your panel config is corrupted

```
rm -r ~/.gconf/apps/panel
```

will restore your panel to the default.  

You either have to logout and back in or kill the panel for the changes to be applied

---

### Post by jodonald on 2010-10-09
It's only me using my computer.  I'll have to wait and see if it doesn't show up on the next few startups but i think going into startup applications should help.  Typing nm-applet only gives a warning message but that might be because it's running now.  Thanks for the help!

---

### Post by owners4life5 on 2010-10-09
no problem (:  ...i just remember having this problem with the desktop my brother and i share.

instead of "switch user" we found out that logging out would prevent this problem from occuring, rather than "fast switching"...for some reason it was causing this error.

you can always connect through the terminal, though, if it is something really important. i.ll give you instructions on that if you would like me to.

---

### Post by jodonald on 2010-10-11
> **0N3 said:**
> nm-applet

If i start this in terminal, is there a way to keep it running even after i close the terminal?

---

### Post by cavh on 2010-10-11
Yes, the following command will keep nm-applet running even if you close the terminal:

```
nohup nm-applet &
```

---

