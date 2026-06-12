---
title: "Karmic Ubuntu add Empathy to auto-start"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by fleamour on 2009-11-25
I want to run a root shell command to add Empathy to auto start up as per this guide:

[http://demmer.ipax.at/blog/ubuntu-autostart-for-empathy-im-client/]("http://demmer.ipax.at/blog/ubuntu-autostart-for-empathy-im-client/")

But do not know how to access root shell?

---

### Post by ubudog on 2009-11-25
Open a terminal: Applications>Accessories>Terminal and type ```
sudo -s
``` then enter your password (you won't see it being typed for security reasons) and press enter.  You will then be in a root shell.

---

### Post by philinux on 2009-11-25
> **fleamour said:**
> I want to run a root shell command to add Empathy to auto start up as per this guide:

[http://demmer.ipax.at/blog/ubuntu-autostart-for-empathy-im-client/]("http://demmer.ipax.at/blog/ubuntu-autostart-for-empathy-im-client/")

But do not know how to access root shell?

```
sudo cp /usr/share/applications/empathy.desktop /etc/xdg/autostart
```

---

### Post by fleamour on 2009-11-25
Thank you ubudog.  Shoulda known root & super user do are the same.

---

### Post by ubudog on 2009-11-26
> **fleamour said:**
> Thank you ubudog.  Shoulda known root & super user do are the same.

You are welcome. Anytime.

---

