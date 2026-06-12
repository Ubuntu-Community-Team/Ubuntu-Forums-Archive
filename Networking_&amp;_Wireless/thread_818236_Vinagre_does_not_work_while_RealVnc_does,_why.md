---
title: "Vinagre does not work while RealVnc does, why??"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by antonluque on 2008-06-04
Hi everyone,

I have a a very weird problem, I have a computer running Ubuntu 7.10 and MythTV, and a laptop with two partitions, Windows XP and Ubuntu 8.04.

I can connect with my laptop to the mythtv computer using RealVNC in Windows, but I cannot do it using Vinagre in Ubuntu. Vinagre tries to connect, but after a couple of second it always displays an error message saying that the connection was closed.

What makes it even more interesting, is that a month ago I could connect with my laptop to the mythtv computer using a previous version of Vinagre, I believe it was 0.3, running on Ubuntu 7.10, but it does not work since I upgraded to Ubuntu 8.04.

Thanks in advance ...

---

### Post by antonluque on 2008-06-04
Any ideas ??

---

### Post by Jose Catre-Vandis on 2008-06-10
I am going to come in and support this thread as I have the same problem. Been using vnc for years to connect to my headless machines on my internal lan. A simple ALT+F2 followed by the command vncviewer "xx.xx.xx.xx:1" gets me to my server (which is set up for resumable sessions with gui and gdm). I can also ssh and ping the machines, no firewall issues.

Using vinagre and entering the same info produces an error about connection closed. Thought this was supposed to make things easier?

---

### Post by Jose Catre-Vandis on 2008-06-11
bump?

---

### Post by Jose Catre-Vandis on 2008-06-13
I guess there are no replies because it doesn't work for anyone ;P

---

### Post by tact on 2008-06-13
Not sure what your problem is but perhaps this snippet of info will help...

Vinagre apparently lacks the ability to connect to RDP or XDMCP.  So if the desktop sharing mechanism of the machine you want to connect to shares via RDP or XDMCP you cannot connect to it with Vinagre.

You can still access through tsclient (the client that was the default before Hardy). 

I think that tsclient is still installed in Hardy.  It is just not present in the menu.  Use synaptic to see if it is installed, install it if not.  

Hope that helps.

---

### Post by Jose Catre-Vandis on 2008-06-14
OK, thanks for that tact. So how does it connect? and what to? Any GUI remoting I do is either through rdesktop (Windows or remote Vbox VMs) or vncviewer (local linux servers), so what is the benefit of having vinagre in the ubuntu desktop if it can't connect to either?

---

### Post by tact on 2008-06-14
> **Jose Catre-Vandis said:**
> OK, thanks for that tact. So how does it connect? and what to? Any GUI remoting I do is either through rdesktop (Windows or remote Vbox VMs) or vncviewer (local linux servers), so what is the benefit of having vinagre in the ubuntu desktop if it can't connect to either?

Vinagre can connect to vnc shared desktops... its a vnc client.

---

### Post by Jose Catre-Vandis on 2008-08-15
Remote Desktop Viewer (vinagre) seems to have fixed itself for me. i can now connect to vnc sessions on my remote computer, with resumablility !

---

