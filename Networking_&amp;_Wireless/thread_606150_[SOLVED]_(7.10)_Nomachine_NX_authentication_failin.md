---
title: "[SOLVED] (7.10) Nomachine NX authentication failing after changing  SSH port"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by evilregis on 2007-11-07
I'm about to hand over a computer to my dad this weekend with the latest Ubuntu on it.  I'm running the latest Ubuntu on my notebook at home.  My dad lives a fair ways away and I wanted to set up a secure way for me to remote into his machine should he have a problem.  But for the purpose of this, I'm working locally, both machines on the same network.

I installed SSHD, Nomachine NX client, node and server on my dad's computer.  I left everything default at first.

I then installed the client on my machine.  I set up the connection and it worked like a charm.

The next step was to change the default port so it wasn't hanging out in such an obvious manner.  On my router I forwarded port 8080 to my dad's machine (for me to try going out and coming back in), changed my /etc/ssh/ssh_config and /etc/ssh/sshd_config to port 8080 and restarted SSH.

Then I made the same changes to SSH on my dad's computer and restarted the daemon.  I also made the changes in /usr/NX/etc/node.cfg and /usr/NX/etc/server.cfg and restarted it as well.

I tried connecting (both using the internal IP and by going through the router) again and I get "Authentication failed for user (username)".

What's weird is if I enable user DB and add/enable myself, I can connect again... as the account I created/enabled.

Any idea why it fails authentication after simply changing SSHs operating port?

---

### Post by evilregis on 2007-11-07
Solved:  While I changed my SSHDAuthPort to 8080, it appears I didn't remove the # that commented it out.  So it was still trying to use the default 22 to authenticate.

---

