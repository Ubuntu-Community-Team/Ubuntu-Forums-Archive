---
title: "pptpconfig doesn't keep routes after reconnecting (persist) a dropped tunnel"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by dqqdrake on 2008-03-20
I've set up pptpconfig to connect to my work network so I can access my home machine at work.  Sometimes the connection gets dropped for some reason so I have the Persist switch set from the pptpconfig GUI.  It does work - after a connection is dropped, it would automatically reconnect.  However, once it's reconnected, it can't reach any other computer on the work LAN other than the PPTP server.  I checked routing table and realized that after reconnecting, it's missing the entry
192.168.220.* * 255.255.255.0 U 0 0 0 ppp0
(192.168.220.0/24 is the work LAN).

If I stop the tunnel and reconnect manually from the GUI, it will have the route entry correctly.  I can also manually add the route to make it work.  But those won't help if the drop of connection happens when I'm at work.  

The routing option on the GUI is "client to LAN".  I even manually added the route in the "Edit network route" section on the GUI.  But that didn't help.

Is there a way to fix this?  I don't mind tinkering with the config files if I know which one is responsible.

---

### Post by babulal on 2008-04-08
Do you got the solution? I have the same problem. 
I need the solution,,,, Pleazzzzzzzzzzzzzzzzzzzzzzz.

---

### Post by farahbod on 2008-04-10
> **dqqdrake said:**
> I've set up pptpconfig to connect to my work network so I can access my home machine at work.  Sometimes the connection gets dropped for some reason so I have the Persist switch set from the pptpconfig GUI.  It does work - after a connection is dropped, it would automatically reconnect.  However, once it's reconnected, it can't reach any other computer on the work LAN other than the PPTP server.  I checked routing table and realized that after reconnecting, it's missing the entry
192.168.220.* * 255.255.255.0 U 0 0 0 ppp0
(192.168.220.0/24 is the work LAN).

If I stop the tunnel and reconnect manually from the GUI, it will have the route entry correctly.  I can also manually add the route to make it work.  But those won't help if the drop of connection happens when I'm at work.  

The routing option on the GUI is "client to LAN".  I even manually added the route in the "Edit network route" section on the GUI.  But that didn't help.

Is there a way to fix this?  I don't mind tinkering with the config files if I know which one is responsible.

Check /etc/ppp/ip-up.d/ConnectionName
```
vi /etc/ppp/ip-up.d/ConnectionName
```
You must place your routing command in there!

---

