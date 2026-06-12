---
title: "ssh directory"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Greslore on 2008-11-14
Is it possible to have SSH use a directory other than .ssh?  A symlink is not a an option for this.

The reason:  I use LDAP auth, and home dirs get created when a user logs in.  Those home dirs get regularly deleted via script, hence I need to use a static directory for .ssh instead.

---

