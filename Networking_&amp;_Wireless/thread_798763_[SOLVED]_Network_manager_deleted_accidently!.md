---
title: "[SOLVED] Network manager deleted accidently!"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by kenchie on 2008-05-18
Hi -

I have inadvertantly deleted the Network Icon from the taskbar which allows me to enter and select wireless networks. How do I get it back?

Thanks!

---

### Post by prshah on 2008-05-18
> **kenchie said:**
> 
I have inadvertantly deleted the Network Icon from the taskbar which allows me to enter and select wireless networks. How do I get it back?


Alt+F2, then```
nm-applet
```

?

---

### Post by kenchie on 2008-05-18
Thank you!

---

### Post by kenchie on 2008-05-30
Hi -

This fix works fine in KDE, but not in Gnome. If I run the above command in Gnome, nothing happens. All I need is the toolbar icon so I can select 'connect to other wireless network..'

Any ideas please?

Thanks!

---

### Post by james_vanb on 2008-05-30
You should be able to right click on the panel - A drop down will appear - Find the Network Manager icon - Drag and drop it back on the tool bar.

---

### Post by kenchie on 2008-05-30
Hi -

Thanks for the reply. In the 'Add to panel' dialog, Network Manager doesn't appear!

---

### Post by dnairb on 2008-05-30
2 possibilities:

1. Check that there is a notification area on one of your panels (the Network manager icon appears here). If not:

Right-click a panel
Click on "Add to panel"
Scroll down the list and select "Notification Area"
Click "Add"

2. The other possibility is that Network Manager is not loading at startup, or its command is wrong.

System --> Preferences --> Sessions

On the "Startup Programs" tab there should be an entry for Network manager.
If so, make sure that it is ticked.
If not, click "Add" on the right, and enter the following:

Name: Network Manager
Command: nm-applet --sm-disable

Click OK, close the window, reboot and the icon should appear in the notification area of one of the panels.

---

### Post by kenchie on 2008-05-30
Hi dnairb -

Yes no.1 fixed the problem - thanks!!!

---

### Post by dnairb on 2008-05-30
You're welcome. Glad to help.

---

