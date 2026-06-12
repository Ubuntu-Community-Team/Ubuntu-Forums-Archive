---
title: "Internet connection in 11.04"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by northwestern on 2011-05-01
I am presently running Ubuntu 11.04 through WUBI on my HP DV5 laptop (Windows 7).When using windows I can flip between wireless and wired easily by pressing the keyboard icon.
Ubuntu 11.04 (and 10.10) will not let me change to the wired option, any ideas please.
Regards
Northwestern

---

### Post by Lateralis on 2011-05-01
If there is a wired connection it will use that.  You can disconnect from either though by (right or left) clicking on the internet connection icon in the top right.  When wired it looks like two antiparallel arrows.  With the WiFi it looks like a WiFi symbol.  

Or, do you mean that with the WiFi off and a network cable inserted you do not have an internet connection?

---

### Post by wittzi on 2011-05-01
I had big problems with my wireless connection after upgrading to 11.04 at the beginning.  Although picking up the wireless network and assigning me an IP address it would not give me access to anything and would essentially not allow me to switch connections.  The exact opposite to you it seems i.e. couldn't switch from wired option to wifi!

In the end I manually disabled wired and enabled wifi and now I can switch between both without any problems.  I truly have no idea why it suddenly worked.

---

### Post by northwestern on 2011-05-01
Thank you for your replies.
At the moment the top bar is showing the up/down arrows which means I must be connected by wire, when I unplug the wire the symbol changes to the wireless network icon but i then loose internet connection. Also the "Enable Wireless" option is greyed out.

Regards
Northwestern

---

### Post by Lateralis on 2011-05-01
Try 

```

sudo ifconfig wlan0 up

```

---

