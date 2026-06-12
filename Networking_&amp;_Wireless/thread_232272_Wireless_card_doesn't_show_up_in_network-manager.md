---
title: "Wireless card doesn't show up in network-manager"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by LittleLebowski on 2006-08-08
Please let me know if this is the wrong place but I cannot figure out how to get my Intel Pro 2915 wireless to show up in network-manager.  Any ideas?

---

### Post by Robor on 2006-08-08
I've got the Intel Pro 2900 and it was recognized and working out of the box.  I can't image there's that much difference between the 2900 and 2915.  I would think the 2915 would be supported as well.  What does a 'ifconfig' and 'iwconfig' give you?

---

### Post by LittleLebowski on 2006-08-08
it's working just network-manager doesn't see it.

---

### Post by LittleLebowski on 2006-08-08
Isn't there a way to add my wireless adaptor info to network-manager so network-manager can configure it?

---

### Post by stmiller on 2006-08-09
You have to edit the file /etc/network/interfaces

---

### Post by LittleLebowski on 2006-08-10
That didn't help me much.  Guess I'll Google and use the search function like I did before I asked this question.  Now if knew exactly what I was doing to the /etc/network/interfaces file, that would be a different story.

---

### Post by gannic on 2006-08-10
Anything listed in there will be ignored by Network Manager.

Comment out the interfaces you want network manager to handle. Only comment out/remove the wlan0 part if thats what its called for you.

Make sure you back up the file first as well.

---

