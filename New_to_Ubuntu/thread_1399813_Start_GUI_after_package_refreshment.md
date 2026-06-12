---
title: "Start GUI after package refreshment"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Pikku_pekka on 2010-02-06
Dear All!

I  use Ububtu 9.10. I have recently refreshed the software packages and from that time on the GUI refuses to start. What command should I use to enable the GUI again?



Thank you for the help in advance!

Regards
/Laci

---

### Post by Psumi on 2010-02-06
reloading software packages shouldn't disable the GUI System.

If there's nothing on the desktop, no panels, etc. you will just need to restart the system, sorry.

Unless you want to go into a tty# terminal.

---

### Post by lotharmat on 2010-02-06
Try ctrl+alt+backspace

this will restart X

If you drop to a terminal (ctrl+alt+f2) and type

```
sudo /etc/init.d/gdm stop
```

and then 

```
sudo /etc/init.d/gdm start
```

What, if any, are the error messages?

---

### Post by Psumi on 2010-02-06
> **lotharmat said:**
> Try ctrl+alt+backspace

this will restart X

If you drop to a terminal (ctrl+alt+f2) and type

```
sudo /etc/init.d/gdm stop
```

and then 

```
sudo /etc/init.d/gdm start
```

What, if any, are the error messages?

I thought crtl+alt+backspace was removed from ubuntu and only enabled via dontzap?

---

