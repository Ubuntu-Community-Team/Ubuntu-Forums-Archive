---
title: "Internet sharing host-ubuntu client-windows"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by marbig on 2006-11-05
Totally new to this and hoping I might get a kick start. To simplify:
[LIST]
[*]Before: My computer (host) and my children's computer(client) cable networked and sharing my internet connection. Both windows XP Home and plugged into a router, router cabled to ADSL modem.
[*]After: Host computer (mine) now has dual boot. When on Ubuntu I have internet connection (many thanks to forum members). Client computer does not have internet connection.
[/LIST]
How do I go about getting this please? Not so fussed about file sharing. But I believe I have to get Samba if I want to use the printer (connected to client). Is this correct?

---

### Post by dmizer on 2006-11-06
well, there are lots of howtos for internet connection sharing.  you'll need to set up ubuntu as a dhcp server via firestarter or the like.

but i'm confused.  you say you have a router.  if that's the case, why is it necessary for you to do internet connection sharing?  the router should be handling all the traffic rather than a single computer.

if you just want to use the printer attached to the client computer, you will not need to install samba.  samba is a file sharing server.  ubuntu will be able to connect to your clients computer without any configuration, just use the printer configuration wizard.

---

### Post by marbig on 2006-11-06
> but i'm confused. you say you have a router. if that's the case, why is it necessary for you to do internet connection sharing? the router should be handling all the traffic rather than a single computer.Sorry dmizer.. router should read ethernet switch.
So do I still > set up ubuntu as a dhcp server via firestarter or the like.?
Thank you for your reply.

---

### Post by dmizer on 2006-11-06
ah ... it's a switch then.

try this: [https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28network%29%7C%28translation%29%7C%28address%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28network%29%7C%28translation%29%7C%28address%29)

i've never done it this way, but it looks to be more simplistic than trying to configure everything in a gui like firestarter.

---

### Post by MacPC on 2006-11-06
Well, why don't you consider getting a router? It's easier to maintain and  It will relief your PC from the extra burdun of duty of ICS and it works better.

To use the printer, go to System->Administration->Printer->Click New printe. In printer type, select Network Printer, and select CUPS Printer (IPP)enter your URL. It then will asks you to enter printe model, driver etc. then you will be all set to go.

MacPC

---

### Post by MacPC on 2006-11-06
Sorry, my mistake.


Please disregard this line. "To use the printer, go to System->Administration->Printer->Click New printe. In printer type, select Network Printer, and select CUPS Printer (IPP)enter your URL. It then will asks you to enter printe model, driver etc. then you will be all set to go."

Forgot your printer is connected to a Windows machine.  You should use Windows Printer (SMB) instead of CUPS.

MacPC

---

