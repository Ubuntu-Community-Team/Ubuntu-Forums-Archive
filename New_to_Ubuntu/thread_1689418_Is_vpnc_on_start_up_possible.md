---
title: "Is vpnc on start up possible?"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by WhatAreHackers on 2011-02-16
I want to use a command on startup for instance.... sudo vpnc-connect vpn/hotspot ....is this possible?

---

### Post by sanderd17 on 2011-02-16
sudo will be dificult since you will have to enter your password. you can use gksudo instead to get a graphical way to enter your password.

to start commands on startup, just add them to the startup manager.
```

startupmanager

```

---

### Post by WhatAreHackers on 2011-02-16
> **sanderd17 said:**
> sudo will be dificult since you will have to enter your password. you can use gksudo instead to get a graphical way to enter your password.
 
to start commands on startup, just add them to the startup manager.
```

startupmanager

```
 
K... I got an error when i started up startupmanager... I am using firestarter, vpn and ubuntu 10.04... would this conflict with startupmanager?

---

### Post by sanderd17 on 2011-02-16
> **WhatAreHackers said:**
> K... I got an error when i started up startupmanager... I am using firestarter, vpn and ubuntu 10.04... would this conflict with startupmanager?

I've seen in the mail what kind of error you got (you should leave it in the post, just between code blocks) and I'm afraid I can't help you. I don't see what is wrong.

---

### Post by sanderd17 on 2011-02-16
sorry, I was completely wrong, it's the program
```

gnome-session-properties

```
that you need

---

