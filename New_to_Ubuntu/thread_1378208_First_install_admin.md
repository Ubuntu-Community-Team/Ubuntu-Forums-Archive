---
title: "First install admin"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by extc on 2010-01-11
I have installed the latest ubuntu from the windows installer as a dual boot system. My username was "administrator", as is the default when installing Ubuntu.

When I log in though, I have no administration rights, cannot configure the modem or internet settings. When I open the user management program, all the rights are greyed-out and unselectable. Un then re-installing does nothing.

Anyone can help? Otherwise I love this OS.

Thank you all so much,

James.
:D

---

### Post by nothingspecial on 2010-01-11
I`m not sure how wubi works exactly but is it possible to boot into recovery mode. This will give you a root shell from which you can fix this.

```
adduser administrator admin
```

or make a new administrative user

```
adduser james
```

```
adduser james admin
```

---

### Post by extc on 2010-01-11
> i assume linux knows what it's doing with me!

thank you very much, i shall try that now. ;):d

---

### Post by extc on 2010-01-19
Thank you, it worked.

---

### Post by nothingspecial on 2010-01-19
Glad to help

---

