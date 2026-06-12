---
title: "Jaunty Notification Query"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-05-11
So, the new jaunty notification is useful, but is it possible to interact with the notification?

Currently while running liferea or pidgin new updates are displayed on the top right corner. When I scroll over it with my mouse it becomes translucent, becoming visible once I move my mouse away. It then dissapears.

Is there anyway to click on the notification?

So, with liferea if I click on it, the feed would open, and with pidgin a conversation would open.

Is this possible?

---

### Post by Didius Falco on 2009-05-11
Hi,

No, the notifications are intentionally designed to be non-interactive. They just show you some information, then fade away.

Regards,

Didius

---

### Post by Dill on 2009-05-11
Perhaps the pidgin-libnotify plugin could be what you're looking for?

[http://gaim-libnotify.sourceforge.net/](http://gaim-libnotify.sourceforge.net/)

From the page: *This plugin adds a libnotify interface to pidgin, enabling popups much like guifications. It has some configuration options, to show popups when a buddy signs on, on new messages and on new conversations only.*

And it looks like it will allow you to initiate actions when these messages popup, such as starting a chat or viewing messages.

I don't use pidgin myself, so perhaps others could speak to the notification system better.

Cheers,
Dill

---

### Post by Didius Falco on 2009-05-12
If you have a look through Pidgin's configuration, you should be able to set Pidgin up to open chat windows when people log in, etc.

The Notification window is simply a messenger - you want the weather (Pidgin), not the weatherman (Notification).  ;)

Regards,

Didius

---

