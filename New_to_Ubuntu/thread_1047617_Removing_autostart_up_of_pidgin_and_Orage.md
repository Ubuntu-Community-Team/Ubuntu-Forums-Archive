---
title: "Removing autostart up of pidgin and Orage"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by tomsax on 2009-01-22
I really want to remove pidgin and Orage.  I dont want them but I they clutter things up and dont help me.

When I go into autostarted applications I see that these programs our listed to start up automatically

amsn
Network Manager
Power Manager
Check about new hardware drivers ( available for the system)
Print Queue Applet
Update Notifier

But there is no pidgin or Orage, so how do I get rid of them?

I know how to add and remove programs, thats how I put aMSN on there (thank you for that) but I dont know how to remove something that isnt there in the first place!

---

### Post by gettinoriginal on 2009-01-22
right click applications and check edit menu, then make sure they are checked to show up in Applications.

---

### Post by DariusS on 2009-01-22
Open Synaptic and do a search for them, then uninstall. this is the most thorough way to uninstall things if you know what to look for. Alternatively, try: 
```
sudo apt-get autoremove pidgin
```
this syntax should work for any installed app, given that it was installed through the repo's. (I'm not positive on any other circumstance).

Hope this helps!

---

