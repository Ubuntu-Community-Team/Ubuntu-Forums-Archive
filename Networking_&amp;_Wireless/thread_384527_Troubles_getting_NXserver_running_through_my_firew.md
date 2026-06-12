---
title: "Troubles getting NXserver running through my firewall"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by ViAo on 2007-03-14
have port 22 forwarded to my ubuntu box, and i can ssh to it via the lan and over the net.
(using putty)

i can get to the nxserver via the lan but NOT the net

i get this error.



it connects, authenticates (authentication complete) then goes to negotiating link parameters.....

and then i get a pop up that says could not yet establish the connection, do yo uwant to terminate.

Here is the details from the error (with the obvious info replaced with XXX)


```
Info: Proxy running in client mode with pid '2600'.
Session: Starting session at 'Tue Mar 13 14:47:56 2007'.
Info: Connecting to remote host '192.xxx.xxx.xxx:5004'.
Info: Aborting the procedure due to signal '15'.
Session: Session terminated at 'Tue Mar 13 14:48:47 2007'.
now :5004 seems to change everytime i try and connect.
```

waht am i doing wrong?
      

I'm guessing that SSH is just for secure authentication and the other ports are similar to how VNC uses a new port for each connected display.


i Opened a few ports for the proxy and X11, like 5000 - 5010 and 6000 - 6010. I'm not sure how nice NX is about closing displays when it's done, so i thought i might require more or less ports open than that open if I reconnect often.
 
help! :)

---

### Post by ViAo on 2007-03-14
ok now here is something wierd.  i have DMZ'd my ubuntu box on my firewall and i get the same error when trying to connect.

---

