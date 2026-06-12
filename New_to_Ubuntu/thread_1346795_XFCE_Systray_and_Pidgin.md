---
title: "XFCE Systray and Pidgin"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Warpnow on 2009-12-05
So...I can't get pidgin to go to the system tray, I added notification area, which I assume is the tray item...as there is no plugin called system tray or tray or such.

How cna I make Pidgin go to th tray?

---

### Post by m_duck on 2009-12-05
You are right, "Notification Area" is the XFCE system tray. If you right click the notification area and go to properties, there is a list of "hidden applications". My first guess is to ensure that Pidgin is not checked in this list.

My only other thought is within Pidgin. Go to Tools -> Preferences and in the Interface tab, make sure that "Show system tray icon" is set to always.

If neither of those are the case, I've no idea.

HTH

---

### Post by Warpnow on 2009-12-05
> **m_duck said:**
> You are right, "Notification Area" is the XFCE system tray. If you right click the notification area and go to properties, there is a list of "hidden applications". My first guess is to ensure that Pidgin is not checked in this list.

My only other thought is within Pidgin. Go to Tools -> Preferences and in the Interface tab, make sure that "Show system tray icon" is set to always.

If neither of those are the case, I've no idea.

HTH

It was pidgin. Thanks...odd...never had to do that for gnome to put it in the tray.

---

### Post by sdqali on 2010-04-25
Thank You m_duck!
That worked for me..

---

### Post by pletiplot on 2011-12-01
> **Warpnow said:**
> It was pidgin. Thanks...odd...never had to do that for gnome to put it in the tray.
Gnome is tied with pidgin more closely, so pidgin has its own icon outside the sys tray in gnome. So if you had allowed the systray in pidgin, you would have seen two pidgin icons.

---

