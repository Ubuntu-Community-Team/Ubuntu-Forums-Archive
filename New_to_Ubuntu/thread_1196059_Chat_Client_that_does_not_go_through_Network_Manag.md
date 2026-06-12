---
title: "Chat Client that does not go through Network Manager"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by pratiks19 on 2009-06-24
Network Manager in Jaunty does not recoginze my internet connection (Mobile Broadband via Bluetooth).
So I cannot use pidgin for chatting..

is there any other chat client which can bypass networkmanager for conecting to the internet ?

---

### Post by Ocxic on 2009-06-24
Apps that use the network don't "go through" the network manager, it's just an easy way to configure your network connections. if you want you can disable network manager or remove it and setup the connection manually.

---

### Post by pratiks19 on 2009-06-25
is it advisable to remove the network manager ?
and after removing nm, will pidgin connect to the manually set up internet ?

---

### Post by mltucker on 2009-06-25
Instead of uninstalling it, just try killing it:

```

sudo killall nm-applet

```

Pidgin probably won't connect by itself, but you can do it at the command line.  You could also try to find another network manager.

To restart the network manager, just run nm-applet.

---

### Post by pratiks19 on 2009-06-27
> Pidgin probably won't connect by itself, but you can do it at the command line. You could also try to find another network manager.

How to use the command line for connecting pidgin ?
and which is a better network manager ?

---

