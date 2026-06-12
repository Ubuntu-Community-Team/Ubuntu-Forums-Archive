---
title: "Firestarter"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by dhlowe on 2009-07-28
Please let me know how I can ensure that Firestarter loads automatically on start-up. At the moment, I need to open it manually each time.
Thanks.

---

### Post by tacantara on 2009-07-28
By default, the built-in firewall in Ubuntu starts up when you turn your computer on.  However, if you want the Firestarter GUI to open on startup (as I do, just for the extra peace of mind), add the program to the Startup Applications program (System > Preferences > Startup Applications).  Click Add, and fill in the required information.  The command to start the program is "firestarter" (without quotes).  The next time you turn on your computer, you will be prompted for your password.  After you provide the password, the Firestarter GUI will open, and its icon will appear in the system tray.

---

### Post by skyjacker on 2009-07-28
> **dhlowe said:**
> Please let me know how I can ensure that Firestarter loads automatically on start-up. At the moment, I need to open it manually each time.
Thanks. Open terminal and type the following:
```
sudo ufw enable
```

---

### Post by esalnoj on 2009-07-28
Out typed.

Do you want to monitor IP traffic? Or just configure the firewall?

---

### Post by dhlowe on 2009-07-28
Thanks - tacantara and skyjacker. Problem now solved.

---

