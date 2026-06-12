---
title: "I am a numty - help please!"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Hoohaa on 2010-01-11
Hi all 
I am a green Ubunto user and have been playing,......oh dear! Can anyone help me with this message?

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Type ‘n’ is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-karmic.list, E:The list of sources could not be read.'

Any help gratefully accepted.

Regards, Hoohaa

---

### Post by howefield on 2010-01-11
Edit your sources to comment out the offending line.

Open a terminal (Applications > Accessories > Terminal) and copy/paste the following...

```
gksu gedit /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-karmic.list
```

Put two "##" at the front of the line one. Save and try again.

---

### Post by Hoohaa on 2010-01-13
Phew thanks Howefield you are a life saver, all sorted now :D

Regards, Hoohaa

---

