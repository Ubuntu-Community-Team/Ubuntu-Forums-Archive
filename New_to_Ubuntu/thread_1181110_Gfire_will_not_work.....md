---
title: "Gfire will not work...."
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Bigbob22 on 2009-06-07
I installed gfire from this website using the deb file:

```
http://gfireproject.org/downloads/
```

After that I could not find it in pidgin. I looked in the plugins section and the accounts section, but I could not find it. I tried reinstalling gfire and I tried reinstalling pidgin, but it still wouldn't work. I am running Ubuntu 8.10. Please help.

---

### Post by Bigbob22 on 2009-06-07
I tried installing from source too,but that did not help.

---

### Post by Bigbob22 on 2009-06-07
Please help.......

---

### Post by Bigbob22 on 2009-06-08
bump

---

### Post by philinux on 2009-06-08
You might need to install the pidgin-dev package from synaptic. No harm in trying it.
And restart pidgin.

---

### Post by Bigbob22 on 2009-06-08
Thanks for the help, but it did not work...

---

### Post by philinux on 2009-06-08
Ok had a go myself on 64 bit.

Downloaded the deb file and installed no errors.

Then open pidgin>Accounts>Manage Accounts>Add>Protocol
Scroll down the list and xfire is listed. Without gfire installed the protocol is not listed. I dont have an account so cant go any further.

---

### Post by philinux on 2009-06-08
Forgot to attach screenshot.

---

### Post by Bigbob22 on 2009-06-08
xfire doesn't show up

---

### Post by philinux on 2009-06-08
Ok what version of ubuntu and pidgin you running.

---

### Post by Bigbob22 on 2009-06-08
Ubuntu 8.10 and pidgin 2.5.6

---

### Post by philinux on 2009-06-08
Adventure man got his working at last.

---

### Post by Bigbob22 on 2009-06-08
I'll try reinstalling pidgin.... again. Thanks for all the help though

---

### Post by Bigbob22 on 2009-06-08
When i installed pidgin through the terminal this is the output:
```
Selecting previously deselected package pidgin.
(Reading database ... 307705 files and directories currently installed.)
Unpacking pidgin (from .../pidgin_1%3a2.5.6-1ubuntu1~pidgin5.8.10_i386.deb) ...
Selecting previously deselected package pidgin-dev.
Unpacking pidgin-dev (from .../pidgin-dev_1%3a2.5.6-1ubuntu1~pidgin5.8.10_all.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
In file "/usr/share/menu/autopackage-gtk", at (or in the definition that ends at) line 1:
[...]&#1088;&#1086;&#1085;&#1085;&#1080;&#1084; &#1055;&#1054;\\nName[sq]=Administro "software" palësh të treta\\nName[sv]=Hantera tredjepartsprogramvara\\nStartupNotify=true\\nTerminal=false\\nType=Application\\n"=
[...]                                                 ^
Expected: "="
Skipping file because of errors...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up pidgin (1:2.5.6-1ubuntu1~pidgin5.8.10) ...

Setting up pidgin-dev (1:2.5.6-1ubuntu1~pidgin5.8.10) ...

Processing triggers for menu ...
In file "/usr/share/menu/autopackage-gtk", at (or in the definition that ends at) line 1:
[...]&#1088;&#1086;&#1085;&#1085;&#1080;&#1084; &#1055;&#1054;\\nName[sq]=Administro "software" palësh të treta\\nName[sv]=Hantera tredjepartsprogramvara\\nStartupNotify=true\\nTerminal=false\\nType=Application\\n"=
[...]                                                 ^
Expected: "="
Skipping file because of errors...

```

Pidgin works but gfire is still not working.

---

