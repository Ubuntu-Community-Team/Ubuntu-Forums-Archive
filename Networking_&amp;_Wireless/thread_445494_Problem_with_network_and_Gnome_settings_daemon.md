---
title: "Problem with network and Gnome settings daemon"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by jEddy on 2007-05-16
Hey everybody

I have been searching for an aswer to my problem and am not getting anywhere. I am still running Edgy because The new version crashes my laptop (another day) and when ever I have a network card active, wireless or lan, the Gnome display daemon fails to start durring the startup process and then gims everything up. The report that it gives is vague, but has to do with not being able to connect to the source. Anyway, it is a huge pain in the neck, I have to disable my networking before I shut down. If anyone could help I would be very grateful. 

Thanks
Jeff

---

### Post by jEddy on 2007-05-16
Anyone have any guesses?

---

### Post by stooshbunutu on 2008-03-01
you can start the gnome-settings-daemon manually if it wont load properly.

Here is what you have to do.

Press Alt+F2 to open a run window.

Then type:
```
gnome-settings-daemon
```
and then click on run.

This will start gnome manually and it will be up within a few seconds.

Hope this helps you, not sure about the networking side but this is one idea for the gnome side

If it happens every boot then add the command to your start-up commands in the sessions section of the system preferences menu.

---

