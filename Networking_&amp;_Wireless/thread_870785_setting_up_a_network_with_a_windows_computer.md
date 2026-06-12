---
title: "setting up a network with a windows computer?"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2008-07-26
I have a Toshiba laptop which is connected to my router via a wireless connection. The laptop runs on windows XP.
My linux pc is connected to the same computer via a cable. How do i set about making a network between the two computers?

---

### Post by dmizer on 2008-07-26
it depends on what you mean by "network".  simply by having both machines connected to the router you have created a network.  if you want to share files between them, then you are looking for a file sharing network.

i will assume (as is often the case) that you would like to create a file sharing network.  for ubuntu, you'll need to configure two separate elements.  first, you'll need to create a samba server.  for more information on how to configure your samba server, see the first link in my sig.  second, you'll want to connect to files shared on your windows machine.  for that, you'll need to configure cifs.  the howto for configuring cifs is in the second link in my sig.

post in the howto threads if you have any questions.

---

