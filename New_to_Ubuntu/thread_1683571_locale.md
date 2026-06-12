---
title: "locale"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by zar123 on 2011-02-07
[COLOR=black]Cannot upgrade or install anything[/COLOR]:

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.utf8
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=

[COLOR=Blue]charmap  i18n is not installed or deleted[/COLOR] (this is the same file for en_US.utf8)
how can i install i18n when i [COLOR=black]Cannot upgrade or install anything copy paste from where

locale-gen en_US.UTF-8
grep: /usr/share/i18n/SUPPORTED: No such file or directory

[/COLOR]

---

### Post by sandyd on 2011-02-07
> **zar123 said:**
> [COLOR=black]Cannot upgrade or install anything[/COLOR]:

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.utf8
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=

[COLOR=Blue]charmap  i18n is not installed or deleted[/COLOR] (this is the same file for en_US.utf8)
how can i install i18n when i [COLOR=black]Cannot upgrade or install anything copy paste from where[/COLOR]
```

sudo apt-get install --reinstall language-pack-gnome-en language-support-en    [language-pack-en-base]("http://packages.ubuntu.com/source/maverick/language-pack-en-base")
locale-gen en_US.UTF-8

```

---

### Post by zar123 on 2011-02-07
> **sandyd said:**
> ```

sudo apt-get install ubuntu-l10n
locale-gen en_US.UTF-8

```

E: Unable to locate package ubuntu-l10n
locate-gen
grep: /usr/share/i18n/SUPPORTED: No such file or directory

this directory is empty

---

### Post by zar123 on 2011-02-07
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by zar123 on 2011-02-07
> **sandyd said:**
> ```

sudo apt-get install --reinstall language-pack-gnome-en language-support-en    [language-pack-en-base]("http://packages.ubuntu.com/source/maverick/language-pack-en-base")
locale-gen en_US.UTF-8

```
it downloaded the package but unable to install it
ERROR were
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.utf8"
    are supported and installed on your system.
there were also error form gtk python
ended up with  "E: Sub-process /usr/bin/dpkg returned an error code (1)"

---

### Post by zar123 on 2011-02-07
still nothing

---

