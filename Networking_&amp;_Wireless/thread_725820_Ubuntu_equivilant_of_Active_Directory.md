---
title: "Ubuntu equivilant of Active Directory?"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by BlackRoseBud on 2008-03-16
I'm only familiar with using Ubuntu on my personal laptop computer.  I want to create an Ubuntu server for users and computers to login on and share settings throughout all workstations in a domain.  Basically an Ubuntu equivalent to the Windows 2000/2003 Active Directory.  Anyone know how I would go about doing this?

---

### Post by ruy_lopez on 2008-03-16
The last time I looked (a long time ago) the solution was very involved.

Take a look at this, hopefully things are easier these days.
[https://help.ubuntu.com/community/ActiveDirectoryHowto]("https://help.ubuntu.com/community/ActiveDirectoryHowto")

---

### Post by koenn on 2008-03-16
> **BlackRoseBud said:**
> I'm only familiar with using Ubuntu on my personal laptop computer.  I want to create an Ubuntu server for users and computers to login on and share settings throughout all workstations in a domain.  Basically an Ubuntu equivalent to the Windows 2000/2003 Active Directory.  Anyone know how I would go about doing this?
looks like that link ruy_lopez gave you is about integrating ubuntu systems into an existing (Windows) AD Domain.
You're probably after something like this :
[https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn)
That should handle account management, authentication, etc. but doen't offer GPO-like functionality for user/vomputer configuration.

maybe you should also have a look at this :
[http://users.telenet.be/mydotcom/howto/linux/migration03.htm](http://users.telenet.be/mydotcom/howto/linux/migration03.htm)

---

