---
title: "Having trouble viewing other computer on the network."
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by Mattevt on 2008-07-27
I'm trying to access a computer that is shared on my network.

I used to be able to click Places>Network>Windows Network, and I could see the other computer. Now, ever since I switched routers, I click "Windows Network", the computer hangs a bit then displays an empty folder. (The numbers are all the same, it's just a new router) Any ideas as to what I may be overlooking? 

Thanks for any insight.

(I'm running 8.04)

---

### Post by Mattevt on 2008-07-28
I'm sorry. Bump.

---

### Post by rukshankb on 2008-07-28
Do you have Admin access on the LAN?

---

### Post by Mattevt on 2008-07-28
The network is open for right now. So we can figure this out. My laptop dualboots with Vista. Vista sees the network fine but Hardy doesn't. On of two family desktops is Hardy only, the other is XP. Neither Ubuntu installation can view the windows network.

---

### Post by ChumleyEX on 2008-07-28
are you able to ping the other computer via the Ubuntu box?

---

### Post by caljohnsmith on 2008-07-28
If you do "smbtree" at the command line, does it return the network?

---

### Post by anubhavrocks on 2008-07-28
Find out the IP address of your windows box.Lets say its 10.0.0.1
Now open the terminal.And give the following command
```
nautilus smb://10.0.0.1
```

---

### Post by Mattevt on 2008-07-28
Well, suddenly the network works. I don't know what happened. I was trying all kinds of things last night, (everything that's been suggested here and then some), then I gave up. I woke up this morning and suddenly it's connected again. Oh well, I hope it doesn't disappear again. 

Thanks for all the suggestions. Ubuntu community support, between the forums and IRC, really is the best.

---

