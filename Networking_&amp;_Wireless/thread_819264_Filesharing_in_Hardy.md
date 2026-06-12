---
title: "Filesharing in Hardy"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by StooJ on 2008-06-05
I've been using Samba for a few years now and it's done the job nicely, since I have a cross platform environment (Windows, Mac, Linux).

However, I use Ubuntu about 80% of the time and am running into problems when using samba for linux-to-linux transfers.

For example, I upgraded from 7.10 to 8.04 a couple of nights ago and used rsync to back up my home directory my fileserver. Although this mostly worked, there were dozens and dozens of errors when rsync tried to chgrp on the server.

Samba seems to be the default filesharing protocol on Hardy (which I found pretty strange) but I'd like something that supports owners & groups properly.

Any suggestions?

Ideally I'd like to set up two sets of filesharing protocols on my server, pointing to the same locations. Connect to the Samba shares when using Windows or OS X, but using NFS or something else when connecting via Ubuntu. Is this possible/a good idea?

Many thanks all.

---

### Post by linux6994 on 2008-06-05
I have file sharing in Ubuntu working really well. I have samba and nautilus shares configured. After installing system-config-samba adding the shares was easy. You can give this configuration a try. Good Luck

---

### Post by StooJ on 2008-06-05
Can you preserve ownerships over Samba though? That's the problem I'm running into.
Samba works fine for most things, but for backing up my Home partition I can't preserve my file ownerships, which is no good :(

---

