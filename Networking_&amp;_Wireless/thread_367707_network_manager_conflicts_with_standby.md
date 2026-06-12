---
title: "network manager conflicts with standby"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by ldbooth on 2007-02-22
Hello World!

I am running into a problem where Network Mangager works most of the time, but I travel around between school, home, coffee shop and I use standby a lot. 

Every once in a while (especially in WEP) when I come out of standby the Network Manager applet shows no connections.

I ran iwconfig in the terminal and it shows the 'ncsu' essid I want to connect to, but network manager can't find it. I can fix it by killing the Network Manager process and rebooting it. Anyone know why this is happening? Again it only happens sometimes (1 of 10).

I'm running Edgy Eft and I also run beryl (which might be the issue).

---

### Post by srt4play on 2007-02-22
This happens too on my girlfriend's Acer laptop.  She runs Dapper though.  Simply right clicking network manager in the notification area and unchecking and then rechecking 'enable networking' fixes it.  It used to annoy her quite a bit but she got used to it.

---

### Post by ldbooth on 2007-02-22
> **srt4play said:**
> This happens too on my girlfriend's Acer laptop.  She runs Dapper though.  Simply right clicking network manager in the notification area and unchecking and then rechecking 'enable networking' fixes it.  It used to annoy her quite a bit but she got used to it.

I discoverd that last week, but this week I have tried it numerous times (disable / re-enable) and it has stopped working. Everytime I kill the process and I boot NetworkManager from the terminal my wireless networks are there! 
Is there a refresh or up/down command for NM?

---

### Post by srt4play on 2007-02-23
Hey ldbooth - 

try putting these two scripts in place:

/etc/acpi/suspend.d/07-networkmanager.sh -  make sure the number is right after acpi-lock, adjust if necessary.

```
#!/bin/sh

/usr/bin/dbus-send --system \
--dest=org.freedesktop.NetworkManager \
--type=method_call \
/org/freedesktop/NetworkManager \
org.freedesktop.NetworkManager.sleep
```

and

/etc/acpi/resume.d/63-networkmanager.sh - make sure the number is right after ifup.  adjust if necessary.

```
#!/bin/sh
       
/usr/bin/dbus-send --system \
--dest=org.freedesktop.NetworkManager \
--type=method_call \
/org/freedesktop/NetworkManager \
org.freedesktop.NetworkManager.wake
```

Don't forget to make them executable.

see [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/40125]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/40125")
for more info.

It now works pretty much every time for me.

---

