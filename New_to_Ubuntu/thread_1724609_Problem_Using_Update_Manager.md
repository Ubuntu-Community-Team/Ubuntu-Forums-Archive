---
title: "Problem Using Update Manager"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by Brinner on 2011-04-08
Hello im completely new to Ubuntu i know a lot with windows(if this helps at all) but im having problems with using the update manager first i had problems with an error with /etc/apt/sources.list but through searching this forum i fixed it but now when i run the update manager it says waiting for synaptic to close and just sits there i looked through the system monitor and it wasnt there so can someone please help me. P.s sorry if this is the wrong place to psot i wasnt sure.

---

### Post by Rex Bouwense on 2011-04-08
Welcome to the forums.  You can have only one update program operating at a time.  The Update Manager will not function with the Synaptic Package Manager running.  Merely close the Synaptic Package Manager and you will be able to run the Update manager.

---

### Post by earthpigg on 2011-04-08
hi,

i bet synaptic is still running :)

open a terminal, and enter this to verify:

ps -A | grep synaptic

or: just restart.

i do not recommend using kill or force-closing synaptic.

---

### Post by Brinner on 2011-04-08
> **earthpigg said:**
> hi,

i bet synaptic is still running :)

open a terminal, and enter this to verify:

ps -A | grep synaptic

or: just restart.

i do not recommend using kill or force-closing synaptic.
thanks you such a simple fix of just restarting and i didnt think of it :D

---

### Post by earthpigg on 2011-04-08
> **Brinner said:**
> thanks you such a simple fix of just restarting and i didnt think of it :D

yes. big thing with package managers is that they all demand that they be the only package manager running. if they aren't 100% absolutely certain that some other package manager isn't managing packages, they will refuse to work - for good reason. better safe than sorry. (ever tried installing or uninstalling two or more pieces of software at the same time on windows? it gets very ugly, very quickly. :P )

---

