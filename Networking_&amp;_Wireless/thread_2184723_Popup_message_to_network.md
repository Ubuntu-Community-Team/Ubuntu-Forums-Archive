---
title: "Popup message to network"
date: 2013-10-30
forum: Networking &amp; Wireless
---

### Post by adam17 on 2013-10-30
Hi, 

I would like to send a pop up message out across my network basically to alert people of an event. is there such a command in the terminal where I can do this and send it to specific ip and or an ip range on the network?

Adam

---

### Post by ian-weisser on 2013-10-30
Do you mean "Is there a way I can alter the screens of other users on systems that I am not logged into?"

No. That would be a huge annoyance and security hole.

It is certainly possible to script up a rather simple listener that runs on each system that takes certain network input and displays it to everybody's screen.

Alternately, it is also certainly possible to script up a rather simple script that ssh into each system in the network and then send a message to each user's screen.

Neither is terribly difficult.

---

