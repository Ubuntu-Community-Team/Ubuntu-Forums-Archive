---
title: "RDP connection refused after removing ..."
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by Woody@N87 on 2008-07-26
I've been using RDP for a long time going from my linux machines to a Dell 700m running Windows XP pro SP2.  I connect to it from both inside an outside the home network and have with success for a long time.  Since several folks were logging in at different times we had a PC Anywhere program installed which we we're no longer using.  I removed it from the windows computer.  Now the RDP doesn't work from either inside our outside the network which leads me to believe that there is a setting on the computer that got changed in the removal process.

The firewall is turned off

Remote Desktop is on

Remote Assistance is on

The admin user name has not been altered in any way, the connection doesn't seem to get to the point of looking for a user or password anyway.
I've tried connecting with windows and linux both, same result.

I can ping the computer (from inside, the router doesn't allow pinging from outside)

It seems that the issue is a setting in the XP machine. Does anyone know of a setting somewhere that the PC anywhere program may have changed during the de-installation?

---

### Post by Woody@N87 on 2008-07-29
For  anyone watching this one, I located the problem.  Removing PC Anywhere also removed the peer to peer networking from the host computer which is why I couldn't connect.  I put in the Windows installation CD, navigated to the networking components and re-installed peer to peer networking, this solved the problem.
   Mike

---

