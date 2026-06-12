---
title: "Several people trying to view my desktop"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by finferflu on 2006-09-29
Hi all,
I did not know what criteria I should have used to find a solution, so I'm just starting a new thread. I'm sorry about that.

Lately I've been receiving several popup messages a day from VNC telling me that some IPs were trying to view my desktop. Now, I'm a bit worried about that: how do all this number of people get to know my IP? Is there a way I can understand that (and possibly prevent it)? I'm a bit concerned about my security here, am I right in doing so?

Thanks for your time.

---

### Post by crokett on 2006-09-29
They probably know your IP by using a port scanner to see what ports you have open.  

You can move VNC to use a different port other than the default if you have not done so.  You can install and configure a firewall that blocks access to those ports VNC uses.  If you do the firewall you will also need to allow the incoming IP addresses you use.  IT sounds like you should install a firewall anyway. You can look at setting up ssh and using it instead of VNC.

---

### Post by finferflu on 2006-09-29
Thanks for your answer. I actually use only ssh but I have noticed that the vino-server seems to startup automatically everytime. Maybe I should just remove it from the automatic startup, even though I don't know how to do that (since it's not in the System > Preferences > Sessions menu).

Thank you!

---

### Post by motin on 2006-10-08
Quote from: [http://ubuntuforums.org/showthread.php?t=11808](http://ubuntuforums.org/showthread.php?t=11808)

It's about VNC and not VINO, but here are some security notes:

> **Darrena said:**
> Notes:
For added security use your hosts.allow to restrict connections from only localhost so that you must use SSH to connect.

If using a router, redirect TCP Port 22 (SSH) from the internet to your PC so you can connect remotely but you may want to use your hosts.allow or a filter on your router to only allow those connections from a trusted source.

If you are going through a firewall that blocks SSH you can redirect 80 or 443 with iptables.

---

### Post by finferflu on 2006-10-09
That's very useful, thanks for the information!

---

