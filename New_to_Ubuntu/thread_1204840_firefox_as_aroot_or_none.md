---
title: "firefox as aroot or none"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-05
im just curius...
when i run an application like firestarter and after that i run firefox will firefox run as root too?

i dont think so but it would be good to hear someone's else opinion....

---

### Post by JillSwift on 2009-07-05
Nope. The program that starts apps like firestarter as the super-user (*gksudo*) would also have to be called to start up other apps to run them as the super-user, too. Otherwise the apps just start up in your current session.

---

### Post by Paqman on 2009-07-05
Nope. Although since Firtestarter runs as root make sure you close it down as soon as you've used it. Also, Firestarter is no longer being actively maintained, so you might want to consider switching to a more up-to-date firewall configuration tool such as Gufw.

Running Firefox as root would be an enormous security booboo, btw.

---

### Post by heyyy on 2009-07-05
> **Paqman said:**
> Nope. Although since Firtestarter runs as root make sure you close it down as soon as you've used it. Also, Firestarter is no longer being actively maintained, so you might want to consider switching to a more up-to-date firewall configuration tool such as Gufw.

Running Firefox as root would be an enormous security booboo, btw.

thank you both
could you recommend me some quick settings on gufw?

---

### Post by Paqman on 2009-07-06
> **heyyy said:**
> thank you both
could you recommend me some quick settings on gufw?

The default settings are perfectly secure as you have absolutely no services listening on any ports. You'd only need to bother with firewall rules if you installed something which listened (eg: some kind of server package)

---

