---
title: "Login problem ,No no desktop in gnome and kde sessions giving erros messages."
date: 2008-12-21
forum: New to Ubuntu
---

### Post by ravindukelum on 2008-12-21
In my ubuntu ,I've installed kubuntu also ,previously those are workin fine,now I'm going to default gnome session using my default user acount"user name:ravindu" it gives followin error message windows.

<code>
1.Nautilus cannot be used now, due to an unexpected error.

Nautilus cannot be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server.

2.The panel has encountered a fatal error

The panel could not register with the bonobo-activation server (error code: 3) and will exit.
It may be automatically restarted.
</code>

And in kde seesion with that defaul user name:

"kdeinit4 couldn't be intialized"


But when I log in ilke deferent user both gnmoe and kde is work fine .

please help me to solve this.

---

### Post by BDNiner on 2008-12-21
Did you change any config files before you got the error? Did you try to kill the Bonobo-activation server and then restarting nautilus
```

killall bonobo-activation-server

```

It can also happen if you made custom changes to your .bashrc or .profile files. As a last resort you can try reinstalling the ubuntu-desktop

```

sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

```

---

