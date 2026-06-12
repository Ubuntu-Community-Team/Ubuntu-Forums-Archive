---
title: "Is there any way to update the synaptic package manager?"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by LxxRyuzaki on 2009-08-03
Because in my synaptic package manager wine is 1.0, instead of 1.1, and I think thing's are easier to install in the synaptic package manager.

---

### Post by running_rabbit07 on 2009-08-03
> **LxxRyuzaki said:**
> Because in my synaptic package manager wine is 1.0, instead of 1.1, and I think thing's are easier to install in the synaptic package manager.

Did you click the reload button?

---

### Post by pedro3005 on 2009-08-03
For new versions of programs appearing on the Synaptic you will have to wait until they're incremented on the servers, which may take some time.

---

### Post by CatKiller on 2009-08-03
Synaptic lists all the versions that are in repositories that you've added. If you want a newer version than is in the repositories you're already using, then you need to add a repository that contains that version.

Wine provide [their own repository]("http://www.winehq.org/download/deb") for new versions.

---

### Post by stoogiebuncho on 2009-08-03
What version of Ubuntu are you running?

---

### Post by snowpine on 2009-08-03
Wine 1.0.1 is the the current stable release, and the correct version for Ubuntu 9.04 Jaunty. If you want an unstable development version, you will have to get it from the winehq.org website, because the Ubuntu developers have decided not to include it in Synaptic (the Ubuntu repository).

---

### Post by LxxRyuzaki on 2009-08-04
I'm running ubuntu 9.0.4, and I couldn't get internet explorer to install. It said I didn't have the newest version of wine or cabextract.

---

### Post by snowpine on 2009-08-04
> **LxxRyuzaki said:**
> I'm running ubuntu 9.0.4, and I couldn't get internet explorer to install. It said I didn't have the newest version of wine or cabextract.

Internet Explorer is the default web browser for Microsoft Windows. For Ubuntu, I would recommend giving Firefox a try...

---

### Post by stoogiebuncho on 2009-08-04
I don't think Internet Explorer works very well with Wine anyway:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=25]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=25")

You might have to resign yourself to using Firefox, Opera, or Konqueror.

---

### Post by kansasnoob on 2009-08-04
I've had some luck following the instructions here:

[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

**Sticky:    HOWTO: New Wine development releases**

---

### Post by CatKiller on 2009-08-05
> **LxxRyuzaki said:**
> I'm running ubuntu 9.0.4, and I couldn't get internet explorer to install. It said I didn't have the newest version of wine or cabextract.

There's a script to install Internet Explorer in Wine, if you really have to. More details [here]("http://www.psychocats.net/ubuntu/ies4linux").

---

