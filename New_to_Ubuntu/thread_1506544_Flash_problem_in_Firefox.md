---
title: "Flash problem in Firefox"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by Charlie Chick on 2010-06-10
Hello Everybody,

I have a curious problem. After having installed Ubuntu restricted extras (which includes flash) I can play a flash based stream but when I shut down and power the computer up again, flash streams won't play until I either re-install flash or Ubuntu restricted extras from Synaptic. 

Anybody know how to make flash work without having to constantly re-install?

Computer is a P4 with 2GB of RAM and 750GB HDD running 32 bit 10.04

Thanks,

Charlie

---

### Post by gandaran on 2010-06-10
probably you installed other flash plugins, check for gnash and swfdec flash, remove every thing flashy, just keep one adobe flash plugin installed.

---

### Post by Charlie Chick on 2010-06-10
> **gandaran said:**
> probably you installed other flash plugins, check for gnash and swfdec flash, remove every thing flashy, just keep one adobe flash plugin installed.

Gnash wasn't installed but swfdec was. I un-installed it and re-booted. No difference.

---

### Post by Bölvaður on 2010-06-10
> **Charlie Chick said:**
> Gnash wasn't installed but swfdec was. I un-installed it and re-booted. No difference.

after uninstalling that one you are supposed to install the adobe flash plugin.
no restart required, only close and reopen firefox

click here to install

[apt:flashplugin-nonfree](apt:flashplugin-nonfree)

---

### Post by Directive 4 on 2010-06-10
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)


this will solve all problems.

---

### Post by Charlie Chick on 2010-06-10
The Adobe flash plugin was already installed, so I re-installed it. It worked until I re-booted and now it doesn't work again.

---

### Post by Directive 4 on 2010-06-10
> **Directive 4 said:**
> [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)


this will solve all problems.


this will remove the source of the problem and fix everything


see, recursion

---

### Post by Charlie Chick on 2010-06-10
> **Directive 4 said:**
> this will remove the source of the problem and fix everything


see, recusion

Yes, it worked! Even after a re-boot. 

Thanks to all of you for your help. Much appreciated!

Charlie

---

### Post by migs73 on 2010-06-11
> **Directive 4 said:**
> [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)


this will solve all problems.


+1 to that!! Had problems running some flash content (ITV Player in UK) and had to watch via Vista on Vbox. I think I had at least two flash type things conflicting. Many thanks.

---

### Post by rabble on 2010-06-14
worked great!  Thanks

---

