---
title: "Change language for one user"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by KIAaze on 2011-02-17
Hi,

I'm trying to create a new user with his own language.
The system-wide language is esperanto.
Support for english is installed.

But when I set the language to english at the login screen and then log in, everything is still in esperanto.
I also tried it with other languages. Nothing works.

How can I change the language for just one user, without changing the system-wide language?

edit: Actually, the language change at login seems to only work partially: the date applet and firefox use the correct language. The rest remains in esperanto.

edit: **Solved by reordering the languages in "System -> Administration -> Language Support" by drag and drop, while logged in as the new user.**

---

### Post by NightwishFan on 2011-02-17
They way you did it at the log in screen should work. Try ensuring full english support is installed in System -> Administration -> Language Support.

---

### Post by KIAaze on 2011-02-17
I already did that. The language support for English is installed.

---

### Post by KIAaze on 2011-02-18
Ok, problem solved. :)

At first I noticed that the environment variables were wrong. I had something like:
```
$ printenv | grep LANG
LANG=de_DE.utf8
GDM_LANG=de_DE.utf8
LANGUAGE=eo_US:eo

```
(I wanted german.)

So I added this to ~/.profile:
```
export LANGUAGE="de_DE.utf8"
```

And it worked.

But I wasn't satisfied with this hack, so I searched for info on the LANGUAGE environment variable and found out that you could actually set it to an ordered list of languages.
That's when I checked "System -> Administration -> Language Support" again and found out that you could reorder the list by drag and drop (without root permissions). (it is explained in the text under it... ^^')

Doing so actually adds an export LANGUAGE line to ~/.profile:
```
export LANGUAGE="de:de_DE:de_AT:de_BE:de_CH:de_LI:de_LU:en"
```

And then everything works. So it was just me not knowing how to use the language support interface. :)

I'm not sure if having to do this additionally to selecting the language at login is normal behaviour or a bug. :confused:

Interesting possibility: multiple spelling checks + different interface language in xchat:
[http://ubuntuforums.org/showthread.php?t=598212](http://ubuntuforums.org/showthread.php?t=598212)

---

### Post by NightwishFan on 2011-02-18
I confirm that you need to drag and drop the language near the top to get proper support. Interesting (and confusing). In this case I like the Debian way better, just run a command to pick locales and it works from the log in screen.

---

