---
title: "Envelope Icon in Panel: What is it and how do I remove it?"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by hanzj on 2010-05-28
Envelope Icon in Panel: What is it and how do I remove it?

---

### Post by hryanjones on 2010-05-28
I believe that's part of your indicator applet and it can connect to different online communications (e.g. email by way of Evolution, instant messaging by way of Pidgin, etc).  You can remove it by right clicking, but then it'll take away your other useful indicators like sound, battery, etc.  Let me see if I can figure out how to remove it with a gconf editor....

---

### Post by hanzj on 2010-05-28
i don't use evolution. i don't use instant messaging. i see no need for the icon. i want it removed without removing any other icon.

---

### Post by jerenept on 2010-05-28
It will remove the icons for : Transmission Bittorrent Client, and maybe other useful stuff. Why do you want to remove it?

---

### Post by lsk3993 on 2010-05-28
> **hanzj said:**
> i don't use evolution. i don't use instant messaging. i see no need for the icon. i want it removed without removing any other icon.
Just right click it and select 'Remove From Panel'

---

### Post by lsk3993 on 2010-05-28
> **jerenept said:**
> It will remove the icons for : Transmission Bittorrent Client, and maybe other useful stuff. Why do you want to remove it?
Well it won't remove them... they can still be accessed from the applications menu

---

### Post by hanzj on 2010-05-28
lsk,
read jerenept's message carefully.

jerenpt says that what will be removed is the trannsmission icon. He did not make any mention of the removal of the program.
but your reply  makes a disagreement where jerenept is silent.

---

### Post by lsk3993 on 2010-05-28
> **hanzj said:**
> lsk,
read jerenept's message carefully.

jerenpt says that what will be removed is the trannsmission icon. He did not make any mention of the removal of the program.
but your reply  makes a disagreement where jerenept is silent.
Yeah fair point.
Well anyway, problem solved now?

---

### Post by hanzj on 2010-05-28
how can one get the icon back after removing it?

---

### Post by lsk3993 on 2010-05-28
> **hanzj said:**
> how can one get the icon back after removing it?
I only know how to restore _all_ the default icons. You can do this with:
> gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panelBut if this is the only icon you've removed then this does the same thing effectively...

---

### Post by Zemblan on 2010-05-28
Right click on the panel, choose "add to panel", choose indicator applet from the list. That will add back the 'envelope' and the others too.

---

### Post by hanzj on 2010-05-28
i want to remove the envelope icon without removing the other icons (e.g., volume) in the indicator-icon applet . How?

---

### Post by Zemblan on 2010-05-28
```
sudo apt-get remove indicator-messages
```

I believe that will remove the 'envelope' and leave the rest intact. Log out and then back in again after running that command

---

### Post by kerry_s on 2010-05-28
> **Zemblan said:**
> ```
sudo apt-get remove indicator-messages
```

I believe that will remove the 'envelope' and leave the rest intact. Log out and then back in again after running that command

you should take out "evolution-indicator" & "indicator-applications" to.

---

### Post by hanzj on 2010-05-28
sudo apt-get install indicator-evolution
> 
E: Couldn't find package indicator-evolution


---

### Post by kerry_s on 2010-05-28
> **hanzj said:**
> sudo apt-get install indicator-evolution

not install, remove. looks like i had it backwards "evolution-indicator"

once you removed should look like this:

---

### Post by Jakiejake on 2010-05-28
It's For The Evolution Mail Program
If you want to remove it remove Evolution and restart
How to remove evolution

Go into The package manager and search for evolution and mark for removal

---

### Post by hanzj on 2010-05-30
> sudo apt-get remove evolution-indicator

Package evolution-indicator is not installed, so not removed

But the envelope icon is still there.

---

### Post by kerry_s on 2010-05-30
just remove the indicator-applet from the panel, then press alt+f2
type-> **gnome-volume-control-applet**
& run, that will give you the old 1 back. 
you need to put that in the startup programs if you want it loaded all the time.

---

### Post by Dumpy Dumpster on 2010-05-30
Thanks kerry_s
Just what is needed and works a treat.

---

### Post by kerry_s on 2010-05-30
> **Dumpy Dumpster said:**
> Thanks kerry_s
Just what is needed and works a treat.

your welcome, i went a different way myself. i'm using a drawer with the auto close turned off, i prefer the button style so i have launchers, i just click away.
i guess i prefer to choose how volume is done.

---

### Post by hanzj on 2010-05-30
Without the indicator applet, what else would be potentially removed. Don't you and I want notifications indicators?

---

### Post by kerry_s on 2010-05-31
> **hanzj said:**
> Without the indicator applet, what else would be potentially removed. Don't you and I want notifications indicators?

not many things work with the indicator app, as long as you turn on the notification icon, you'll get the old behavior of notifications.
example: transmission, in preferences you have to select "show transmission icon in notification area".

---

