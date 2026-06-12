---
title: "No Internet through Firefox"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Rsrockerz on 2008-07-24
Ok, I'm new here, so go easy on me.

I've been using ubuntu since 6.06 and I haven't had this problem. Ok, so when I turn my computer on, Everything have the OK mark issued e.g. Starting Firestarter    OK. Then I login, X11 start perfectly. Pidgin opens, and I can chat with my friends. But when I open firefox to use the internet, I get this (I code my links so their not live) : 

```

http://imagenerd.com/uploads/firefoxwBsT.png

```

Also, when I run "sudo apt-get update", it works:

```

http://imagenerd.com/uploads/terminalOlpn.png

```

When my sister logs into her account, she can chat too, but no firefox. I have also tried other browsers, and sites other than Hotmail.

Any help?

---

### Post by Rsrockerz on 2008-07-24
Bump

---

### Post by Tom--d on 2008-07-24
Are you using Network Manager? 

If you are not. 
Remove it!
```
sudo apt-get remove network-manager
```

Firefox, for some reason, relies on Network manager for a connection. once that has gone. It looks else were.

If the connection is done through Network Manager, then I dont know :\

---

### Post by nukleuzN on 2008-07-24
File -> uncheck "Work offline"

---

### Post by Rsrockerz on 2008-07-29
Nope neither of those helped, though thanks for trying. Any one else?

---

### Post by cpcgm on 2008-08-27
Similar thing here. Sometimes Firefox refuses to load any page while Epiphany doesn't have the slightest problems.

---

