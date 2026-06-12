---
title: "About iptables init script"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by frankabel on 2007-09-14
Hi all,

I just want know why the iptables packages don't come with an init.d shell script as others packages. I hear that exist some security reason about that, even I know that in some old debian version the script was removed, but why? What script or way do you advice me to use in my servers? I had saw lots of ways, but not know what is the most secure.

Just add that would be nice if the sugestion about this issue is accord the new upstart init ubuntu system

Salute
Frank Abel

---

### Post by gpredrag on 2007-09-18
One could put iptables init script in /etc/network/if-pre-up.d and /etc/network/post-down.d.
Those scripts get executed before and after an interface is being brought up or shut down.

More elegant solution would be to use shorewall or some other wrapper around bare iptables commands.

---

### Post by frankabel on 2007-09-19
Thanks for your reply.

I'm a little confuse... that mean that when whatever interface go down my iptables rules go down too? Where can I read about the scripts in those directories that you mention?

Salute
Frank Abel

---

### Post by gpredrag on 2007-09-19
Those would be scripts with regular iptables commands. i.e iptables -A ....
Scripts also receive variables such as $IFACE (which interface is being brought up) $METHOD (start or stop) which you can use and do something clever in your script.

More on that subject: man interfaces.

You can control what happens when interface is being brought down (shut down iptables or not) by (not) placing script in post-down.d. It make sense to erase rules that would be put up again if you bring interface up again.

But, again it is much more flexible to maintain shorewall firewall rules, than those hand made scripts (from my experience) so unless you have some very good reason not to, I suggest you to take some time to investigate shorewall firewall.  It has excellent documentation, and example configurations. As I said it's only wrapper around  iptables, but it makes configuration more manageable, including having it's own startup and shutdown scripts.

---

### Post by frankabel on 2007-09-20
Thanks again!

---

