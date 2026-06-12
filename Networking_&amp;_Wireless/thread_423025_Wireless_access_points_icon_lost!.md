---
title: "Wireless access points icon lost!"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by conteur on 2007-04-25
Usually I do things a lot more catastrophic than this. I right clicked on the separator bar on the Ubuntu panel that was next to  the little blue vertical bar icon that show my wireless signal strength and access points. Now the separator is gone along with the icon. The network is still running, but how do I get the icon back? Also I can no longer see the blue circle that shows up when I run Firestarter.

---

### Post by medad on 2007-04-26
You accidently removed your Notification Area.  Click "add to panel" on the upper panel near where you removed your notification area.  Re-add the Notification Area and lock it.  Then log out of Ubuntu and log back in.  You will see all of the icons that you are currently missing.

I posted something similar in your other thread.

---

### Post by mrpaco on 2007-04-26
If you are running Feisty, running  ```
nm-applet --sm-disable 
``` should get your network status back up and running.  I am not familiar with Firestarter though.

---

