---
title: "NX client cannot connect to VNC server successfully"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by phasenew on 2007-11-16
system: ubuntu gutsy
desktop: gnome
VNC server: vino
NX server: free version
NX client: on linux or windows

problem: 
NX client can connect to the desktop session successfully, but cannot connect to VNC server. 
The VNC server on the same machine as NX server is set up with GUI: system->preference->remote desktop, boxes are checked, password is set.
the NX clients on both windows and linux machines are configured according to instructions on the nomachine.com. The server is set as: 123.345.567.890:22 under the general tab, the desktop is select as VNC and settings are: 123.345.567.890:0, authentication is put in.

apparently the client can connect to NX server and get authenticated, and a black window pops out, but an error message in the black window says "cannot set RFB password. please contact your system administrator", after clicking the "OK" button, the client is closed.

I tried the port of the NX server with 22, 5900, 2200, and whatever I found on the web, also tried the display number from 0 to 5, all them just do not work. 

what does that RFB password mean? why its password cannot be set? thanks a lot for helping.

---

### Post by DeFrancoj on 2007-12-02
I encounter same using mac client.

---

### Post by sirspiddy on 2007-12-19
I had the same issue.
From this article [http://www.nomachine.com/ar/view.php?ar_id=AR06E00469]("http://www.nomachine.com/ar/view.php?ar_id=AR06E00469")
I found part of the solution.

<Quote> What do I need  to run VNC sessions?

You need to ensure that both vncviewer and vncserver, are installed on each of your NX node host machines.  Please note that installation of vncserver is required to provide vncpasswd, used to set the password to access VNC desktops.</Quote>

All I did was install vnc4-common which contains the file /usr/bin/vnc4passwd.

I now can connect to my ultravnc windows boxes using port 5900.

Hope this helps

---

