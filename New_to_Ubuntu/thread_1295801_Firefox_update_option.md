---
title: "Firefox update option"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by Loki57701 on 2009-10-19
Why in the linux version of firefox is there no "check for updates" option like on mac and win?

---

### Post by anonymous_user on 2009-10-19
You need root permissions to update Firefox.

Also with Linux, you most likely use the package manager to update your programs (Firefox included). In Ubuntu the package manager is Synaptic (apt-get).

---

### Post by 2blue on 2009-10-19
You have to mark off for "back-port updates" in Synaptic Update Manager to get new versions of software. If you don't, you only get updates for the old versions until next version of Ubuntu comes.

---

### Post by Loki57701 on 2009-10-19
I know how to update firefox, I was just wondering if there was a reason there's no option in the browser iteself to update it. Couldn't mozilla devs add the option and then "if" the user decided to update then the system would prompt for the password?

---

### Post by aysiu on 2009-10-19
It's because it has been deactivated. Software updates are supposed to happen through the package manager and not through the application itself. That is the blessing and curse Linux has, and Windows and Mac do not.

If you prefer the have the application update itself, "install" the binary from the Mozilla website:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Loki57701 on 2009-10-19
Thats interesting, thanks guys, I'll check the backports option and then head over to that website.

---

### Post by egalvan on 2009-10-19
First off, make sure you are not confusing

up**date**

with

up**grade**


The first is making "updates" to the minor version,
such as

3.0.1 --> 3.0.2


The second is making "upgrades" to the major version,
such as

3.0 --> 3.5


Up**dates** are handled by the package manager in order to keep track of dependencies (among other things).

Windows has no "package manager" so the updates/upgrades can be (and are) handled directly by FireFox.

Up**grades** are usually not permitted in Ubuntu releases due to stability reasons.
 Releases, especially LTS ones, are tested with  major versions of software, and making major changes can cause "regressions", or instability (bugs and crashes).

But as always in the *nix world, one has choices.
And one can choose to up**grade** their software packages.
Almost always this means a bit more work than simple up**dates**,
in order to keep users aware of the situation.

Remember one of the Unix Philosophies...

"Unix doesn't keep you from doing stupid things, because that would also keep you from doing clever things"

---

### Post by Loki57701 on 2009-10-19
Thanks egalvan, I'll keep that in mind.

---

