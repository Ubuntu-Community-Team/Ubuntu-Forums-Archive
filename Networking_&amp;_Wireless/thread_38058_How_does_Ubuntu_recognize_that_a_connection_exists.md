---
title: "How does Ubuntu recognize that a connection exists?"
date: 2005-05-29
forum: Networking &amp; Wireless
---

### Post by jkndrkn on 2005-05-29
Lets say your computer is equipped with three routes to the internet.
[list]
[*]Ethernet
[*]Wireless Network
[*]56k Modem
[/list] 
Now, assume that all connections are currently closed. You decided to activate your ethernet connection. What mechanism does linux use to recognize if this connection is open?
Lets say you decide to activate your wireless network adapter. Will linux ignore this new open connection?

Lets say you close all connections and start up your 56k Modem. Now what happened. Is some resource being controlled by the ethernet connection that is now assigned to the 56k Modem. If so, is there a way to manually control which connection has access to that resource?

Any ideas on where to look?

---

### Post by Seti on 2005-06-04
Usually your ethernet connection is eth0 or eth1, and your wireless will also either be eth0 or eth1 depending on how its set up. If you do ```
ifconfig eth0
``` 
in a console it should give you some info on what is connected.

---

