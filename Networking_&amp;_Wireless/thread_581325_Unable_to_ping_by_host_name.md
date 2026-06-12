---
title: "Unable to ping by host name"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by loveshackdave on 2007-10-19
I'm having problems pinging by host-name between my vista and Ubuntu boxes. I believe the host name is being broadcast because the router shows both machines being connected by their host names and the send hostname line is in the resolve.conf. I use synergy by referencing my ubuntu box by host name on my vista system without any problem but I can't ping it by it's name. Anyone have any ideas?

---

### Post by noob12 on 2007-10-19
What the router sees is just what is sent in the dhcp request.

Some suggestions:
(1) You may find that resolving using the .local suffix works. e.g. **ping MYXPBOX.local**
(2) You may want to install the winbind package
```

sudo aptitude install winbind

```
Then edit **/etc/nsswitch.conf** and add **wins** to the hosts line in the position shown
here:
```

hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="DarkGreen"]wins[/COLOR] dns mdns4

```

---

### Post by loveshackdave on 2007-10-19
great, this sounds helpful. I'll have to try it out when I get home. Thanks!

---

### Post by drinkpepsi on 2007-10-20
Thanks, was what I was needing.

---

### Post by loveshackdave on 2007-10-20
well, installing winbind did the trick. Thanks for your help!

---

