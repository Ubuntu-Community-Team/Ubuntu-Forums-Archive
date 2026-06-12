---
title: "Problem with Gnome and XDMCP"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by MGMorden on 2007-06-07
Ok, I'm running into some issues.  My setup is as follows:  Microsoft Windows XP running VMWare Server.  On a VMWare Virtual Machine I am running Ubuntu Linux 7.0.4 Desktop.  Using bridged networking between the two.

The install goes well.  Networking works on the VM, and I can use it ok from the VMWare Management Console.  That being said, it's somewhat sluggish with the emulated display.  "Remotely" connecting to the Linux machine with an X11 server on my Windows machine would yield a much more responsive system.  So I go into the Login Screen configure, enable remote logins.

I load up Cygwin with X11 onto the Windows machine.

I start the Cygwin server with the following:

X -fullscreen -query 192.168.0.15

The X server starts, connects to Ubuntu fine, and brings up the login screen.  Problem is, from here, if I login, nothing Gnome-based will work.  If I leave it as a Gnome session and login, it accepts the password, then just hangs.  If I set it to "failsafe terminal" I log in and get my xterm window.  From here I can launch firefox and several other non-Gnome apps just fine, but if I try to launch gnome-session or any other Gnome program it just sits there doing nothing.

Anybody have any ideas about this one?  Thanks.

PS I'm running 7.0.4 but also tried 6.0.6 with the same results (only upgraded to 7.0.4 b/c I though it might fix this problem).

Mike

---

