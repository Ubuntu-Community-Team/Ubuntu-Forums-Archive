---
title: "Running wifi-radar as root at login"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by akniss on 2006-07-22
Is there a way to have the wifi-radar gui come up when I login without having to enter my sudo password a second time?  I have ```
wifi-radar -d
``` in my startup programs, which brings up wifi-radar on login just as I want, but it makes me enter my root password, which I just had to put in at login.  Is there any way to start the program at login as root so that I don't have to type my password twice?

---

### Post by st14n on 2006-08-25
Edit: I see now that you asked for the gui. Then this is not the solution for you beacuse it connects to the network using wifi-radar deamon in the background.

You've probably got a solution for your problem already, but I'll tell you how I do it anyway.

There are other ways of course, but one of the easy ways is to use the tool sysv-rc-conf to set wifi-radar to start at boot. Install and run this application:

```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```

Set the wifi-radar process to start at runlevels 2, 3, 4, and 5.

---

### Post by akniss on 2006-08-25
Thanks for the response.  Its funny you respond now, as although i posted this about a month ago, just yesterday I got network-manager configured and working properly to do what I had been trying to get wifi-radar to do... which is allow me to choose the proper wireless network right after login.  So, anyway I appreciate your help, and if something breakes network-manager (I've heard it can be kind of flaky sometimes) I will deffinately give your suggestion a try.

---

