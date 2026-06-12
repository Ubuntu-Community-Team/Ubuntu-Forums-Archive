---
title: "Modem help does not match reality."
date: 2009-03-17
forum: New to Ubuntu
---

### Post by Bob Appleby on 2009-03-17
Using 8.10  
I installed a Linuxant driver for my modem, then looked in the help system for what to do next in the "Connecting with a modem" section. The first few lines were:

Press system>administration>network
Press unlock and type your password
To unlock settings select connections tab.

There was no "network" only "network tools" which I selected.
There was no "unlock"
There was no "connections tab"

What am I doing wrong?

Bob

---

### Post by mdp25 on 2009-03-17
I'm having the same problem. I hope someone can please shed some light on this.

---

### Post by Bob Appleby on 2009-03-17
Have you found a way to set up your modem with data concerning your ISP? Their phone number, password etc?

---

### Post by ddrichardson on 2009-03-17
There was a move around of packages - [here]("https://bugs.launchpad.net/ubuntu-doc/+bug/310331").

---

### Post by ugm6hr on 2009-03-17
If the driver is correctly installed, it is likely that everything else can be done from within Network Manager (the icon in the top-right that looks like 2 computer screens or 4 blue/grey vertical bars of different heights).

---

### Post by ddrichardson on 2009-03-17
It can't. NM doesn't yet support modems. gnome-network-tools did. Large bug thread, many grumpy users.

---

