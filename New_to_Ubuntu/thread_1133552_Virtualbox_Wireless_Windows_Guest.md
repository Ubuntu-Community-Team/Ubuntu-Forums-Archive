---
title: "Virtualbox Wireless Windows Guest"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by fzfowler on 2009-04-23
I have looked everywhere and have found that most guides that to deal with this problem are outdated. Basically, I have a broadcom wireless card in my laptop, I am running Ubuntu 8.10 and Virtualbox 2.2.0 with Windows XP installed as a guest. I just need to find out through any means how to connect to the internet through my wireless card. It works fine with a wired connection but I cannot for the life of me figure out how to make wireless work.

Thank you!

---

### Post by Peter09 on 2009-04-23
To clarify, does wireless work for Ubuntu?

---

### Post by fzfowler on 2009-04-23
Yes, no problems with Ubuntu wifi at all...if there is a command that I can do to show you my wireless configuration I can post that information...

---

### Post by Peter09 on 2009-04-23
VirtualBox uses your existing connection, it does not need any further configuration. In the network settings for your virtualbox guest you need to set up the type of connection you need.

---

### Post by fzfowler on 2009-04-23
That is what I am having trouble with. I used a bridged connection when I am connected by cable but I cannot figure out my connection when I use wireless.

---

### Post by Monotoko on 2009-04-23
Windows XP usually just says its connected wired whilst the host computer may be connected wirelessly, or as yours is, bridged.

Windows XP will use the very same internet the host computer uses, just because it says its connected wired, doesnt mean it actually is, it just thinks its connected wired, because its connected to the host (think of it as a virtual wire that connects these two) the host then goes to the internet

---

