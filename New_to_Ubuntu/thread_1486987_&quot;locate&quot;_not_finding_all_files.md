---
title: "&quot;locate&quot; not finding all files"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by npnufn on 2010-05-18
Why is locate omitting / missing files that I know are there?

The "locate" utility may not find all your files, if you chose to have an encrypted home directory during setup. That's deliberate per Bug [#372631]("https://bugs.launchpad.net/ubuntu/+source/mlocate/+bug/372631") . 

But if you're like me and you do want to have all your files be searchable with locate, edit /etc/updatedb.conf to exclude "ecryptfs" in the PRUNEFS= variable assignment.

sudo vi /etc/updated.conf

Refresh the locate database by deleting the old one, and run "updatedb":

sudo rm /var/lib/mlocate/mlocate.db
sudo updatedb

It should keep refreshing properly on its own after that.

---

