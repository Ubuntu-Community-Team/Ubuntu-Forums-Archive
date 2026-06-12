---
title: "General questions about Metacity and Compiz"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by Nico34 on 2011-02-18
Hi,

I've spent the past two days looking for a clear and plain explanation about Compiz and Metacity, but didn't find any.


I'd be really glad if you could answer to this simple (not to say noobish :mrgreen:) questions:
1) Metacity and Compiz are installed automatically in Ubuntu 10.10, but Metacity is the default window manager, right?
2) As there doesn't seem to be a simple GUI "switcher", how do you enable/disable them (easiest possible way)?
3) Do they work together? Metacity is the default wm, but  when I activate a Compiz desktop effect, does Metacity stop to run? How do I know which one is enabled?
4) I have to enable Compositing to use Docky but don't want to use Metacity's one (turned on with Ubuntu Tweak) and would like to use Compiz Compositing; how do I activate it?


Many thanks in advance for your help.

Bye :)

---

### Post by TeoBigusGeekus on 2011-02-18
> **Nico34 said:**
> Hi,

I've spent the past two days looking for a clear and plain explanation about Compiz and Metacity, but didn't find any.


I'd be really glad if you could answer to this simple (not to say noobish :mrgreen:) questions:
1) Metacity and Compiz are installed automatically in Ubuntu 10.10, but Metacity is the default window manager, right?
2) As there doesn't seem to be a simple GUI "switcher", how do you enable/disable them (easiest possible way)?
3) Do they work together? Metacity is the default wm, but  when I activate a Compiz desktop effect, does Metacity stop to run? How do I know which one is enabled?
4) I have to enable Compositing to use Docky but don't want to use Metacity's one (turned on with Ubuntu Tweak) and would like to use Compiz Compositing; how do I activate it?


Many thanks in advance for your help.

Bye :)
1) Metacity is indeed the default one - compiz is enabled when you have enabled advanced desktop effects from the appearance preferences.

2)
```
compiz --replace
```
Starts compiz.
```
metacity --replace
```
Starts metacity.

3)They don't work together, as far as I know. To see which one is enabled you can check in your appearance settings whether advanced desktop effects are enabled.

4)No idea about this, sorry.

---

### Post by hannnndy on 2012-01-25
I have a problem activating my compiz too

when i try 
# compiz --replace

I get: 
 the following error [http://ubuntuforums.org/showthread.php?p=11639426#poststop](http://ubuntuforums.org/showthread.php?p=11639426#poststop)

please help it's urgent

---

