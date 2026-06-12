---
title: "update manager not responding"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by mikhaell on 2010-02-12
hi, i tried running update manager and got no response. when i typed in terminal sudo update manager i get sudo: update: command not found
. any ideas?

---

### Post by Enigmapond on 2010-02-12
That's because it would be..
```
sudo update-manager
```

also have you tried to update/upgrade in the terminal?

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by mikhaell on 2010-02-12
this is what i get when i write sudo update-manager

(process:8662): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 107, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 119, in __init__
    logging.exception("setlocale failed")
NameError: global name 'logging' is not defined

---

### Post by Enigmapond on 2010-02-12
I don't use it...I deleted the whole thing as it was getting in the way. Maybe try purging it and then re-installing.

---

### Post by mikhaell on 2010-02-12
thanks but i think the problem is in a missing file when i upgrade on terminal i keep on getting:

perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.

---

### Post by mikhaell on 2010-02-12
any ideas?

---

### Post by rabon on 2010-02-13
I had the same problem after upgrading to Karmic (when I changed system language).
I found that this error has to do with missing language packages.

See what gives sudo dpkg-reconfigure locales .

May be you are using a language which is not installed. You can get language packages via "sudo apt-get install --reinstall language-pack-en". The other possibility would be to change your labguage via "export LANG=en_GB" or " (for english, for example). May be you have to fiddle around with utf8 - there are lang-Packages called en_US.utf8 and without, dependign on your configuration.
This should also work via Ubuntu menus System -> Admin -> Language support.

---

