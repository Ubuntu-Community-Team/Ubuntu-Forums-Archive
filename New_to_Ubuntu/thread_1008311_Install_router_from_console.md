---
title: "Install router from console?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by WileyGaia on 2008-12-11
Hi - is it possible to install my DSL router from the console in Recovery Mode? I have a brand new router, but cannot get to the normal GUI in Ubuntu 8.10 because I have a "Ubuntu has to start in low graphics mode" problem.
I figured that maybe the fixes I have been given are dependent on an internet connection, in which case I need to configure my router from the console...?

---

### Post by Paqman on 2008-12-11
You could try to install a text-only browser like Lynx and see if you can browse to the router control panel through it.

```
sudo apt-get install lynx
```

(You won't need the sudo if you're in recovery mode)

---

### Post by halitech on 2008-12-11
normally routers are plug and play, just plug it in and start it up and your computer should get an ip address. only catch might be if you need to log in with a pppoe connection from the router.

---

### Post by Paqman on 2008-12-11
> **halitech said:**
> normally routers are plug and play, just plug it in and start it up and your computer should get an ip address. only catch might be if you need to log in with a pppoe connection from the router.

They're plug and play between the router and PC, but you'll need to set up the details of your connection to your ISP. You'd also need to set up your wifi if it had it.

---

### Post by halitech on 2008-12-11
I'm on cable internet and as soon as I powered everything up, it worked. Maybe I'm one of the lucky ones who has an ISP that doesn't require making a bunch of changes. I also don't use wireless.

---

### Post by gpsmikey on 2008-12-11
the router should play with your isp although you may have to clone the MAC address.  You should be able to use the GUI in the "Live CD" to get to the router and configure that if that is what you need to do.  I'm not aware of a way to get into the router with the command line (although some support telnet, I have not done that method).

mikey

---

### Post by ajcham on 2008-12-11
> You could try to install a text-only browser like Lynx and see if you can browse to the router control panel through it.

Speaking from personal experience, I have a D-Link router with a browser based control panel.  However, it is frame based and consequently doesn't play nicely with lynx.

I would boot up with a live disc and see if I could access the control panel that way.

---

