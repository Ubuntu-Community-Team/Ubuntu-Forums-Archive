---
title: "dsl connection"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by mavenuparker on 2010-09-01
I'm trying to set up dsl connection (modem connection, not router) in kubuntu 10.04. I added new dsl connection, set up my username, service (pppoe) and password. However, the knetwork manager doesn't show my new connection on connection's list.
:(:(

im unable to connect to internet...please help me..

---

### Post by juil on 2010-09-01
maybe you can tell us what shows under connection information and edit connections.

---

### Post by mavenuparker on 2010-09-01
the dsl network I added in the edit connections menu under dsl doesn't show up in the available network connection in knetwork manager.....

---

### Post by egalvan on 2010-09-01
regarding
 *modem connection, not router*

??
brand
model name
model number
??

---

### Post by dineshs on 2010-09-01
While configuring the connection,did you tick [COLOR="Blue"]Available to all users[/COLOR]?

---

### Post by juil on 2010-09-01
Normally, there's no need for you to edit the Auto Eth0 connection.

Try going to IPv4 Settings tab and choose Automatic (DHCP) and check the Connect Automatically and Available to all users box.

Also, reset your modem and make sure it's not cabling issue.

---

### Post by Clever_Username on 2010-09-01
I used to use ppoe software years ago and as I recall it requires a username and password to pull an ip. So I wouldn't think you could just set the interface configuration to use dhcp without first going through authentication.

---

### Post by juil on 2010-09-01
I have windows installed on my system. When I got my dsl, I just had to access my modem via web-browser and configure username and password, but i never had to use a network manager in windows or ubuntu to get my internet connection. It just did it automatically.

---

### Post by mavenuparker on 2010-09-02
i could not find any check box for available to all users out there....

---

