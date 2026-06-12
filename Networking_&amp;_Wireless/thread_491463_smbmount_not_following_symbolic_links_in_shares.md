---
title: "smbmount not following symbolic links in shares"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by strag on 2007-07-03
Alright, I've got some samba shares set up for home folders on my ubuntu server, my windows systems can hook up to the shares fine and browse through everything without any problems.

The problem occurs when using my ubuntu laptop to link into the samba shares. I'm using smbmount to mount the share as just using Network from the Places menu won't bring up the shares properly (it sees the server, connects to the server, doesn't see any shares, and using connect to server just ends up in it sitting there for a while and then not being able to connect). Anyways, the problems with other methods aren't the issue. Smbmount connects the share just fine, but it's unable to follow symbolic links that have been made on the server end, it just says that what the link points to simply doesn't exist. As I said, my windows systems are able to use the links just fine, so does anybody have any suggestions as to what might be going on here?

---

