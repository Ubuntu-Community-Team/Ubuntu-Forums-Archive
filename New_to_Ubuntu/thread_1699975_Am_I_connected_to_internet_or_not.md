---
title: "Am I connected to internet or not?"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by Fanatico on 2011-03-04
I've successfully set up adsl connection using Ubuntu documentation

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

I can connect to ISP provider via adsl modem using pon dsl-provider command and disconnect using poff.

However I don't have any indication on the system status bar whether I am connected to internet or not.

How can I get indication whether I am connected to internet or not?

Thanks

---

### Post by Frogs Hair on 2011-03-04
If you hover the mouse pointer over the notification area icon it will indicate connection type and active status .

---

### Post by Fanatico on 2011-03-04
No, if I hover the mouse pointer over the notification area icon it shows: "No network connection". However I obviously do connected to Internet.

---

### Post by grahammechanical on 2011-03-04
Can you surf the web? Load Update Manager and click Check. Open the Ubuntu software Centre select a program and click on the link to that programs web site. If you have access then you are connected.

Load System Monitor and see if you are sending and receiving and how fast it is.

Regards.

---

### Post by Fanatico on 2011-03-05
grahammechanical,

Yes, I can surf the web, but I don't have any indication on the status bar that I am connected.

---

### Post by dionysius on 2011-03-05
Did you use Network Manager to set up the connection, or did you use the CLI method described in the docs? If the latter, it may be the case that Network Manager isn't actually managing your connection.

---

### Post by Ben Page on 2011-03-05
Click on the network manager applet in the notification area and choose "edit connections". In there you should see all connections managed by network manager. It may be a glitch, reboot your OS and try again if there are no connections there. If everything fails, open terminal and type:

```
ifconfig
```

and post the output.

---

