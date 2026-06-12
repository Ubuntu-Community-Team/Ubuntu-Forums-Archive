---
title: "Installing Octave 3.2.4"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by evan54 on 2010-02-25
Hi,

I'm a beginner and am trying to install Octave 3.2.4 on ubuntu. I have a 64 bit processor.

I downloaded a .tar.gz file from this website:

[http://www.gnu.org/software/octave/download.html](http://www.gnu.org/software/octave/download.html)

and when running "./configure" I get the following message:

configure: WARNING: I couldn't find -ltermcap, -lterminfo, -lncurses, -lcurses, or -ltermlib!
checking for rl_set_keyboard_input_timeout in -lreadline... no
configure: WARNING: I need GNU Readline 4.2 or later
configure: error: this is fatal unless you specify --disable-readline

I don't want to disable -readline as I'm not sure how that will effect other programms.

any help much appreciated,
eVan

**************************************
EDIT
**************************************

so i downloaded libreadline-dev through the synapitc package manager and it sort of started working... However, it took forever... so I quit... How long is it meant to take I've never had an installation go for so long.

eVan

---

### Post by smmalmansoori on 2010-02-25
Install it from synaptic, its already there.

---

### Post by evan54 on 2010-02-25
ok yeah that is what I ended up doing. But the version there is not 3.2.4... doesn't matter though thanks anyway

---

### Post by fkasumovic on 2010-04-16
Try installing libreadline5-dev or libreadline6-dev from synaptic,
it works for me.

---

