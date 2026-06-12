---
title: "Mirroring Installed Programs on Desktop and Laptop"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-07-27
I use Unison to synchronize my personal files, but a method to mirror installed programs eludes me. How can I keep the same programs installed on both computers? How can I keep the same settings (I tried synchronizing the home directory, but this caused problems with some applications)?

---

### Post by EnigmaticCoder on 2010-07-27
I found a possible solution, although I haven't tried it yet

Generate a list of installed software
$ dpkg --get-selections > installed-software

Move that list to the other computer
$ dpkg --set-selections < installed-software
$ dselect

---

### Post by EnigmaticCoder on 2010-07-27
> **EnigmaticCoder said:**
> I found a possible solution, although I haven't tried it yet

Generate a list of installed software
$ dpkg --get-selections > installed-software

Move that list to the other computer
$ dpkg --set-selections < installed-software
$ dselect

Hmm, does that method remove unwanted packages too?

---

### Post by Paqman on 2010-07-28
> **EnigmaticCoder said:**
> Hmm, does that method remove unwanted packages too?

Yep. It shouldnt be too hard to automate the process using Ubuntu One and a couple of anacron scripts, too.

---

