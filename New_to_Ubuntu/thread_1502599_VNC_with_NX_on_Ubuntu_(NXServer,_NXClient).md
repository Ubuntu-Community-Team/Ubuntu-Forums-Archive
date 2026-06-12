---
title: "VNC with NX on Ubuntu (NXServer, NXClient)"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by swaroopgr on 2010-06-05
Hi,

I'm trying to use VNC to connect from a windows to to a remote Ubuntu machine (on the same LAN). I've installed NX server, NX Client and NX node on the target machine running ubuntu (The machine that I need access to). I have openssh installed and running here (port 22 is open)

I DO NOT want a new session. I need to continue with an existing session. I've installed the NX client for Windows on my machine and am using the VNC option to get a connection to the NX server.

The problem: I have the NX client installed on Windows. When I connect from windows to the ubuntu machine, The authentication works fine. However, the target machine refuses the connection with a "Unable to connect. Connection refused (111)" error.

Constraints: I do not have physical access to the target machine but can only open up a terminal with SSH (To let you now I do not have physical access to the GUI currently)

Can someone please let me know what I'm missing here? Is it a problem with firewalls? (I don't think so. Because I can still SSH into that machine). Please help

---

### Post by cariboo on 2010-06-05
Is there a user logged into the remote computer? If it's just sitting at the gdm screen, you won't be able to log in.

---

### Post by swaroopgr on 2010-06-05
Yeah. There is a user logged into the Ubuntu system.

I tried TightVNC too. I could see my Ubuntu screens. However, it wouldn't recognize any mouse movement / clicks inside that area.

---

### Post by jtratcliff on 2010-07-08
There's a known bug w/ VNC & Xorg when using the compiz window manager.... something to do with how XDamage is implemented... The VNC connection works but the screen isn't redrawn...

 After opening the unresponsive VNC connection try temporarily switching to metacity over a separate ssh connection:

$ metacity --display=:0.0 --replace

switch back w/

$ compiz --display=:0.0 --replace

---

