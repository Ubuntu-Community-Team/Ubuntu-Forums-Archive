---
title: "Nasty Update Problems in Natty"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Krishna Murthy on 2011-07-28
[B]Installation :[B]Maverick upgraded to Natty. Everything fine.

**The Problem :** Heavy rains created network problems. So chose the next best thing. Software sources--other--select best server. All tests done and server in a neighboring country chosen. Reloaded. OK.

Update manager shows all the applications again which I have already installed from my previous server. Tried 5 times. Checked and rechecked.

It doesn't make sense to reinstall all the applications just because I chose to update from a different server.

**Conclusion :** Natty or perhaps all the versions of Ubuntu does not have a clue about installed applications+versions and the OS does not make a list of all installed applications.

This is not the sign of a good Operating System.

Do and check it for yourself.

Any suggestions/solutions are welcome.

---

### Post by cavh on 2011-07-28
I think you'll find it's proposing updates to the installed applications, not to reinstall the applications themselves. Post a screenshot to show us what's troubling you.

---

### Post by coffeecat on 2011-07-28
> **Krishna Murthy said:**
> It doesn't make sense to reinstall all the applications just because I chose to update from a different server.

It wouldn't, but you don't. The deb packages you download from one server are identical to those you download from any other and are cached in your /var/cache/apt/archives folder. So, if your system is re-installing the same packages 5 times over, something has gone wrong in your system. Nothing to do with packages in the repository servers.

Is your system re-downloading or re-installing the same packages?

---

