---
title: "Cannot remove Nexus 5 Network from network list"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by hellocatfood on 2014-08-11
When I click on the Network Manager indicator I have an odd entry in there called Nexus 5 network

[IMG]http://i.imgur.com/LwnJhtA.png[/IMG]

Clicking on it does nothing and it does not show up in the list of networks in Edit Connections

[IMG]http://i.imgur.com/Z2l8mMT.png[/IMG]

The university I'm studying at suggests that this is causing some of the connection troubles that I'm having. Can anyone suggest why this is appearing and how I can have it safely removed? I'm running Ubuntu 14.04 on a Dell XPS 13 laptop.

---

### Post by varunendra on 2014-08-14
What does this show -
```
nmcli con
```
You may post only relevant part of the output.

---

### Post by hellocatfood on 2014-08-19
> **varunendra said:**
> What does this show -
```
nmcli con
```
You may post only relevant part of the output.

```
NAME                      UUID                                   TYPE              TIMESTAMP-REAL                    
Nexus 5 Network           5e2aaef6-4e59-451b-b193-799f4cffb159   bluetooth         never  
```

---

### Post by lisati on 2014-08-19
> **hellocatfood said:**
> ```
NAME                      UUID                                   TYPE              TIMESTAMP-REAL                    
Nexus 5 Network           5e2aaef6-4e59-451b-b193-799f4cffb159   [COLOR="#FF0000"]bluetooth[/COLOR]         never  
```

The network name seems to relate to a connection via bluetooth. I notice that you've got a blutooth icon showing on the screenshot in your first post. Does accessing your bluetooth settings shed any light on this network?

---

### Post by varunendra on 2014-08-19
> **lisati said:**
> The network name seems to relate to a connection via bluetooth.

Yup. That is the kind of connection that is created when you connect to internet by tethering your phone via bluetooth. Network Manager does not provide settings control for such connections, only uses it. These connections are created (and can be deleted) using the Bluetooth device settings.

The bluetooth manager will show only the paired devices (when bluetooth is "On") in its device list. Deleting the one that was used to create this connection will also delete the connection from NM profile.

Alternatively, you can delete this file manually -
```
sudo rm "/etc/NetworkManager/system-connections/Nexus 5 Network"
```
..assuming the key-file name is same as the connection name (it usually is). The double-quote is important because the name contains blank spaces.

---

### Post by hellocatfood on 2014-08-26
> **lisati said:**
> The network name seems to relate to a connection via bluetooth. I notice that you've got a blutooth icon showing on the screenshot in your first post. Does accessing your bluetooth settings shed any light on this network?

Why indeed it does! All I did was untick the mobile network setting and it's now gone from the networks list!

[IMG]http://i.imgur.com/Yuu34Zw.png[/IMG]

Thanks

---

