---
title: "remote desktop 8.04 from 10.5"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by stefansjs on 2008-07-15
I'm trying to remotely access my Ubuntu (specifically Ubuntu Studio 8.04) computer from a Mac running 10.5.  So far I've been completely unsuccessful in finding a client that will actually connect.  I've tried Chicken of the VNC, as well "Screen Sharing" (built into Mac 10.5).  Both of them seem to time out when connecting to my computer.  I've tried SSHing to my Ubuntu computer to change the remote desktop settings, but nothing seems to help.  My Remote Desktop settings are:

[LIST]
[*]Allow other users to view your desktop - checked
[*]Allow other users to control your desktop - checked
[*]Ask you for confirmation - unchecked
[*]Require the user to enter this password - has occupied both states
[*]Only allow local connections - unchecked
[*]use an alternative port - unchecked
[*]Require encryption - has occupied both states
[*]lock screen on disconnect - checked
[/LIST]

Am I likely having trouble with the client side or server side?  Does anybody know any good vnc clients for mac that they know works to connect to ubuntu?

Thank you

---

### Post by jimv on 2008-07-15
Are you logged into the Ubuntu machine when you are trying to connect from the Mac?

---

### Post by stefansjs on 2008-07-22
I'm logged in through ssh, but not locally.  Will that cause a problem?

---

