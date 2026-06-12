---
title: "Multi user networks."
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by linuxftw on 2007-06-26
How would I go about creating a network using Ubuntu, where each user's files are stored on a server, rather than each local machine?

Thanks in advance :)

---

### Post by Scunizi on 2007-06-26
This might actually be a question for the Server section...  You'd like to create a server where /home is stored for each user.  A LSTP (I think that's the right acronym) server might be what you're looking for.  Each machine on the network would actually boot from the server making the remote machines actually just terminals.  Although I'm not aware how to do it, you might be able to locate each users home on the server using Network File Share (NFS) and configuring your fstab to point to the server and location for each user.  However you'll run into problems with that if you want the ability of each person to be able to log into eny given computer.  There's only one fstab and for this to work with multiple users on one or many computers you'd need to be able to load a specific fstab depending on the user.  On the flip side, if each person only used one specific computer, it might be doable.

---

