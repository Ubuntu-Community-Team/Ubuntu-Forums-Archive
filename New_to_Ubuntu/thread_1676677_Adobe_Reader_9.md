---
title: "Adobe Reader 9"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by iraparks on 2011-01-27
How can I change the Reader to English, Package Manager only has DEU version and I can't communicate in German.

Thank you,

---

### Post by mharrison on 2011-01-27
Have you tried this?

[http://www.liberiangeek.net/2010/09/install-adobe-reader-acroread-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-adobe-reader-acroread-ubuntu-10-10-maverick-meerkat/)

---

### Post by kaldor on 2011-01-27
I see two packages. *Adobe Reader 9* and *Adobe Reader 9 - German*.

Run *sudo apt-get install acroread* (to install Adobe Reader) and see if that works.

---

### Post by Bölvaður on 2011-01-27
by just searching for Adobe reader in synaptic package manager I found 2 packages


[LIST]
[*]acroread
[*]adobereader-deu
[/LIST]

You should uninstall the version you have currently (for an instance you can go to System &#8594; Administration &#8594; Synaptic Package Manager and quick search for "adobe reader" and click the box in front of those options)

you can install acroread package from synaptic or by clicking [THIS LINK]("apt:acroread")
(it does the same thing and installs acrobat from the same source as in synaptic)

---

### Post by AlphaLexman on 2011-01-27
From a command line, what is the output of:
```
echo "$LANG and $LANGUAGE"
```

---

### Post by iraparks on 2011-01-30
thank you everyone, i got it! excellent forum, understanding the definition of "Beginner". Cheers

---

