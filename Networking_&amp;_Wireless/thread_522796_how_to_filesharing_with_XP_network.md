---
title: "how to filesharing with XP network"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by guhpraset on 2007-08-11
how to connect an ubuntu box to a XP network? I have the internet working, but failed in file sharing.

Every time ubuntu try to browse the shared files on XP machine, it ask for password while i never set any password.  And so with the xps, they cant see the shared file on ubuntu box. :confused:


Help me please.

---

### Post by aysiu on 2007-08-11
For browsing XP--try an actual Windows existing username and password.

For sharing with XP, watch [this](http://www.youtube.com/watch?v=Ad17kma8rNM).

---

### Post by guhpraset on 2007-08-11
Success, thankyou very much Aysiu, now all the XP PC can access the shared files on ubuntu box. 

Now there still a problem, i cant access the shared files in the XP box (from ubuntu box), it always ask for password that i never set. 

what is the password? How to pass this?

---

### Post by aysiu on 2007-08-11
I don't really know. We don't have XP computers in our household (just Mac and Ubuntu). I'm guessing it'd be a username and password of an existing XP user.

For example, if on XP you log in as *guhpraset* and your password is *vcn29A$n*, then I'd type in *guhpraset* and *vcn29A$n* when prompted for a username and password using Samba.

---

### Post by guhpraset on 2007-08-14
i tried to set password on xp and use it to browse from ubuntu, still fail. 

XP keep asking password... weird. Thankgod this is not so important (yet) for me.

Any other suggestion to try?

---

### Post by bwinfrey on 2007-08-14
It sounds like you need to configure Samba to match your XP Network ID settings.

---

