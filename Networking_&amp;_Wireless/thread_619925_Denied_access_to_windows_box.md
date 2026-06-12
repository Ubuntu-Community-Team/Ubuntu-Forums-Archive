---
title: "Denied access to windows box"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by ardvark on 2007-11-22
I  have 3 PC's on my home network, two are windows XP and one Ubuntu linux. Windows (a) can access files on windows (b) and Linux (c). Windows (b) can access files on Linux (c) and Linux (c) can access files on Windows (b). But neither (b) or (c) can access files on (a). I've tried turning off the firewall on (a), made sure the Shared files folder was indeed showing shared, also checked to make sure some ports were set per info from Microsoft. Also when I try to set up Ubuntu to use the printer on windows (a) I can't see the printer with the printer configuration program. Obviously windows (a) is blocking access but I haven't been able to find where. I know this is probably a windows problem, but I was hoping that maybe someone has seen this before and knows a quick fix.

---

### Post by mellowd on 2007-11-23
What are the permissions on Windows A looking like? Remember you need to look at both file and share permissions

---

### Post by ardvark on 2007-11-23
The file I'm trying to access is C:\Documents and Settings\All Users\Shared Documents. If I right click on it, it does show sharing enabled and theres a message at the bottom of the box that says that Windows Firewall is configured to allow sharing this folder with other computers on the network. The only other thing I see about permissions is under properties and that's set read-only.

---

### Post by mellowd on 2007-11-24
Right click the folder and select properties. You'll see sharing and security at the top. What are the permissions on both?

---

### Post by jonandrews on 2007-11-24
Have a read through my xp/ubuntu network & printing guides at

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

They are for ubuntu novices, but they may well help.

---

### Post by ardvark on 2007-11-24
Well, I've checked that and like I said the Windows "Shared Documents" folder is checked for "Share this folder on the network" and "Allow network users to change my files". I believe there is something more basic blocking access inward to the Windows box. In response to jonandrews, the problem with the printing is that I don't even see a printer available. When I click on the icon for the Windows PC nothing shows up for printers. This works fine on my other Windows PC.

---

