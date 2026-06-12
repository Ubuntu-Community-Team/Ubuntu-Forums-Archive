---
title: "Firestarter Inbound connections"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by NorgeNerd on 2007-02-15
I've installed Firestarter, but cannot get it to allow the other machines on my network to connect.  I've tried every conceivable policy, but nothing changes.  (except that once in a while, I get a login prompt instead of a "Network path not found" msg.  The login prompt doesn't recognize any login credentials)  I have always been able to connect to my other machines from the Linux box, but there's no reciprocity.  My Mac at least generates an entry in the event log.  My PC doesn't even seem to warrant a log entry.  And, yes, I've clicked on the Mac log entry and created a very permissive policy directly from it.  No change.  Thanks much for your ideas.

---

### Post by Floppyjoe on 2007-02-15
Do you have to have the users on the computers that you are trying to connect from also have accounts on your linux box to be able to connect?

---

### Post by NorgeNerd on 2007-02-15
All users have accounts on all machines (the usernames and passwords differ, but everyone can log on anywhere).  And, as I mentioned, I occasionally get a logon prompt.  It always fails though.

I'm now thinking the Samba configuration file needs to be edited to allow Samba connections from the network.  I remember reading that somewhere.  And I don't remember reading that Firestarter ever touches the Samba file.  Any insight?

---

### Post by Floppyjoe on 2007-02-15
You probably need to have the users from the other computers to also have an account on the machine you are trying to connect to with the same names and passwords.

---

