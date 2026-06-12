---
title: "basic help on getting wifi connection"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by tshapin on 2008-01-04
I installed xubunto 7.10.

When I click on the upper right icon for connections, I see several wifi routers. i select the one in my house and see the opportunity to type my password. 

1. Can I leave it at automatic or should in select tkip? I tried both.

2. After I save it nothing happens. There is no attempt to connect, i.e. I do not see the icon changing to curved arrows. Is there something else I should do?

3. If I click on the connection icon and select my router again, my password was not saved; there is a blank password area. Is this normal?

Please tell me what I should do to get a connection.

---

### Post by jan quark on 2008-01-04
if the roaming mode makes trouble try a manual configuration.

click on the network applet in the right corner and select manual configuration

then type in the needed stats.

oh by the way please post the results of the following commands you can type into the terminal
```
lspci -v | less
```
```
ifconfig
```
```
iwconfig
```
```
sudo iwlist scan
```
 these gather more info about your network status

---

### Post by tshapin on 2008-01-04
Here is how I got my connection with no help from the forum!

1. I clicked on the network applet and clicked on "connect."

2. While the icon changed into moving arrows, I clicked on the icon again and selected the name of my router.

3. I typed my router password in the window and selected "connect."

4. My keyring came up and asked me for a password which I supplied.

I waited a few seconds and GOT MY CONNECTION


Thanks to ME for posting this. It may help some other newby! :-)

---

