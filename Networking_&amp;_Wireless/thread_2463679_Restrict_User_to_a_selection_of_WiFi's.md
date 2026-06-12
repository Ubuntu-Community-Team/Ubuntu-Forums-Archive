---
title: "Restrict User to a selection of WiFi's"
date: 2021-06-16
forum: Networking &amp; Wireless
---

### Post by cgrauer on 2021-06-16
I recently took the responsibility for the student's Ubuntu computers of my son's school. I'm IT professional but not too familiar with ubuntu. I would like to ask if the following scenario is possible and how:
- We have several WiFi access points in the school with different SIDs and Keys
- I want the default user (i.e. students) to be able to connect to these WiFis
- but I want them not to be able to connect to other WiFis (especially to their private hotspots...)!
- other users (like teachers) should still be able to connect to any WiFi.

I already found a solution to restrict all WiFi connections and to require the admin password to connect. But the computers are used by many teachers and they don't know (and shouldn't know...) the admin password, but still they and their students should be able to connect to the school's WiFis. 

Is that possible with Ubuntu?

---

### Post by TheFu on 2021-06-16
Anything is possible with effort and a little scripting.  Can't say that I understand the issue or that I use wifi much.

Nobody needs to know any admin password to connect to a network, unless you've done something odd. For situations like this, I'd setup a *radius server* to control network access .... or a VPN, if using wifi now that everyone knows wifi isn't secure and hasn't been secure the last 20+ yrs.  If the VPN is always-on and no networking will work without out, then that would effectively prevent access to other networks.  Do you intend for a student NOT to use any network at home too? That would be a result.  Hard to meet covid home-school requirements with that limitation.

I do not know how to allow connections to some wifi, but not others. I'll sleep on that a bit.  I certainly wouldn't use network-manager.

---

