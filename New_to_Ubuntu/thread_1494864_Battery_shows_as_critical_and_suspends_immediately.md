---
title: "Battery shows as critical and suspends immediately after cord is removed"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by Exosus on 2010-05-27
I am running Ubuntu 10.04 on my Falcon NW I/O and whenever I unplug my cord the message "Battery level is critically low" appears and the computer suspends. If I leave it unplugged and bring it back out of suspend, it runs fine for another 2 or so hours, and it doesn't do anything like that on my Windows partition. Anyone have any thoughts on stopping this?

**Just realized I put kubuntu as the header - not intentional. Apologies**

---

### Post by rg_stephens on 2010-05-27
gnome power manager seems to have some bugs.  I've had similar problems from time to time. You could take power manager out of the startup menu, but then you wouldn't be able to suspend at all. 

If you do <alt>+f2 and type *gconf-editor* you can change more functions of power manager. Go to:
/apps/gnome-power-manager/actions
and change *critical_battery* from *suspend* to *nothing*

---

### Post by Exosus on 2010-05-27
That took care of it. Not a clean fix, but honestly I don't especially need my computer to suspend on my behalf - a simple message is fine. Thanks.

---

### Post by MatthewPlanchard on 2010-07-01
Another way to work around this is to go to gconf-editor -> apps -> gnome-power-manager -> general and uncheck "use_time_for_policy".  This will allow you to re-enable automatic suspend and/or hibernate in case you step away from your computer and forget that it's on (which has happened to me on more than one occasion).

---

