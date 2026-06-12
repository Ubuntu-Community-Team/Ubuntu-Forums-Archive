---
title: "Internet wireless problem"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by naarkhoo on 2009-11-13
I made a small network which the server is Winxp and client is on ubuntu 9.04
i set DCHP on Automatic on network manager,

i ve selected the correct security key, and entered the correct key, 
My network manager indicate that wireless connection has established connection ( and become blue), but i am still unable to surf the web wirelessly, the web pages will not load up.

---

### Post by JBAlaska on 2009-11-13
Try making a manual connection in NM using the IP, gateway, netmask and DNS you allocated in XP

---

### Post by naarkhoo on 2009-11-13
> **JBAlaska said:**
> Try making a manual connection in NM using the IP, gateway, netmask and DNS you allocated in XP

thank you for answering.
As Xp said, 
> 
       Connection-specific DNS Suffix  . :
       Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
       Physical Address. . . . . . . . . : 00-53-45-00-00-00
       Dhcp Enabled. . . . . . . . . . . : No
       IP Address. . . . . . . . . . . . : 89.165.81.99
       Subnet Mask . . . . . . . . . . . : 255.255.255.255
       Default Gateway . . . . . . . . . : 89.165.81.99
       DNS Servers . . . . . . . . . . . : 89.165.0.13
                                           89.165.0.14
       NetBIOS over Tcpip. . . . . . . . : Disabled

I am not sure, but 
I set "89.165.81.100"  subnet "255.255.255.255" gateway "89.165.8199" and DNS is "89.165.0.13"  but still i have the problem

Is my setting right?

---

### Post by hal10000 on 2009-11-13
> I am not sure, but
I set "89.165.81.100" subnet "255.255.255.255" gateway "89.165.8199" and DNS is "89.165.0.13" but still i have the problem
 
If this is your local area network, then your ip-address iw wrong. If you get the same or a similar address when using dhcp, then your dhcp server is configured wrong in local networks the addresses must be either 10.X.Y.Z or 192.168.X.Y or between 172.16.X.Y and 172.31.X.Y

You have to start the dhcp server on your XP machine (or at least somewhere in your lan)

The address you have setup looks like you've got it from your poviders dhcp server, but if you have a local network and want to use dhcp, you have to set uo a dhcp server in your local net

---

