---
title: "Free NX - login to same session?"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by pickarooney on 2008-06-24
Is there some way of getting NX to connect to the existing linux session so I can use it to remotely train a user? 
I first tried setting up VNC, which did the same thing (created a new session) and was hoping NX would be a better solution.

edit: It's not actually the separate program freenx, but the free version of NX

---

### Post by Sawyer_ on 2008-06-24
When you terminate the current session in NX, it prompts you a window asking if you want to disconnect or terminate from the current session.

When you select disconnect, when you log in through NX the next time, the client will prompt you a list of the sessions available and then you will be able to resume the previous session.

---

### Post by pickarooney on 2008-06-24
What I really mean is that if someone is sitting in front of the PC, can I connect in such a way that they see on the screen what I'm doing with the mouse and keyboard?

---

### Post by Sawyer_ on 2008-06-24
Ah, I think that is possible by selecting the Shadow desktop setting from the general tab in the configuration.
This will allow another client to attach to the running session.

---

### Post by pickarooney on 2008-06-24
This is in the server config then? I'll have a look, thanks :)

---

### Post by Sawyer_ on 2008-06-24
No, I was talking about the configuration on the NX Client.

---

### Post by pickarooney on 2008-06-24
Ah... brilliant, thanks :D

---

### Post by Baneblade on 2009-08-15
I was looking for this as well as it would always create a new session and change all my themes. I still find creating a new session quicker from a remote location though (probably compiz' fault i think?)

Anyway, thanks to Sawyer_ for pointing out "Shadow"!

---

