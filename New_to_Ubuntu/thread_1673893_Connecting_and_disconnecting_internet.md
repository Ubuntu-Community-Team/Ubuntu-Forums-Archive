---
title: "Connecting and disconnecting internet"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by zammil on 2011-01-23
hi friends,


I configured my ubuntu  network by using the command  sudo pppoe conf in the terminal so to connect to the internet i just have to switch the modem on.but i want to connect and disconnect internet at my will.in windows it allows me to do that [IMG]http://img267.imageshack.us/i/bsnl.png/[/IMG]
is there any application that allows me to do that in ubuntu????

---

### Post by zammil on 2011-01-23
any help!!!!!!!!

---

### Post by slashwannabe94 on 2011-01-23
Hello Zammil, 

I assume you are using a dongle? 

Also if you are using a mobile broadband dongle, you just need to click on System>Preferences>Network Connections. Then set up your dongle in the Mobile Broadband tab. 

The above is done using the network Manager Applet, in the top right of the ubuntu desktop, on the top taskbar. 

Give me more information on what you are trying to do?

---

### Post by slashwannabe94 on 2011-01-23
> **zammil said:**
> hi friends,


I configured my ubuntu  network by using the command  sudo pppoe conf in the terminal 

according to my terminal "sudo pppoe conf" command does not exist.

---

### Post by alaukikyo on 2011-01-23
in top right corner right click the networking icon and then edit connections and then edit auto eth0 and then deselect connect automatically and now everytime you want to connect to internet ust left click the networking icon and click on auto eth0.

---

### Post by zammil on 2011-01-23
> **alaukikyo said:**
> in top right corner right click the networking icon and then edit connections and then edit auto eth0 and then deselect connect automatically and now everytime you want to connect to internet ust left click the networking icon and click on auto eth0.

thz  alaukikyo but when i get disconnected and then connect again  will i get a new ip address as in windows (for downloading files from filesharing sites as i'm a free user frequent downlading  is possible only by getting a new ip address)plz do reply!!!!

---

### Post by alaukikyo on 2011-01-23
> **zammil said:**
> thz  alaukikyo but when i get disconnected and then connect again  will i get a new ip address as in windows (for downloading files from filesharing sites as i'm a free user frequent downlading  is possible only by getting a new ip address)plz do reply!!!!

i don't know you should try yourself.

---

### Post by dineshs on 2011-01-24
Latest ubuntu versions use Network manager for managing devices.Try this
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)
If you dont have network manager (older linux versions) try pppoeconf
> according to my terminal "sudo pppoe conf" command does not exist.The command is ```
sudo pppoeconf
```.

---

