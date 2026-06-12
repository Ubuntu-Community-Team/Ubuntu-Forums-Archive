---
title: "What do the default Ubuntu groups do?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by evouga on 2009-01-23
"man group" and "man groups" didn't help. I've figured out that I need admin to use sudo and lpadmin to use CUPS. What do netdev, powerdev, and adm do?

EDIT: Also, which group do I need in order for synaptic to show up on the System menu? I can access Synaptic from the command line by typing "sudo synaptic" but it doesn't appear in the GUI, for some reason.

---

### Post by cozmicharlie on 2009-01-23
> **evouga said:**
> "man group" and "man groups" didn't help. I've figured out that I need admin to use sudo and lpadmin to use CUPS. What do netdev, powerdev, and adm do?

EDIT: Also, which group do I need in order for synaptic to show up on the System menu? I can access Synaptic from the command line by typing "sudo synaptic" but it doesn't appear in the GUI, for some reason.

Synaptic should be in the menu without having to do anything.  You should be able to go to sytem>administration>package manager.  If it is not there then check the menu list by right clicking on applications>edit menus>system>administration and make sure it is checked.  If it is not there (and it should be) then add it as a new item using the command "synaptic" (without quotes).  When you start it from the menu, it will ask you for your password (basically the same as doing sudo).  I really doubt synaptic is not on the menu.

---

### Post by evouga on 2009-01-23
When I go into "edit menu," there is no check in the checkbox next to "Synaptic Package Manager." I can check it, but then it unchecks by itself after a few seconds, and Synaptic still does not appear on my System menu.

---

### Post by cozmicharlie on 2009-01-23
How are you signing on - as a user?  Are you (whatever you set up for user) a member of the group "admin"?

---

### Post by evouga on 2009-01-23
I am logging in through LDAP, which gives me the group IDs corresponding to admin (110 I think) and lpadmin.

What's strange is that most other Administration items - Update Manager, for instance - show up fine in the menu. It's only Synaptic (and the non-free driver menu item too, it seems) that aren't there, and refuse to get added when I go to "edit menu."

Note I can run these fine manually on the command line, by typing eg. sudo synaptic.

---

### Post by evouga on 2009-01-26
Surely somebody is an expert on Linux user groups, and/or how Ubuntu populates its menus? Bumping in hopes of more help...

---

