---
title: "Network icon?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Revenged on 2009-02-08
In the top toolbar on the right, there was a little network icon, that would allow me to reset my connection. If clicked, it said "wired connection" then some other stuff. I removed it when I was reconfiguring the toolbar. Anyone know how to get it back? (And no, it is not the "Network Moniter" you see when you right click and select "add to panel")

---

### Post by ptn107 on 2009-02-08
It's the NetworkManager applet.  Go to System -> Preferences -> Sessions.  Scroll down the list of programs and look for 'Network Manager' and make sure the box next to it is checked.  If it's not on the list, click add and fill in with this information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

Make sure the box is checked and click ok.  You may have to restart your computer for the changes to take effect.

Edit: Yeah overlord.gaurav's solution is correct, if the notification area was removed then it needs to be added.

---

### Post by overlord.gaurav on 2009-02-08
You've deleted the 'Notification Area'.
Right click on the menu > Click on add > now 'Notification Area' from the list, and you're done.
You'll now see your network icon again.

---

### Post by Revenged on 2009-02-08
> **overlord.gaurav said:**
> You've deleted the 'Notification Area'.
Right click on the menu > Click on add > now 'Notification Area' from the list, and you're done.
You'll now see your network icon again.

Aha! Thank you.

---

