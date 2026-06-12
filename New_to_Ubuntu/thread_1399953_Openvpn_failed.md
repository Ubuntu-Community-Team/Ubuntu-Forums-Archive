---
title: "Openvpn failed"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by rosegal on 2010-02-06
Stopping virtual private network daemon(s)...                                 
*   Stopping VPN 'openvpn'                                              [ OK ] 
 * Starting virtual private network daemon(s)...                                
 *   Autostarting VPN 'openvpn'                                          [ OK ] 
 *   Autostarting VPN 'server'                                           [fail] 

ok this is what i got when i tried connecting openvpn between two pc using ubuntu.this is my client...the pc i used as the server succeeded when i restarted the openvpn but my client failed and i din know whats the reason...neway i open the daemon file and got these :

[ Feb  6 16:43:42 unknown-laptop ovpn-openvpn[15684]: TCP: connect to 10.xxx.x.xx:1194 failed, will try again in 5 seconds: No route to host ]

do anyone have any idea about it?i am new to these so i cant figure out whats the mistake...or whats the solution...How can i make the server working...Pls help....

---

### Post by The Cog on 2010-02-06
The error message says what your problem is - it is trying to connect to 10.xxx.x.xx and there is no route to it. I know that 10.anything is not an address that will ever be accessible over the internet so either you are trying to connect a VPN across a provate network, or you just have the wrong address in the configuration file for the server.

Are you trying to connect across the internet? If so, 10.x is definitely the wrong address. If 10.s is the internal private address of the OpenVPN server, then you need to connect to the public address instead, and arrange for UDP port 1194 to be forwarded to 10.x.x.x.

---

### Post by rosegal on 2010-02-08
yes m trying to connect over the internet..so now i must connect to the public address is it?to do that i need to do ip forwarding...can i know how to arrange for UDP port 1194 to be forwarded to 10.x.x.x ?

this 10.x.x.x is the public address rite?

---

### Post by The Cog on 2010-02-08
Yes. Over the internet you will need to connect to the public address. This can be found by visiting a site like whatsmyip.com with yoru browser. 

The incoming packets to your public address UDP port 1194 need to be forwarded to your internal IP 10.x address port 1194 of course. This is done by configuration inside your internet router. I can't help with that - how it's done will be very specific to the make of router you have.

---

