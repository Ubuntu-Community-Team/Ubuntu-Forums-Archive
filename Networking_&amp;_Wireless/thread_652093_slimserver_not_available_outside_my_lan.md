---
title: "slimserver not available outside my lan"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by spx3 on 2007-12-28
hi,
I'm behind a router and altough I've forwarded port 9000 to the computer wich is running
slimserver I still can't play the stream outside my lan.
what can I do ?

---

### Post by mellowd on 2007-12-29
To what IP are you trying to connect from outside your lan? when connecting from outside you need to connect to your public IP (the ip address given to you by your ISP) the forward will then forward port 9000 to the respective machine.

from outside your lan are you able to telnet to port 9000? (you won't connect, if it gives you an error you haven't, if it says nothing you have connected)

---

