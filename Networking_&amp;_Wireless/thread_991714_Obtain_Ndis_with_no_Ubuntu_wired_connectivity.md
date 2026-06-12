---
title: "Obtain Ndis with no Ubuntu wired connectivity?"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by carusoswi on 2008-11-24
So, I rebuilt my system over the weekend.  Got carried away restoring other features (actually, chasing down a bad data cable that was driving me (and my system) nuts), forgot to load my driver for my Belkin N1 adapter.

So, now, I'm in a remote location with no wired internet.  Loading the driver for the adapter was a piece of cake in XP, but from Ubuntu, I need to download some software (NDIS??) in order for my Ubuntu installation to offer me the opportunity to load the driver.

Anyway to do this when Ubuntu can't reach the 'net?

I can get online in XP, but doubt there is a way to get what I need there.  

Suggestions appreciated.

Caruso

---

### Post by spcwingo on 2008-11-24
If the system is a dual boot with xp you can get it going.  All you have to do is boot up xp and go here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Download the three files for your version of Ubuntu.  Boot Ubuntu back up, mount your windows partition and double-click first ndiswrapper-common.  It will open gdebi package installer and tell you that the version is available through synaptic.  Click OK, then click install package.  Then do the same for ndiswrapper-utils.  Lastly do the same for ndisgtk.  Now you can install your windows driver.  To do so just go to System>Administration>Install Windows Drivers.  Let me know if that gets the job done.:)

---

### Post by carusoswi on 2008-11-24
Communicating via my Ubuntu wireless connection at the moment.  Your instructions worked like a charm.  Now, I have those files on my system in case I ever find myself in this situation again.
Thanks for the help.

Caruso

> **spcwingo said:**
> If the system is a dual boot with xp you can get it going.  All you have to do is boot up xp and go here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Download the three files for your version of Ubuntu.  Boot Ubuntu back up, mount your windows partition and double-click first ndiswrapper-common.  It will open gdebi package installer and tell you that the version is available through synaptic.  Click OK, then click install package.  Then do the same for ndiswrapper-utils.  Lastly do the same for ndisgtk.  Now you can install your windows driver.  To do so just go to System>Administration>Install Windows Drivers.  Let me know if that gets the job done.:)

---

### Post by spcwingo on 2008-11-25
Glad I could help a fellow M$ refugee.

---

