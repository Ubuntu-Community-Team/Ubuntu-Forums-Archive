---
title: "package cannot upgrade."
date: 2011-02-01
forum: New to Ubuntu
---

### Post by beew on 2011-02-01
Synaptic lists the package "upstart" as upgradable, but when I tried to mark it I get the error message

> upstart:
  Breaks: libc6 (<2.12.1-0ubuntu10.2) but 2.12.1-0ubuntu10.1 is to be installed


I looked up the package libc6, version 2.12.1-0ubuntu10.2 is installed Does it mean that upgrading "upstart" would require a downgrading of libc6?

Since both packages ("upstart" and "libc6") come from the repository Maverick-upates/main, am I correct to think that this is a problem with that repo itself and has nothing to do with my particular source configuration?

---

### Post by hansolo4949 on 2011-02-01
I think the problem MAY be stemming from an update that was just released. Did you just update or auto-update today? strangely, the update that might be causeing this, won't install on my system. Now, i'm am no expert on this, so I might be completely off base.

EDIT: I get the same error message, and I don't have the update installed, so it isn't that. I will try apt-get updating, and try it then, since it needs some repository that it apparently can't get.

---

### Post by [Snc] on 2011-02-01
> **beew said:**
> Synaptic lists the package "upstart" as upgradable, but when I tried to mark it I get the error message



I looked up the package libc6, version 2.12.1-0ubuntu10.2 is installed Does it mean that upgrading "upstart" would require a downgrading of libc6?

Since both packages ("upstart" and "libc6") come from the repository Maverick-upates/main, am I correct to think that this is a problem with that repo itself and has nothing to do with my particular source configuration?

I would read this as:

> *you have* libc6 ( *that requires* <2.12.1-0ubuntu10.2) *installed,* but 2.12.1-0ubuntu10.1 *has to be* installed *to make this work*Quirks in repos are always happening, but mostly fixed within 24h or so ... I had Natty (11.04 in a virtual machine) not startable, waited for a day or so and updated the system from grub rescue, then it worked .... [B]kudos to the folks, that do that possible ;)

[/B]edit: just like hansolo4949 here, i got some update problems when I tried it .... well, that's (maybe) the third time this month, but 11.04 RC is coming close, so I guess it is normal... kudos to the above mentioned people (again). It should disappear soon. From my point of view, just don't "Partially upgrade".... ever ... :)

---

### Post by beew on 2011-02-01
Yes, this is today's update. I haven't upgraded it yet, I couldn't and wouldn't even try. :)

---

### Post by FighterZP on 2011-02-02
Same problem - unable to install ubuntu ((

---

### Post by FighterZP on 2011-02-02
Problem solved

[http://newyork.ubuntuforums.org/showthread.php?p=10420893](http://newyork.ubuntuforums.org/showthread.php?p=10420893)

---

### Post by hansolo4949 on 2011-02-02
Yep, with the latest updates, now everything works as planned. This is one of the things I loe about Ubuntu, lightning fast (in comparisin to Windows) response to any bugs/quirks/driver incompatibilities.


Why noone in the "normal" computer world knows about Ubuntu, and it hasn't taken over Windows, is just awful;)

---

### Post by beew on 2011-02-03
Turns out I have forgotten to activate the "Ubuntu proposed" repository. Checked the box in Synaptic and reload and all the upgrades went through. Thanks to everyone who has responded to the thread.

---

