---
title: "Multi-user connection to dial up internet. How?"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by crazypiglady on 2007-01-23
How can I give all users access to log on to the internet without giving them the root password? It seems that whomever  is logged into Ubuntu, they are asked for the administrators root password when they want to connect to the internet. I’m using an external dial up modem. There are no problems with the hardware or connection I just want all users to have access to just click. Have a missed a checkbox somewhere or something?

---

### Post by rmartz on 2007-01-24
What are you using to connect to the internet?

---

### Post by crazypiglady on 2007-01-26
I’m using a pace external modem and the default gnome-ppp connection and the telephone on the panel. I think it’s a permissions thing and think I may have solved the problem by clumsily giving compete access to everything on the list I found under users and permissions. I think this is giving users permission to use their own password but hopefully not permission to affect the system. I’ll check out what damage I can do as a guest user.

---

### Post by rmartz on 2007-01-26
Full permissions ... like kids in a candy store, huh?

Hope all goes well.

---

### Post by crazypiglady on 2007-01-30
Hmm. Yes well. I’m also having similar problems with Debian (gnulinex) and that specifies root password. At the moment, to get it working, I’m happy to be relaxed in giving permissions. But even ticking all the checkboxes offered in the / users profile permissions tab/, which include allow users access to modems etc doesn't affect this. The root password works and that's all. I thought it may be something with the way I’m connecting. I was trying to use the modem lights (or red telephone) to connect but that doesn't work. All the information is the same as in the networking properties in which clicking activate works. Its probably the sort of thing that various clicking about with it, I’ll fix but I thought there may be a simple solution to get my head round it. Maybe another ppp.

---

