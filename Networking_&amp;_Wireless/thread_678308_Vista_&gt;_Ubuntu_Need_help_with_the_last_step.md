---
title: "Vista &gt; Ubuntu: Need help with the last step"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2008-01-25
Hi,
My home network is pretty much sorted; there are five PCs, four running various versions of Kubuntu and one running Vista Home Premium. Occasionally I bring my work WinXP  notebook home. Networking is a mix of cable and wireless. 

We're using "simple file sharing", which is all we need. 

[LIST]
[*]Vista > my XP notebook sharing works fine
[*]Linux (Kubuntu) PC > Vista work fine
[*]**Vista PC to a Linux PC does not work**
[/LIST]

Vista Network Discovery lists the Samba netbios names, but trying to access them results in Windows error 0x80070035, "Network Path not found".

The other strange problem is that I cannot ping any of other linux PC's IP addresses from the Vista PC

Anyone have any ideas about what else I can troubleshoot, given that I have pretty much exhausted advice found here and elsewhere so far?

Thanks

---

### Post by GuiGuy on 2008-01-25
> **GuiGuy said:**
> 
Anyone have any ideas about what else I can troubleshoot, given that I have pretty much exhausted advice found here and elsewhere so far?


Nevermind; I shut down everything and rebooted it all, including the router. Vista shared file access to the Linux PCs is now working. :redface:

Technology is wonderful. When it works

---

### Post by JCMS on 2008-01-25
Really? I'm getting the same error when trying to acess XP from Vista

---

### Post by GuiGuy on 2008-01-25
> **JCMS said:**
> Really? I'm getting the same error when trying to acess XP from Vista

I've had the error a couple of times before, but can generally resolve by 


[LIST]
[*]Rebooting the router
[*]repairing the vista network connection
[/LIST]

The above assumes that Network discovery is configured correctly on Vista and that Netbios network access is enabled(?)

As a last resort, and again I am assuming that there's nothing wrong with what M$ likes to call "Check your settings", 

[LIST]
[*]goto the device manager and UNINSTALL the network card
[*]Uninstall the driver as well but make sure you have a copy handy for the re-install
[*]shut down the PC
[*]reboot the router
[*]restart the PC
[*]re-install & reconfigure the network device.
[/LIST]

The purists will probably freak when they read the above, but it has often got me out of trouble, 

You may also care to check
> 
If creating the same username and password on both XP and Vista, can you
access now?

Cases: Vista networkingCases: Vista networking 2) If browsing in Vista
network, receive Network error: error code 0x80070035 - The network path was
not found. ...
[http://www.chicagotech.net/netforums...opic.php?t=356](http://www.chicagotech.net/netforums...opic.php?t=356) - Similar pages

chicagotech.net :: View topic - Vista: The Network Path was not found
The Vista laptop when I > > have XP Pro loaded says it cannot access
\\Edward. Detail shows error code > > 0x80070035 The network path was not
found. ...
[http://www.chicagotech.net/netforums...83bdd7](http://www.chicagotech.net/netforums...83bdd7) 1c5ab4


Cheers

---

### Post by d3n0 on 2008-05-03
Chek if you can access your ubuntu (Linux) box over ip. Type i.e. '\\192.168.2.10' (your ip address of course). If that works Then open (right click on notepad for example and execute it as admin) c:\windows\system32\drivers\etc\hosts and add 

'your ip'   'name that appears in networks'  i.e.

192.168.2.190   d3n-desktop

---

