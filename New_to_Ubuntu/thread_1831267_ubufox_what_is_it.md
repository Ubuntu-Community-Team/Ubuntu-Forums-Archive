---
title: "ubufox? what is it?"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-23
apt-get upgrade

Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ubufox: Depends: xul-ext-ubufox
E: Unmet dependencies. Try using -f.

---

### Post by Lars Noodén on 2011-08-23
"Ubuntu-specific configuration defaults and apt support for Firefox"
[http://packages.ubuntu.com/natty/xul-ext-ubufox](http://packages.ubuntu.com/natty/xul-ext-ubufox)

---

### Post by 007casper on 2011-08-23
apt-get -f install ubufox

is that correct?

---

### Post by Lars Noodén on 2011-08-23
The package name is 'xul-ext-ubufox' so the option would be:

apt-get -f install xul-ext-ubufox

---

