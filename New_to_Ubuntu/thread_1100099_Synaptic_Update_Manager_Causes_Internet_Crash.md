---
title: "Synaptic Update Manager Causes Internet Crash"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Happyisgood on 2009-03-18
Hi, I recently started having this problem after I changed routers (I now use a Linksys160n.) Whenever I try to run Synaptic Update Manager it lasts about 20 seconds then the internet crashes.  I have to manually reset my wireless.

I'm open to any suggestions (I was thinking it might be some messed up port forwarding issue that I'm not aware of.) Any help would be great.

Thanks!
Happy

---

### Post by Happyisgood on 2009-03-18
I really hate doing this... butttt... I have to bump this

---

### Post by Happyisgood on 2009-03-19
I tried deleting the internet from my remembered networks and reconnect again.  It still doesn't work.

---

### Post by Happyisgood on 2009-03-19
I keep trying different things, if you guys need any more info that might help let me know... I'm willing to try ANYTHING

---

### Post by mocoloco on 2009-03-19
Have no idea, but what are you doing when it happens?  If you're installing things, try installing from the command-line and see if it still does it.
Also try running synaptic from the command line, with "gksu synaptic".  It might give some output as to what's going wrong.
Also note the time it happens, then look through your log files (System -> Administration -> System Log).  I'm not knowledgeable enough to tell you *which* log mind you :), but look at the latest output of all of them, see if anything looks useful.

---

### Post by Happyisgood on 2009-03-19
Well what I do is...

Boot in Gnome

Alt + F2

update-manager

Install updates

Then between 5 and 10 seconds later my internet is gone!

---

### Post by Happyisgood on 2009-03-20
Ok, I decided to try a variant of the updater

update-manager -d

UPGRADE DISTRO

It fails the same way, but crashes at a random point, I can provide screenshots if you want, or if theres an error log I can quote let me know!

---

### Post by krzysz00 on 2009-03-20
A /var/log/syslog would be nice (copy to home directory after crash, then post)

---

