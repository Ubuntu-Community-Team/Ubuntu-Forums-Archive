---
title: "Can't &quot;update-manager -d&quot; over ssh?"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by smontanaro on 2009-04-10
I have a virtual host web server which I can only access via ssh.  I'm trying to update from
Intrepid to Jaunty using "update-manager -d".  That starts off ok but eventually pops up
a dialog box which reads:

[INDENT]
Upgrading over remote connection not supported

You are running the upgrade over a remote ssh connection
with a frontend that does not support this.  The upgrade
will abort now.  Please try without ssh.
[/INDENT]

Is there another alternative?  I don't have access to any physical hardware, so I can't pop
in a Live CD or anything similar.

Thanks,

---

### Post by bodhi.zazen on 2009-04-10
[https://help.ubuntu.com/community/IntrepidUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20(Recommended](https://help.ubuntu.com/community/IntrepidUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20(Recommended))

---

### Post by bodhi.zazen on 2009-04-10
> **bodhi.zazen said:**
> [https://help.ubuntu.com/community/IntrepidUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20(Recommended]("https://help.ubuntu.com/community/IntrepidUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended"))

Jaunty is in beta right now and I would hold off until the release unless there is some upgrade you can not live without. Especially w/ your set up.

---

### Post by smontanaro on 2009-04-10
Thanks.  do-release-upgrade -d seems to be working.  I wonder why update-manager didn't mention
it as a specific alternative.

---

