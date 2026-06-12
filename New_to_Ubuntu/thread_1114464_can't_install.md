---
title: "can't install"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by DarinB on 2009-04-02
on a friends hardy machine i cant install telepathy haze and get the error when trying to update packages
kathy@kathy-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
not sure what to do 
i installed empathy and it asks for backend for protocols
i got off the forum to add telepathy-haze as the protocol
she uses aim and i messed up her pc by removing pidgin to add the latest version and now i can't even add pidgin back with out getting broken packages from pidgin for hardy any ideas on how to get her IM working again
i don't care what application i use

---

### Post by Cypher on 2009-04-02
You need to prepend "sudo" to your command, since "apt-get" is an administrative command.

---

