---
title: "Reverse SSH trouble"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by jbradshw on 2008-08-04
This is more of a ssh question in general and not really specific to Ubuntu, but since I'm using Ubuntu I thought I'd just post it in here.

I'm new to reverse SSH tunneling and I've looked at how-to guides but I can't seem to use the tunnel I've created to get back through it. Here's the scenario:


Client WORKCOMPUTER is behind company firewall running Ubuntu 8.04. I have a Snapgear router at home which runs off linux which we'll call HOMEROUTER. I have HOMECOMPUTER running Windows (which sits behind the router) which I want to be able to ssh back through to my work computer.

On WORKCOMPUTER I ran this:

ssh -nNT -R 1100:HOMEROUTER-IP:1100 WORKCOMPUTER-IP

It prompted for my current user name@WORKCOMPUTER-IP's password. I entered that and it now just sits there, which from what I've read, is normal.

Now I'm able to ssh as root into HOMEROUTER from HOMECOMPUTER on port 22 and that gets me to a prompt locally on the router.

Now I tried entering this command from HOMEROUTER's prompt:

ssh -p 1100 localhost

But I get Connection refused. I also replaced localhost with router's IP and I still get connection refused.

Am I missing something? I'm hoping it's something simple that I'm overlooking.

---

### Post by kevdog on 2008-08-04
Id have to look into it specifically (I did a while ago), but something about forwarding connections.  I can get back to you later today (8 hours or so if you need help).

I think this link tells about the entire story:

[http://gentoo-wiki.com/TIP_SSH_Reverse_Tunnel](http://gentoo-wiki.com/TIP_SSH_Reverse_Tunnel)

---

### Post by jbradshw on 2008-08-04
Thanks for the guide, and I figured it out. I had the localhost and destination hosts swapped - I think the guide I read previously was in error. Anyways that helped out - thanks!

---

