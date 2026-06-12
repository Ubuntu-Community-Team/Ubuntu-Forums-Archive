---
title: "Error Opening Synaptic Package Manager"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Andavane on 2011-04-20
I got this message yesterday when opening the synaptic.
I was in the middle of another job and forgotten the procedure for reporting bugs.
It's the first time this has happened with me.
It was a one-off occurrence; a restart fixed it.

It seems to be a variation on this thread:

[http://ubuntuforums.org/showthread.php?t=1183329&highlight=Error+Opening+Synaptic+Package+Manager]("http://ubuntuforums.org/showthread.php?t=1183329&highlight=Error+Opening+Synaptic+Package+Manager") 

Here OS = Ubuntu 10.10

---

### Post by Locke_99GS on 2011-04-20
Typically that error occurs when another package manager is running. Periodically your system may automatically check for updates without your interaction. When this hapens to me, I usually wait a couple of minutes and try again.

Sometimes this happens when no package manager is running, but the last time one was run it didn't release it's lock. If you are *absolutely certain* that no other active process is using that lock, you can remove it yourself. This doesn't happen often, usually only when a package manager errors out ungracefully, or faults.

---

### Post by Andavane on 2011-04-20
Thanks - will try to remember if it happens again.
But how do you remove the lock?

---

### Post by Locke_99GS on 2011-04-20
Delete it :)

---

### Post by Andavane on 2011-04-21
Sorry for appearing obtuse, but
...Where's the lock?  :confused::confused:

---

### Post by plucky on 2011-04-21
> **Andavane said:**
> Sorry for appearing obtuse, but
...Where's the lock?  :confused::confused:

It tells you in the error message.

**/var/lib/dpkg/lock**

---

### Post by Andavane on 2011-04-21
OK so you navigate to there and delete that.
As long as you're rock-sure that synaptic isn't already running.
Got it.
Cheers.

---

### Post by Blasphemist on 2011-04-21
I believe that the update manager and during installation the software manager may also lock the packages.

---

### Post by Locke_99GS on 2011-04-22
Update Manager and Software Centre both use the apt package management system.

---

