---
title: "upgrade to 7.10 from 7.04 turns on firewall, rejecting servers"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by rocket777 on 2007-10-21
AFter upgrading, I found that my servers would not function because the upgrade left the firewall on with no entries. This caused all my servers (remote desktop, and sshd) to reject connections.

Just thought I'd mention this. I don't know how it got turned on, and I don't think it was on before the upgrade. The easiest way to turn it off is with firestarter, where there's a single on/off button.

I don't need it since I'm behind a firewall already via my router. Others might not be as secure. Turn it off at your own risk.

---

### Post by jlombs on 2007-10-21
Hey - I am a bit of a noob and I think that this firewall software might be causing some issues for a bunch of us (DNS traffic too)

Can you get me more details on how to turn it off?

---

### Post by rocket777 on 2007-10-22
The firewall is a set of rules that let you restrict access to your servers in a variety of ways. If it is not set correctly, it can make many of your services fail.

Look under applications/internet. See if you have firestarter installed. If not, add it via add/remove apps. 

Then, look at this page:

[http://www.fs-security.com/docs/status-page.php](http://www.fs-security.com/docs/status-page.php)

Once it is running, click on the stop firewall button. If this fixes your problems, then you know that the firewall is what is causing your problem.

You can look at the status tab and if there is an events count under serious, you probably have some kind of blocking going on. In my case, I found events for my 2 servers.

I don't know, yet, how to make it stay off, as when I come back from hibernation it's back on.  I'm still studying the online manual (mine doesn't seem to have a working help command).

I'm looking for how to make a rule that allows all connections from my local (192.168.*.*) lan, as that's where I connect to my ubuntu system from my laptop running XP. If you find that the firewall is your problem, I'm sure you can find some help by others more knowledgable than me on how to set it up so it both protects yet doesn't shut down your servers that you want active.

---

### Post by jlombs on 2007-10-22
Thank you Rocket777 - I will check this out when I get home

---

