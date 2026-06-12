---
title: "Re: Network manager can't edit wired settings"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by Spider65 on 2010-03-22
I have the same problem with 9.10 Desktop GNOME.
I want to change my interface to static IP, but when i go into Network Manager and i select my Eth0 interfce, the "Edit" button remain disabled and i cannot change the configuration.

---

### Post by Iowan on 2010-03-23
You're probably doing it right - but what do you mean by: > select my Eth0 interfce  On my Karmic machine, if I right-click the NM icon and select "Edit Connections...", I'm taken to a screen with (my only option): Auto eth0 (last used - never). If I click on Auto eth0 , the Edit and Delete options become ungrayed.

Yours is working differently?

---

### Post by Spider65 on 2010-03-24
Yes, i mean exactly the same, but in my case, the Edit and Delete options doesn't become ungrayed.

---

### Post by Spider65 on 2010-03-26
I have done some other tests and if i run Network Manager from a shell with "sudo", all works well. Only if i run the NetworkManager from NM icon on the top i cannot change the connection  settings.

---

