---
title: "Wireless Networks"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by Timoteo32 on 2009-12-25
So randomly, all of my wireless networks disappeared from the list and I can't get online.  Any common causes and/or where do I go to check on my network card? I don't understand most of what I'm looking at in the menus :(

---

### Post by Mahngiel on 2009-12-25
try from a terminal 
```

nm-applet

```

---

### Post by Timoteo32 on 2009-12-25
what does that do?

??
> Could not acquire  the NetworkManagerUserSettings service as it is already taken.

---

### Post by Mahngiel on 2009-12-25
it starts the network manager so you can connect your wifi.

---

### Post by Timoteo32 on 2009-12-25
and if that doesn't work? i.e. error message above

---

### Post by Timoteo32 on 2009-12-25
bump?

---

### Post by walt.smith1960 on 2009-12-26
For whatever reason the 'notification area' disappeared from the top panel. Try this:


[LIST]
[*]Right click on the panel at the top of the screen. Any blank area should do, I think
[*]Add to panel
[*]Scroll down to 'notification area'
[*]Highlight 'notification area' and left click 'add'
[/LIST]
This fixed my problem. I hope it works for you as well.  My question is why the 'notification area' disappeared. This is not the first time for me. There doesn't appear to be an option to lock it to the panel.

---

### Post by blackened on 2009-12-26
> **walt.smith1960 said:**
> For whatever reason the 'notification area' disappeared from the top panel. Try this:


[LIST]
[*]Right click on the panel at the top of the screen. Any blank area should do, I think
[*]Add to panel
[*]Scroll down to 'notification area'
[*]Highlight 'notification area' and left click 'add'
[/LIST]
This fixed my problem. I hope it works for you as well.  My question is why the 'notification area' disappeared. This is not the first time for me... 


You probably deleted it by accident and didn't realize it. It's really easy to do.

> ...There doesn't appear to be an option to lock it to the panel.

Sure there is, but you're probably using a gtk theme that doesn't have distinct (or even visible) gripper handles. To get the menu for the notification area you must right-click on the space just to the left of the leftmost icon in the applet. 

You can lock the applet, but this will not keep you from deleting it by accident.

---

