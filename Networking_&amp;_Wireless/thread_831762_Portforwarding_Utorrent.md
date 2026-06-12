---
title: "Portforwarding Utorrent"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by seeker55 on 2008-06-17
I have just got Utorrent working under wine, can someone please tell me how I can set up a static ip and forward Utorrent's port in Ubuntu.

PS: I have done this in windows..

---

### Post by rlzyoner on 2008-06-17
Shouldn't you use your router to forward ports ?
I generally just check out the NAt section of my router interface and port forwarding is located somewhere there

---

### Post by seeker55 on 2008-06-17
I cannot seem to access the router interface here, in windows it was just typing in '127.0.0.1' but that doesnt seem to work..

---

### Post by rlzyoner on 2008-06-17
127.0.0.1 is your loopback address

From a terminal type route -n and this should bring up the default gateway of your router (with the flag UG)
Then type this into the address bar of the browser and that should access your router

---

### Post by superprash2003 on 2008-06-17
its usually 192.168.1.1 .. if you still have problems please post your router model no

---

### Post by seeker55 on 2008-06-17
Now I could access my router interface, but how do I set up my static ip?

---

### Post by rlzyoner on 2008-06-17
What type of router are you using ?
Each router's interface and menues are different but mine for example, at the interface, follows this process
Network -> NAT -> Edit

Then there's a section to enter the IP addy and the port number

If you can't follow, post your router brand and I'll try jot down some directions

---

### Post by seeker55 on 2008-06-18
My router is the Aztech DSL600EW, Thanks for all the help.

---

### Post by superprash2003 on 2008-06-18
here's how you port forward for your router [http://www.portforward.com/english/routers/port_forwarding/Aztech/DSL600EW/default.htm](http://www.portforward.com/english/routers/port_forwarding/Aztech/DSL600EW/default.htm) .. port forward any port no you wish and ensure you enter the same port no in utorrent preferences.. to make sure you have opened your port successfully try this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by seeker55 on 2008-06-18
Yes I am aware of how to portforward but I will need a static IP right? And the static IP guides are only for windows and mac os. [[http://www.portforward.com/networking/staticip.htm]](http://www.portforward.com/networking/staticip.htm])

---

### Post by superprash2003 on 2008-06-18
to setup static ip in ubuntu.. go to system->administration->network and select your adapter and click on properties and there select static ip and enter static ip address there

---

