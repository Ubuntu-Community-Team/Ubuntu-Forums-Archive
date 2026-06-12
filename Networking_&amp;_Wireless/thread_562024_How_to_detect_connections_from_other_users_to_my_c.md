---
title: "How to detect connections from other users to my computer"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by tisk on 2007-09-28
So I have my samba connection set up so that I can access or be accessed from a large windows network. I also have firestarter running. How can I find out when someone is copying files or streaming from my share?

---

### Post by Cryptog on 2007-09-28
The "surest" way is with this: 

sudo netstat -pan | more

It will show you what ports are open (state=Listen) and who is connected (state=Established).  You will want to do that while no one is connected to get familiar with the ports that are normally open on your box. Then do it again look for anomilys.

---

### Post by tisk on 2007-09-28
thanks, that works really well :)

---

### Post by psusi on 2007-09-28
Less is more.

netstat | less

---

### Post by tisk on 2007-09-28
> Less is more.

netstat | less

that just give me a load of blank lines in the terminal?

---

