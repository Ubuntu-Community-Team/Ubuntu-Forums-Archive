---
title: "Hewlit Packard printer software"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by benjamin.s.vaccaro on 2009-04-27
Hello,

I **just installed Ubuntu 9.04** and I am trying to connect my HP Deskjet 5740 printer. I tried to go through the Hp website, but to no avail. Could anyone help me find the installer? 

Note: I can use the printer and print, but I need the software to clean the toner etc.

Thanks.

---

### Post by kansasnoob on 2009-04-27
Try running in terminal:

```
sudo apt-get install hplip-gui
```

HP Toolbox should then show up in Systems > Preferences >

After restart you should also have the HP Status Service Icon in the system tray/panel.

---

### Post by benjamin.s.vaccaro on 2009-04-27
Awesome, thanks a lot!

---

### Post by appier on 2009-05-05
I wanted to say "Thank you" to kansasnoob.  I just used your advice as well, and it worked great.

Greetings from Wichita!

---

