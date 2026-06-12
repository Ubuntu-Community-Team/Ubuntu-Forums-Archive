---
title: "Samba Usershare and Force User"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Solomoriah on 2008-07-24
I'd like to arrange matters so that usershares are under the influence of "force user = owner_of_usershare".  I can't figure out how to do this... %u is the username associated with the logged-in user account, not the owner of the share.

The problem I'm seeing is that files created by guest users aren't properly accessible to the usershare's owner.  I'm using a usershare to move non-work related files from my work machine (Fedora Core 4) to my home machine (Ubuntu Hardy) and it's rather inconvenient to have to do "sudo chown" all the time.

On a related note, I can't access files on my Fedora Core systems Samba drives from my Ubuntu system, but it works fine the other way around...

---

