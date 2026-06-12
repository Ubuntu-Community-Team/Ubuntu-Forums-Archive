---
title: "Trouble authenticating with AD (and Avahi?)"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by r-mo on 2007-06-06
I'm following the [winbind how-to]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") and everything's working great until I get to testing the changes to nsswitch.conf with getent.  All this does is return the local users nothing from AD.  Any suggestions on where to go from here? I can see everyone using wbinfo just not in passwd and group :(

On a possibly related note.  I'm not sure whether it's avahi doing this or some other mysterious force but the workstation keeps on losing the domain and search domain I set (doing it either with network manager or editing resolv.conf).  How do I either configure or disable avahi?  I was going to remove it but edubuntu-desktop depends on it :S

---

