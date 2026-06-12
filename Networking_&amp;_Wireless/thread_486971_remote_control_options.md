---
title: "remote control options"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by finite9 on 2007-06-28
I want to remote control a Fiesty Gnome laptop standard installation (being used as a server) from another laptop on my network, as well as from work via my router.

I have installed VNC and it works, sort of, but I have the same problem as 100 other people on the forums...it does not refresh the screen.  So, what other options do I have besides VNC??  Im not looking for a solution, although if you know why xvnc4server does not refresh the session properly, then pease tell me!  I just want to know what other solutions exist.

---

### Post by earobinson on 2007-06-28
I think you could do all your server task via the command line so whats wrong with ssh?

---

### Post by t4thfavor on 2007-06-28
Since you asked about vnc I am assuming that you don't want to use the command line. There is a way to connect a remote X session over an ssh tunnel. I have never had success with remote X through ssh tunnels though. Alternatively you could use xdmcp which is generally deemed non-secure. I guess it boils down to ease of use, or security. Other than those options I don't really know of anything else. 

You could try webmin, which is a web based management console for your linux box (sort of like a wireless router has).

---

### Post by lwh on 2007-06-28
I dont know VNC but insted i'm using Nomachine (NX) to remote control some of my Ubuntu desktops, Its simple to install using deb packages and is working using ssh.
try to have an look on [www.nomachine.com](www.nomachine.com)

The cool thing about Nomackine is the Guest application is advalible for both linux and windows and the windows version can run from a USB-STIC :-)

---

### Post by finite9 on 2007-06-29
i already have ssh working, and this does satisy most of my needs, but sometimes, I want to use a graphical application remotely, as it is easier than having to remember or learn the CLI commands for that app.  I have VNC working over ssh as well, but the refresh problem makes it unusable.

I have heard of Nomachine before, but isn't it proprietary software?  I remember vaguely that it got very good comments from users, but I would prefer a GPL solution.

---

