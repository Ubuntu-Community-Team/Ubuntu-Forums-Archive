---
title: "smbclient"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by gpalmia on 2009-01-29
Hi all!
I am working with ubuntu server 8.4.
I have installed the packages samba-common and smbclient.
In the LAN there are other machines: one with ubuntu S.O. too, same version (the Master Browser), other with windows XP and Vista.
The command:
```
nmblookup - M -- -
```
gives back to me the correct IP address of the master browser.
Also the command:
```
nmblookup - T "*"
```
gives back correct IP addresses of all Computer of the LAN.
The command:
```
nmblookup -SA <IPAddress>
```
return the correct NetBios names of all the PC of the net;

When I try to enter in the shared folder with smbclient command I have some error.
In fact if I type:
```
smbclient - L <PCName>
```
**the system tries for three times to connect itself with an IP address that does not exist in the LAN and then it communicates to me the impossibility to carry out the logon**.
But if I type the command:
```
smbclient - L <IPAddress>
```
or
```
smbclient //<IPAddress>/SharedFolderName> -U <username>
```
I see the SharedFolders or I can work with them.
After all it is as if from somewhere in the net something gave to the client the mistaken information with regard to the correspondence between the NetBios name of the PC and its IP address.
Some suggestion?

---

### Post by Dedoimedo on 2009-01-29
You don't need netbios on xp or vista ...
What are the non-existent IPs, btw?
Dedoimedo

---

### Post by gpalmia on 2009-01-29
Thankyou very much for your answer!
All the machines on the LAN has address like 192.168.1.X and when I type the command:
```
smbclient -L <PCName>
```
the system tray  to connect with
212.48.8.140:445
212.48.8.140:139
212.48.8.140:140
then show me the error message: Error NT_STATUS_ACCESS_DENIED

---

