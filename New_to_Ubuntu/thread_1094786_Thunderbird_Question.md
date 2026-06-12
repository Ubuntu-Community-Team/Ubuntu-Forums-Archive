---
title: "Thunderbird Question"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-03-12
i have two folders that seem to contain my thunderbird data.
~/.thunderbird
~/.mozilla-thunderbird
my email is always running, and they have both been modified today. do i need both these folders? what is the point of having two?

---

### Post by HermanAB on 2009-03-13
See:
Edit, Account settings, Local folders

That will tell you which one is really in use, but i would leave those folders alone!

Cheers,

Herman

---

### Post by mjheagle8 on 2009-03-13
none of the accounts are using .thunderbird
i renamed it, so far no problems noticed. if thre arent any issues within the next week ish i'll probably delete it.

---

### Post by mdebusk on 2009-03-13
> **mjheagle8 said:**
> i have two folders that seem to contain my thunderbird data.

Are you sure both are folders? Is it possible that one is a symbolic link to the other?

---

### Post by presence1960 on 2009-03-13
> **mjheagle8 said:**
> i have two folders that seem to contain my thunderbird data.
~/.thunderbird
~/.mozilla-thunderbird
my email is always running, and they have both been modified today. do i need both these folders? what is the point of having two?

I only have ~/.mozilla-thunderbird folder. This contains all your emails, preferences, extensions and themes. You definitely need this folder. As far as the ~/.thunderbird I have no idea why you even have that, I have never seen that one before on a thunderbird install. I have installed ubuntu on more than a few machines with thunderbird and have never seen that folder.

---

### Post by philinux on 2009-03-13
It changed during one of the upgrade cycles. Thunderbird now sets up it's profile folder as .mozilla-thunderbird on a clean install.

---

