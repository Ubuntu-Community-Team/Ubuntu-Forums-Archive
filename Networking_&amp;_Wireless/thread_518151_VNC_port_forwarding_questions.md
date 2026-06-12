---
title: "VNC port forwarding questions"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2007-08-05
I've not used VNC yet (terminal server client), but am going to start testing it out this week and hopefully make a video of it in action.

Let's say you have a private network with three PC's attached to a router (all of them running Ubuntu), and the router is attached to a cable modem.  From my understanding so far, in order to establish a remote desktop session with any of these PC's on this network, they must have:

- Remote Desktop enabled
- Port Forwarding on the router must be configured for each PC

How do you change the default remote desktop listening ports on Ubuntu in order to set distinct port forwarding rules for each PC?

---

### Post by misconfiguration on 2007-08-06
In order to forward ports, you have to do that from your routers config.

In order to change ports, you'll have to manually edit the daemon's config file for each particular service.

Say you want to change SSH (port 22) to 2242

You'd have to edit /etc/ssh/sshd_conf and manually change the listening port to 2242 from 22. 

So some research may be involved for you.

---

