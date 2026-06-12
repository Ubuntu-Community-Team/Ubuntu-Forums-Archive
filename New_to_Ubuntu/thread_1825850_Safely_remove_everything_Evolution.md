---
title: "Safely remove everything Evolution???"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by mikodo on 2011-08-15
Hi,

I have moved everything I need to save from Evolution to Thunderbird (emails, contacts, etc.), and have it accepting POP3 emails from my ISP's webmail. I have read that one cannot remove the Evolution package, without breaking dependencies for the ubuntu-desktop meta-package and to do so, would remove the meta-package.

So, if I keep Evolution around and when I eventually do a new install of Ubuntu 12.04 and use my ~/ partition in the install, I will  have Evolution files in my home. As, I want to use Thunderbird now, and 12.04 will be using it as the default, what can I safely do, to purge Evolution?

If any solutions are risky, I ain't gonna do it; because I know just enough to break things, but usually not enough to fix 'em. :)

Thanks.

---

### Post by mikewhatever on 2011-08-15
Removing evolution doesn't break any dependencies.
That said, you have to watch out, because some of the evolution packages and related libraries (evolution-data-server-common) remove too much of Gnome desktop with them, but still, it's OK to remove those that don't.

As for your home, you can remove the .evelution folder without breaking the desktop or dependencies. What's there is just the user settings and the emails.

---

### Post by madjr on 2011-08-15
maybe is a good idea to just fresh install to a new partition.

i always have 2 partitions, one for my main and one for testing new releases. If everything works ok with the new release i use that, if not am safe and have the old one.

---

### Post by mikodo on 2011-08-15
Thanks guys!

:D

---

