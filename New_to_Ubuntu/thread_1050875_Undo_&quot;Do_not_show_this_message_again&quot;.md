---
title: "Undo &quot;Do not show this message again&quot;"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by AndrooUK on 2009-01-26
Hey everyone,
I recently clicked on the button 'Do not show this message again' by accident on the battery discharging notification.

Is there a way to restore the message, or indeed any message accidentally hidden?

Thanks!

---

### Post by Tim Sharitt on 2009-01-26
Hit Alt-F2 and enter gconf-editor. In the left pane; expand apps, scroll down and expand gnome-power-manager and click on notify. A list of possible notifications will appear in the right pane. 

Clicking on the options will bring up a description in the lower right part of the screen.

---

### Post by AndrooUK on 2009-01-31
Oh brilliant, thanks very much!  Works fine now.  :D

edit: I've tried to mark the thread as solved, but the option is not available to me in the Thread Tools link...

---

