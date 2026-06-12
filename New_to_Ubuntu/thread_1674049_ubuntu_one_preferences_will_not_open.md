---
title: "ubuntu one preferences will not open"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by yakinikku on 2011-01-23
hi guys, 

sorry for posting another thread.  but, as the thread title says my ubuntu one preferences will not open.  from the GUI or from a terminal using the ubuntuone-preferences.  i get the following error

```
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-preferences", line 1143, in <module>
    prefs_dialog = UbuntuOneDialog()
  File "/usr/bin/ubuntuone-preferences", line 535, in __init__
    self.__construct()
  File "/usr/bin/ubuntuone-preferences", line 975, in __construct
    self.devices.list_devices()
  File "/usr/bin/ubuntuone-preferences", line 377, in list_devices
    token = get_access_token(self.keyring)
  File "/usr/bin/ubuntuone-preferences", line 124, in get_access_token
    'oauth-consumer-key': 'ubuntuone'})
gnomekeyring.BadArgumentsError

```

i have also tried uninstalling and reinstalling but that did not work.  any suggestions?

---

### Post by SavageWolf on 2011-01-23
Try:
```
killall ubuntuone-preferences
```
I have problems like that sometimes...

---

### Post by yakinikku on 2011-01-23
> **SavageWolf said:**
> Try:
```
killall ubuntuone-preferences
```
I have problems like that sometimes...

tried that, this is what i get

```
ubuntuone-preferences: no process found

```

any other suggestions?

---

### Post by kmcbest on 2011-02-24
I'm getting exactly the same problem as described in #1, with the integrated Ubuntu One in 10.04.

---

