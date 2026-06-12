---
title: "Brand New Install of 9.10 - No Networking"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by Charltp5 on 2010-01-16
Hi, Newbie question... I have a Dell Latitude C400 on which I have installed Ubuntu 9.10.

When I boot up I have an ethernet cable plugged in to my router which is all working fine. But the laptop does not start seem to detect the wired connection and I get "No network connection" when I hovver over the icon on the desktop.

I have tried searching the web but can't find a solution yet...

Any help greatly appreciated.

---

### Post by mapes12 on 2010-01-16
Right click the Network icon and make sure "Enable Networking" is ticked.

---

### Post by Charltp5 on 2010-01-16
Yes it is ticked and I have a connection listed in Network Manager but 'never used'.

How do I check if my network card is actually working properly (drivers installed etc...)?

---

### Post by Charltp5 on 2010-01-16
Network Controller is 3Com 3c905C-TX/TX-M [Tornado] (rev 78) but running System Testing reveals no internet connection.

---

### Post by mapes12 on 2010-01-16
Try highligting it then "Edit" the connection. To check that your ethernet adapter is working in Terminal ```
ping -c4 127.0.0.1
```If no errors come back then try pinging your router. Might be a good idea to reboot the router (switch it off then on again).

---

### Post by Iowan on 2010-01-16
**ifconfig -a** should show available interfaces (even if not enabled). **sudo lshw -C network** will show more information about interfaces.

---

### Post by Charltp5 on 2010-01-16
Yes that works fine - get 4 responses.

---

### Post by Charltp5 on 2010-01-16
> **Iowan said:**
> **ifconfig -a** should show available interfaces (even if not enabled). **sudo lshw -C network** will show more information about interfaces.

ifconfig -a shows 2 interfaces eth0 and lo

sudo lshw -C network show me loads of info about my ethernet adapter.

Still no connectivity. In Networks I have Wired Network with disconnected greyed out and VPN Connections > Configure VPN...

---

### Post by Charltp5 on 2010-01-25
> **Charltp5 said:**
> Hi, Newbie question... I have a Dell Latitude C400 on which I have installed Ubuntu 9.10.

When I boot up I have an ethernet cable plugged in to my router which is all working fine. But the laptop does not start seem to detect the wired connection and I get "No network connection" when I hovver over the icon on the desktop.

I have tried searching the web but can't find a solution yet...

Any help greatly appreciated.

[COLOR="Red"]**[SIZE="3"]Can anyone help with this as I am still no further forward... I haveno network/internet wired/wireless connectivity at all... thanks.[/SIZE]**[/COLOR]

---

### Post by Iowan on 2010-01-25
Easy to get lost in the forest of threads...
I think I've worn the good off of [this]("http://ubuntuforums.org/showthread.php?t=1156441") one, but have a look, anyway. One of the last posts is about making the machine look like Windows box.

---

