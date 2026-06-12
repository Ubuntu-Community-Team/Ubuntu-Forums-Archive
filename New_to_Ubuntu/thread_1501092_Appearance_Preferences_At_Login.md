---
title: "Appearance Preferences At Login"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by nevercroft on 2010-06-03
For some reason whenever I log out, the "Appearance Preference" window comes up. This started happening after I was following some tutorial about how to change the login screen and I copied/pasted a line of code into a terminal. I have since lost that page (which probably has the solution im looking for) but if any of you could help disable this that would be great!

EDIT: Alright I went through my terminal recent commands and found the command that started this. 

So now I'm just trying to reverse this command:

> gksudo -u gdm dbus-launch gnome-appearance-properties

Anyone?

---

### Post by nevercroft on 2010-06-03
bump

Anyone?

---

### Post by elliotn on 2010-06-03
What i noticed is that when u log off or restart ur pc with windows open then when u log on the windows will still be open. But that option u enable it somewhere.

---

### Post by qwerty2009 on 2010-06-03
it happened to me ages ago... what fixed it for me was to open assistive technology's window > keyboard accessibility > accessibility > then untick the first box and restart

---

### Post by nevercroft on 2010-06-03
Thanks for the reply, but I'm having a hard time figuring out what your are telling me to do. What option am I supposed to enable?

---

### Post by nevercroft on 2010-06-03
Thanks qwerty, Ill reboot and see if that works.

---

### Post by nevercroft on 2010-06-03
No luck guys, the window still pops up at login.

---

### Post by qwerty2009 on 2010-06-03
Have you checked if its in your startup applications?

check for anything regarding gnome-appearance-properties
system >preferences >startup applications

also on the options tab in startup applications make sure the " Automatically remember... " option is unticked

---

### Post by nevercroft on 2010-06-03
Nope, it's not in there. I also checked that box. Still nothing.

---

### Post by rimin31 on 2010-08-10
just paste this command in terminal:


sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

---

### Post by OxentroT on 2011-09-30
AH! YES! Recognized the similarities between the command which allowed me to make the edit in the first place. Just forgot at the time to recall the link!  :lolflag:

---

### Post by oldos2er on 2011-09-30
Closed, necromancy.

---

