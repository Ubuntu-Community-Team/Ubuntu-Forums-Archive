---
title: "[SOLVED] Having problems remote desktop into ubuntu machine from xp machine"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by dean20007 on 2007-08-27
Hi 

I am major problems remote desktopping into my ubuntu machine from an xp machine on my local network.

I have followed the how-to's and have enabled remote desktop on the ubuntu machine. I have installed tightvnc viewer on my XP machine, but when I try and connect to the IP address of the  ubuntu machine it says it can't connect.

I can ping both machines from the other. 

Things I have tried:

Sharing a folder on the ubuntu machine - Result XP initially found the machine but told me I didnt have permission to access it.
Tried sharing a folder on the XP machine - Result Ubuntu tried to open folder but claimed it couldnt read all the contents.

Can anyone help

Thanks

---

### Post by raijinsetsu on 2007-08-27
Are you connecting through a firewall, or are they on the same subnet?

---

### Post by nanofilter on 2007-08-27
what version of Ubuntu are you running?

- When connecting to your XP machine from Ubuntu, make sure to temporarily disable Firewall on the XP machine so you have no obstacles troubleshooting your access.

- Make sure the folder you are trying to access on the XP machine is Shared and that your user have the right access perimissions (Read, Write, etc.).

- Make sure you have no firewall running in the background on your Ubuntu machine.

Pinging does not give you much since ping it's using different protocol (ICMP) than e.g. file sharing (e.g. SMB) or Remote Desktop (RDP) or VNC (RFB).


desh

---

### Post by dean20007 on 2007-08-27
Thanks for the replies 

I am on the same subnet. I am running fiesty 7.04. 

I am pretty sure I have met all the suggestions you have made but still no joy

Any other ideas.

Additionally I only really wsh to remote from XP to Ubuntu if that helps at all

Thanks for your help

---

### Post by dean20007 on 2007-08-29
Hi Folks

So I have managed to get into my Ubuntu desktop via my XP machine, but something is still not right. I left my ubuntu machine with just the desktop (no app windows open) but when I remote in I get a web browser opened with a page I had been looking at previously. Also I can't click anything I can move the mouse and it controls the cursor remotely but no clicks etc seem to work

Any ideas??

---

### Post by dean20007 on 2007-09-04
The problem was using vino? I updated to a differnet version of VNC and it worked fine. Cheers for the help in getting it sorted guys

---

