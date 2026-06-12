---
title: "lamp vs kubuntu"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by flameash on 2011-01-05
hi, everyone.

newbie here.

I got my LAMP server running fine with a little testing website.
I searched on google and found that Kubuntu looks really nice and I want it to be my desktop.

I know from web that everyone is installing LAMP on Kubuntu. 
But the thing is that I'v already installed LAMP on the server machine.  Can I install Kubuntu now without affecting on my LAMP server? :confused:

pre-thanks!

---

### Post by bodhi.zazen on 2011-01-05
> **flameash said:**
> hi, everyone.

newbie here.

I got my LAMP server running fine with a little testing website.
I searched on google and found that Kubuntu looks really nice and I want it to be my desktop.

I know from web that everyone is installing LAMP on Kubuntu. 
But the thing is that I'v already installed LAMP on the server machine.  Can I install Kubuntu now without affecting on my LAMP server? :confused:

pre-thanks!

You can, but if it is a dedicated server that is not such a great idea. If you need a graphical interface for a server use something similar to webmin or phpmyadmin.

If you are using it as a desktop + server (sharing files over nfs or samba on a LAN) you will be fine.

```
sudo apt-get install kubuntu-desktop
```

---

### Post by flameash on 2011-01-05
Thank you very much.

I tried your code and now the interface is working fine; the server works fine as well.

/bow

---

