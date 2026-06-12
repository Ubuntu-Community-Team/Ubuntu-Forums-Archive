---
title: "Firestarter firewall application"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Red Rebel on 2008-12-12
Hi All:

Is there a practical way to set up the Firestarter firewall application to start automatically upon start up?

---

### Post by aheckler on 2008-12-12
Your firewall automatically starts upon bootup, Firestarter is just a GUI, not the actual firewall itself.

Sorry if you already know this, just trying to clear stuff up.

---

### Post by juanoleso on 2008-12-12
Firestarter is just a gui front end for iptables (which is the actual firewall) and it sets up iptables to load firewall rules at startup after you install the program.

if you would like the gui to pop-up each time you login got to system >  preferences > sessions, click add then type a name (firestarter) then a command, this is going to be "gksu firestarter", then hit ok and close.

One other thing, if you are behind a router, then you are probably already firewalled with that.  It might be redundant.

---

### Post by Red Rebel on 2008-12-12
Yes, I am aware of the fact that Firestarter is just an application to configure the Ubuntu firewall. The reason I ask is, because, I want to make sure that my configurations I set through Firestarter are allways active. Once I configure the Firewall through Firestarter, do I have to have Firestarter always active?

---

### Post by juanoleso on 2008-12-12
no, if you want to make sure that your rules are active, open a terminal and put:
```

sudo iptables -L

```
and it will show you that all of the rules that firestarter put in place have been loaded.

---

### Post by Nepherte on 2008-12-13
> **Red Rebel said:**
> Yes, I am aware of the fact that Firestarter is just an application to configure the Ubuntu firewall. The reason I ask is, because, I want to make sure that my configurations I set through Firestarter are allways active. Once I configure the Firewall through Firestarter, do I have to have Firestarter always active?
The firewall rules created by firestarter are loaded upon booting. So you don't need to startup firestarter to get its configuration to work.

You can check your firewall configuration with the command juanoleso gave you.

---

