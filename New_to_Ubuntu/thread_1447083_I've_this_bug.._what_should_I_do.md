---
title: "I've this bug.. what should I do?"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by Rushyang on 2010-04-04
Bonjour guys,

I was facing problem in my ubuntu software center that It displays,

**"Waiting for another software managers to quit."**

it is already reported on [_LAUNCHPAD_]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/464020").


i also can't get ```
sudo apt-get install <package_name>
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```Any solution? 

-Rushyang.

---

### Post by howefield on 2010-04-04
Perhaps you have another package manager running, whether that be apt-get, Software Center, Update Manager, Synaptic Package Manager, Adept Package Manager, ect ect.

You can only have one package manager running at a time.

Try closing all package managers or if that doesn't work, reboot and try again. ?

Maybe you have the update manager applet in the top panel ?

---

### Post by EssexEagle on 2010-04-05
Just worth checking - have you tried already the fixes suggested in the bug report you linked to?

---

### Post by NightwishFan on 2010-04-05
Welcome to Ubuntu Forums Raito-kun. Ensure all package managers are closed and that you are fully up to date.

---

### Post by MichealH on 2010-04-05
You gotta run because this bug will eat you! ;)

Forget that. Have you got a package manager running? Its only allowed one at a time because it locks the shared directory so the other one can disrupt the other... For example I'm Upgrading but I cant install [cowsay]("apt://cowsay/") <-- Click if intrested

---

### Post by Aped on 2010-04-05
reboot ;)

---

### Post by perham on 2010-04-05
try this:

```
sudo rm /var/lib/dpkg/lock
```

and then run the package manager

---

### Post by @rizz on 2010-04-05
Hi,

  I am with Aped REBOOT! (works with a surprising success rate!!!:lolflag:)

---

