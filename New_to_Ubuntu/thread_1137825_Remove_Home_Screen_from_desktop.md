---
title: "Remove Home Screen from desktop"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by apoorvs on 2009-04-25
I installed Ubuntu Eee 8.04 over XP on Thursday. Since then I have upgraded to 8.10 and then onto 9.04. In each version, I have tried to find remove the home screen:

[IMG]http://i43.tinypic.com/9vigk6.png[/IMG]

How do I remove this application/applet and get to the desktop?

---

### Post by ohzopants on 2009-04-27
First you need to find out what process is displaying.  You're going to have to use ps -A to find it.

Once you identified the program displaying the home screen, search through synaptic to find which package installed it and remove that package.

If you don't want to actually uninstall it, it's probably being invoked by your "session". Check the session manager to disable start up programs you don't want (this program could actually be running as a service, in which case you would go to "services" to disable it).

---

### Post by apoorvs on 2009-04-27
Thx

---

### Post by SentientFluid on 2009-04-27
I think [this may help you out]("http://forums.geteasypeasy.com/viewtopic.php?f=10&t=1053&sid=c74833af2c2ffd051000e0ac453dd2e3").

It shows how to enable Full Desktop mode.

---

