---
title: "password protected samba shares"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by burzum on 2007-08-07
I want some password protected shares that should be accessible from every machine in the network by entering a password and username. The username should not be bound to the current logged in user that tries to access the share. A lot of the tutorials i've read told me to do it this way, but i dont want this behavior.

How can i do that? I've read already some tutorials but i was not able to set the shares up as i wanted them. I was never able to access my shares, ive got always errors.

---

### Post by dmizer on 2007-08-07
i'd like to know why you want to handle your network this way.

primarily because, if i know why ... it might be easier to offer a workable solution.

this is because both in windows and in linux file sharing networks, it is not common to handle password protected shares in this fashion.

---

### Post by burzum on 2007-08-07
Hu? Not common?

In my company i can connect to different shares by entering a user/pass to access them.

For example if i want to access the software share i have to login to this share with the tech-division account made for this share. Because not everybody is allowed to access this share. But thats a windows only network.

---

### Post by dmizer on 2007-08-07
is your company using active domain?

i think it would be difficult to get the results you desire on a simple samba network.  and i don't even know where to start to tell you how to configure an active domain server (not because it's impossible ... but because i haven't made the effort to yet).

---

