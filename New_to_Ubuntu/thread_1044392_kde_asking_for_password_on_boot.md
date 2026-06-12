---
title: "kde asking for password on boot"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Jynxx on 2009-01-19
Hey all. I installed kde and deleted gnome. When I boot, KDE asks for a password. There is only 1 user account on my computer. Is there a way to set it so it boots into KDE without asking for user password?

---

### Post by azr on 2009-01-19
If you're using the 8.10 (kde4)

Applications -> System -> System settings -> Advanced Tab -> login manager -> Convenience tab  -> check the enable auto login

The reason the put the warning sign is for security reasons; the following quote is from the help file on the relevant section. 

> Important
Please think more than twice before using these options. Every option in the Convenience tab is well-suited to seriously compromise your system security. Practically, these options are only to be used in a completely non-critical environment, e.g. a private computer at home.

---

### Post by Jynxx on 2009-01-19
That did it, thank you!

---

