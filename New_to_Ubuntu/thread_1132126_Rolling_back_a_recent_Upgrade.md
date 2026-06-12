---
title: "Rolling back a recent Upgrade"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by jlhaslip on 2009-04-21
Had an Upgrade of the system a day ago and now I can't access a Web Service. And I can't recall the specific Updates, either. Is there a Log of the recent Updates available someplace on the system? Is it possible to "undo" those updates? 
Seems the Gov't of Canada only supports 7.10 but for some reason, however, I had used their site on Saturday just fine running 8.10 Ubuntu.

And thanks for any replies.

---

### Post by Sidewinder1 on 2009-04-21
Can you back-up your data to an external and reinstall 7.10? There may be a way do do what you ask in Synaptic or possibly just boot into the older kernel at the initial boot selection page. Just some suggestions as I haven't tried any of them...

---

### Post by Eisenwinter on 2009-04-21
I'm pretty sure you can downgrade the packages, but I'm not entirely sure as for how to do it with APT.

Go into /var/cache/apt (I think that's where apt keeps its' downloaded packages), and just manually install the ones you want with dpkg.

---

### Post by jlhaslip on 2009-04-21
I really don't want to down-grade to 7.10 since the Service *was running* using 8.10 until a System Upgrade the other day. (timezone software changes or something, I do not recall exactly what the upgrade was about)
All I need to do is remove the recent changes (system upgrade) and revert the 8.10 to the way it was last week. Then it will likely work again, I'm thinking.

*edit*

Semantics. Maybe I should say that I am looking for a way to remove/rollback an "update" instead of an upgrade.

---

### Post by Sidewinder1 on 2009-04-21
Sorry, the 7.10 suggestion was my mistake; i misunderstood your original post. A thousand pardons. :-) I don't really have the answer that you're looking for. However I believe the time zone update, to which you are referring, was probably named "tzdata" if you go into Synaptic--->File--->History and find the latest instance of tzdata that will at least tell you when...Perhaps someone more knowlegeable than I can take you from there.
HTH
Side

---

### Post by bodhi.zazen on 2009-04-21
There is no easy way to roll back the changes.

What problem are you having ? Perhaps it would be easy to fix. Can you give details ? service, error messages , logs ?

---

