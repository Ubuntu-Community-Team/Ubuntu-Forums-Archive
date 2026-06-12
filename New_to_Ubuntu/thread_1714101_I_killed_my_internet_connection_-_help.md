---
title: "I killed my internet connection - help"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by garyed on 2011-03-24
Ubuntu 10.04 on my Desktop wired internet.
Everything has been working fine for quite a while.
I was experimenting with "/etc/NetworkManager/nm-system-settings.conf" to get an icon on the task bar. I changed "managed=false" to "managed=true" then issued the command:
```
sudo killall nm-system-settings       

```
I rebooted & the icon appeared in the task bar but the "wired internet" option was grayed out & I haven't been able to reconnect. 
I saved the original nm-system-settings.conf file so I put it back & rebooted but still no internet connection.
Any ideas?

---

### Post by garyed on 2011-03-24
Well I guess I just got paranoid, everything worked out.
I went to System-Preferences-Network Connections & added a wired connection. I then repeated the original steps that got me into trouble & when the network icon appeared this time there was an added option for the new wired connection. Once I got it working I put the files back to their original state rebooted & no more network icon but my internet is working O.K. now.

---

