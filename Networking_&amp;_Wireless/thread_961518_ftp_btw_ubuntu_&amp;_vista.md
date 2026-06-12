---
title: "ftp btw ubuntu &amp; vista"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by kingkong22 on 2008-10-28
I have one vista and one ubuntu home. both can access internet via wireless. but there are not in LAN. ftp sever has been installed in ubuntu. how can I use ftp from vista to ubuntu ?

---

### Post by nixscripter on 2008-10-28
If they are on the same network, both machines should be able to talk to each other directly unless the router is doing something weird.

First, do you have an FTP client on Vista? If not, try FTP Dummy: [http://www.dummysoftware.com/ftpdummy.html](http://www.dummysoftware.com/ftpdummy.html)

Then just figure out the IP of your Ubuntu box by opening a terminal and running: ```
ifconfig | grep 'inet addr'
```

Depending on how you have the server set up, either try anonymous FTP or your username and password.

---

