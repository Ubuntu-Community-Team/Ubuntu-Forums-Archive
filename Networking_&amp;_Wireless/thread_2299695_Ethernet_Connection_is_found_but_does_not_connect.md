---
title: "Ethernet Connection is found but does not connect"
date: 2015-10-20
forum: Networking &amp; Wireless
---

### Post by Delta_jom on 2015-10-20
Hello! 
I had installed 64-bit ubuntu to an old computer, hooked it up to the network through ethernet, and everything went fine for a while. Then one day someone unplugged it and when I plugged it back in it says that you have been disconnected from the internet whenever I tried to connect. It allows me to attempt to connect but it never succeeds. The connection is going through a hub that is connected to another computer running 32-bit puppy that is having the same problem. 

I will take all the help I can get, for I am extremely new to concepts such as this, and linux operating systems in general.

Thank you
D_j

---

### Post by SeijiSensei on 2015-10-20
Where is your router located in this arrangement?  The hub should be connected to the LAN side of the router and all the machines wired to it.  The only way to move traffic through the Puppy machine is with NAT masquerading configured on that machine, but that's not worth if it you can connect directly to the router.

---

### Post by Delta_jom on 2015-12-02
Thanks for the help, tried it in a different port and it didn't work, but then I switched the cable and both worked fine. Just a faulty ethernet cable.

---

