---
title: "Synaptic package Manager (Password)"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by hkl@hkl.no on 2010-11-01
Anyone

I'm confused, just installes ubuntu server 10.10 and ubuntu-desktop. Everything works fine, except, I try to run Synaptic Package Manager from the GUI, it ask for password, I type the "admin user" password (the user I'm also logged in with), and I get an invalid password responce.

The password works when logging in, sudoing, and for other GUI apps that requires PW.

Help please
br

hkl

---

### Post by ibizatunes on 2010-11-01
Does you account have admin rights? if it does then type your own password in...
If not you will have to assign your self admin rights, from admin > user and groups

---

### Post by hkl@hkl.no on 2010-11-01
The account has admin rights, (is the first user created on system) UID:1000

When I check in the Users & Groups GUI I also have to submit PW, this is the same pw I use when I try package Manager, no problems in users & Groups (PW accepted) but not in Package mgr.

hkl

---

### Post by hkl@hkl.no on 2010-11-02
Anyone who have an idea? Please

This is confusing.

Br

hkl

---

### Post by coffeecat on 2010-11-02
> **hkl@hkl.no said:**
> Anyone who have an idea? Please

It's possible you may have fallen foul of a really obscure little quirk I discovered when trying to be far too clever for my own good. See this thread:

[http://ubuntuforums.org/showthread.php?t=1577781](http://ubuntuforums.org/showthread.php?t=1577781)

Try both 'gksudo synaptic' and 'gksu synaptic' from the terminal. If you get different gui password prompt windows and gksudo works when gksu doesn't, then the explanation is in that thread and the fix is in gconf-editor.

---

### Post by hkl@hkl.no on 2010-11-02
> **coffeecat said:**
> It's possible you may have fallen foul of a really obscure little quirk I discovered when trying to be far too clever for my own good. See this thread:

[http://ubuntuforums.org/showthread.php?t=1577781](http://ubuntuforums.org/showthread.php?t=1577781)

Try both 'gksudo synaptic' and 'gksu synaptic' from the terminal. If you get different gui password prompt windows and gksudo works when gksu doesn't, then the explanation is in that thread and the fix is in gconf-editor.

And we have a WINNER!

Many thanks coffeecat, would never ever found this one myself. I'll by you a coffee (cat) next time your in the neighborhood.

Again thanks

hkl:popcorn:

---

