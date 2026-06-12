---
title: "Kubuntu non primary users"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by dastasha on 2009-02-27
Ok this has stumped me.

I'm using Kubuntu Intrepid. On the initial install Knetwork found my Huawei E220 USB modem. It was easily configured - I just right clicked on the globe icon down by the time and date and the other icons. Knetwork recognised the modem right from the start. Now I just right click on it, select my provider and I have net access.

I then set up my daughter and wife their own user accounts. When logging in using their details, I right click on the globe icon, select the provider and nothing happens. Normally I see the little rotating gear, then a little antenna or tower to signify a successful connection. But there is no action when I attempt to connect using their accounts. Is it something to do with permissions for the non primary users? I'm out of ideas.

I'm using Kubuntu 8.1 as I said with KDE4.2 if that makes any difference

---

### Post by dastasha on 2009-02-28
I see one or two users have had a similar problem in other forums.
No replies for those guys either.
Could anyone offer help?

---

### Post by dastasha on 2009-02-28
Bump

---

### Post by dastasha on 2009-03-01
Help please?

---

### Post by txcrackers on 2009-03-01
Make sure they're in the "dialout" user group

---

### Post by dastasha on 2009-03-01
They are. I've added them to every group where my own name appears in etc/group with commas between our names.

---

### Post by dastasha on 2009-03-01
Resolved this issue by:

1. Adding the other users to the correct groups (I'm guessing dialout was the main one)
2. Deleting the connection previously established in Knetwork then setting it up again.

---

### Post by clive littlewood on 2009-03-01
Hi

Well done datasha you stuck to it and won !!!!! :P


Thanks for posting your solution it will help others in the future when searching the forum.

Clive

---

