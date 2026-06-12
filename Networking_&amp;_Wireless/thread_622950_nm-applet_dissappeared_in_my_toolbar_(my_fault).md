---
title: "nm-applet dissappeared in my toolbar (my fault)"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by oddworld on 2007-11-25
I I accidentally clicked "remove from panel"  on the network manager, the one with all the wifi bars.
Now I don't know how to bring it back.
Wifi works, but I cant find the manager in the bar, or when I click "add to panel" and that menu pops up.
Running Gusty.
Internet works, just no manager.

Thanks!

---

### Post by arvevans on 2007-11-25
look at "/usr/bin/nm-applet"
If that is the one you want you should be able to execute it from a terminal screen.
_._

---

### Post by oddworld on 2007-11-25
In the terminal, whenever I run nm-applet, the terminal does nothing. Just hangs.
In preferences -> sessions, nm-applet --sm-disable is still listed.
My network works, I just accidently deleted the icon in my toolbar

---

### Post by arvevans on 2007-11-25
Right-click on the panel where you want the nm-applet to appear.  Select "Add to Panel".
A window should pop up that will allow you to scroll down to "System and Hardware".
Select "network monitor" from that menu, and click on "add" at the bottom of the window.

All this applies to Gnome WM, not sure what it will be if you are running KDE or something else?

_._

---

### Post by oddworld on 2007-11-25
SOLVED!
In the future, anyone who has this problem should do this:
In order for nm-applet to appear in the panel, it required "notification area" to be in the panel.
To add notification area, right click on panel and "add to pannel", then click notification area.
Then make sure in System -> pref -> sessions that Network Manager has the command nm-applet --sm-disable
This just means that network manager will run at startup.
The Notification Area is the area where your network manager icon will appear.
Try restarting if it does not work right away.

I ended up fixing my own problem, I just thought I would tell everyone the solution if anyone does the same thing.

---

### Post by arvevans on 2007-11-25
Sounds like you might have known the answer before you ask the question?
In any case, glad to see that your problem is solved and you are again a Happy Linux User.
 :)

_._

---

### Post by oddworld on 2007-11-25
Yea, I have used ubuntu 2-3 times in the past, but only used it for about 4-5 hours. 
I would end up breaking something, or couldnt get wifi to work and got frustrated and switched back to xp.
But with 7.10 everything has been so easy!
I have had 40 questions / problems and found the solution in less than two minutes by going online (mostly this site).
So I think I am sticking to gusty... I never thought I would say this but bye bye xp.

---

### Post by m3tr0g33k on 2007-11-26
**Thank You!!**
Been bugging me on and off for days - the wifi notification is great and works well, but NOT without the notification manager!

that's not in any of the nm-applet docs. Maybe it should be listed as an operational dependency? Maintainers?

thanks again!

---

