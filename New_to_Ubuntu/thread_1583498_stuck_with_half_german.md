---
title: "stuck with half german"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Kubischbuntu on 2010-09-27
Hi,

I am just in the process of setting up a new Kubuntu 10.4 machine. i went into the System Settings - Languages and added German - thinking that this would give me German spell checking - immediately it made all of the language settings box german - since I want the comouter to be in english I removed German again and the language settings box reverted to english but most of my K menu items and some other things are still in german - how do I get everything back to english???

Thanx

---

### Post by NightwishFan on 2010-09-28
Go into synaptic and remove all traces of the german translations.

---

### Post by Kubischbuntu on 2010-09-28
will searching for "german" bring them all up?

---

### Post by NightwishFan on 2010-09-28
Quite possibly. Also, check if there is a "Defaults" button in the KDE Control Center. Forgive my limited KDE language experience, I never needed to change mine. :(

---

### Post by Kubischbuntu on 2010-09-30
Hmm.. I had a look and it only has German spell-checking dictionaries installed. I also selected to "completely remove" residual German localization packages but - still no luck - looks to me like I may have to file a bug report for this??

---

### Post by NightwishFan on 2010-10-01
Some German packages the name is DE and not German. I could help you more, but I do not even have a KDE live cd. :(

---

### Post by Silent Warrior on 2010-10-01
Do forgive me for asking: Did you log out or reboot between setting the locales? KDE seems to be more liberal about this than Gnome, but changes in languages do still only take effect for apps started after the change is applied.

Look for packages named either kde-l10n-de or kde-i18n-de and remove those. In case of problems, check to make sure you have an English localisation installed, or set to be installed. The spell-checkers are named either aspell-/ispell-/myspell-de. (hunspell?) Well, you should search for them in Synaptic, to make sure - the myspell-one might be named de_DE instead.

---

