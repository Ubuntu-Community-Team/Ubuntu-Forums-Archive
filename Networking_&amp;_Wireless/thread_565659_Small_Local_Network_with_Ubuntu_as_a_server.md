---
title: "Small Local Network with Ubuntu as a server"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by Peter Alien on 2007-10-02
Hello, i want to make a local network with Ubuntu Linux 7.04 as a Server and 5 PC Clients and a Router with Internet Access, but i don't know how to configure the Ubuntu to make that.
The Server will run Ubuntu 7.04 and the other PCs will run WinXP Pro.

And Ubuntu has to run a database application (Access or MySQL).

Can someone help me with that ?




I'll really apreciate...
Many many thanks.

---

### Post by peabody on 2007-10-02
A simple solution would be to install the ubuntu desktop cd and then use firestarter to share the internet connection from the ubuntu machine.  All you have to do after that is install apache2, and phpmyadmin and you'd be set.

---

### Post by Jussi Kukkonen on 2007-10-02
> **peabody said:**
> A simple solution would be to install the ubuntu desktop cd and then use firestarter to share the internet connection from the ubuntu machine.  All you have to do after that is install apache2, and phpmyadmin and you'd be set.
Peabody, he has a router -- I don't see why he'd want to route all traffic through the server... Or why he should use a firewall software to share internet connections... Care to explain?


Peter Alien, you need to tell us what exactly you want to use the server for -- can't help you otherwise. 
MySQL is easy:[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
MS Access on the other hand is Microsoft software. You can guess twice whether MS has made a linux version.

---

### Post by Peter Alien on 2007-10-02
Well...the Server is for at least this 3 things:


1) to run a database application... maybe with MySQL (in the future) as a database (3 persons have to put data in it at the same time)


2) for the 5 PC Clients to have Internet.


3) To manage a remote computer that is far away :)

---

### Post by Jussi Kukkonen on 2007-10-02
> 1) to run a database application
Check.
> 2) for the 5 PC Clients to have Internet.
If you have a router, you can just connect all of your machines to it, right? Even consumer routers should have a firewall and DHCP (if you want to use that for the client PCs)...
> 3) To manage a remote computer that is far away
You'll need to provide more information than that...

---

### Post by peabody on 2007-10-02
> **Jussi Kukkonen said:**
> Peabody, he has a router -- I don't see why he'd want to route all traffic through the server... Or why he should use a firewall software to share internet connections... Care to explain?

I missed that part of his post so I assumed he wanted to use the Ubuntu server as the router.  Firestarter has an Internet connection sharing feature that's easy to setup, which is why I recommended it.

---

### Post by Jussi Kukkonen on 2007-10-03
> Firestarter has an Internet connection sharing feature that's easy to setup, which is why I recommended it.
Ahh, I see. Thanks.

---

### Post by Peter Alien on 2007-10-05
Ok but tell me just one thing more, if i put a Database Application in Ubuntu (Server Machine) the other 3 persons can input data to it just like that? I mean the application can be accessed by all 3 at the same time? Ther are no problems with the App or the Server because of that?


About the subject that refers to manage a computer that is far away... i mean something like "Windows Remote assistant" or "VNC", something that i could use in Ubuntu to control a remote computer.


Many thanks

---

### Post by Kitsun on 2007-10-05
Ubuntu comes with a program called vncviewer which serves as a client for VNC.

Press ALT-F2 and type in vncviewer and than click run, type in the IP of the computer you want to connect to, and than password.

---

