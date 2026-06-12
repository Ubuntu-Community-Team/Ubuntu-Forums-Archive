---
title: "Change Router Settings - from where?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Teasdale on 2009-08-18
I have a Netgear wireless N router and I'm having trouble with some devices not finding the signal. Most laptops can find the signal, but other devices can't see it. After searching around the internet, it seems that N-routers can cause this kind of problem and one possible fix is to change the router settings to "mixed mode."

I'm assuming this is something I do on my PC. I found one instructional webpage that said to go to "advanced." I'm guessing that assumes I'm using Windows. With Ubuntu, where do I find these settings?

I've looked under System > Preferences > Network settings but I don't see anything there. There's nothing even listed under Wireless. My set-up is a modem plugged into a router; the PC is plugged into the router with a cable, but the router is also wireless.

---

### Post by lisati on 2009-08-18
Many routers have a browser-based interface. On my Netgear WGR614v7 router I'm able to hook up via a wired connection, open firefox and navigate to [http://routerlogin.net]("http://routerlogin.net")

---

### Post by Teasdale on 2009-08-18
OK, I'll see if my router has a web interface - the link posted takes me to a blank page with some script saying "denied," but I'll look into a specific site for my make and model.

---

### Post by Nimless on 2009-08-18
Usually the default ip address of routers is [http://192.168.1.1](http://192.168.1.1)

Type it manually in the url bar otherwise Firefox will complain :P

---

### Post by Mark Phelps on 2009-08-19
> **Teasdale said:**
> I'm assuming this is something I do on my PC. I found one instructional webpage that said to go to "advanced." I'm guessing that assumes I'm using Windows. With Ubuntu, where do I find these settings?
You don't.  These are setting in the router's configuration tabs.

> ...the PC is plugged into the router with a cable, but the router is also wireless.
Look at the IP address assigned to your PC when it is plugged into the router in Wired mode.

If your IP address is 192.168.0.nnn, the router will most likely be 192.168.0.1

If your IP address is 102.168.1.nnn, the router will most likely be 192.168.1.1

Enter the appropriate IP address manually into a Browser window and you should see your router config page.

---

