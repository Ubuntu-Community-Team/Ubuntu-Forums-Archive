---
title: "Azureus - synchronization between Linux and Windows"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by DracoPsycho on 2007-04-26
Did anyone try to synchronize Azureus between Linux and Windows? I did link linux's azureus config to windows' but there's a problem with path's format. Anybody got any idea? I would use Wine eventually, but as long as I know java doesn't work there...

[I don't know if it's right place to post this but didn't know where to put this.]

---

### Post by dercaS on 2008-01-04
An old post, but it describes perfectly the problem I'm having too.
The problem is of course in the azureus.config file.

The solution as i see it is to have a batchfile or script that under startup of Azureus, automatically replaces the path settings for downloads and torrentfiles in the azureus.config file. Depending on what OS you use.

Does anyone know any easy CLI based application that can do this?
Example replace "string" with "string2" in file.name?

---

