---
title: "Conky as a startup task"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by Dark Aspect on 2009-11-15
Hello,

For some reason in Ubuntu 9.10, I cannot make conky a startup task. When I use System &#8594; Preferences &#8594; Startup Applications conky appears on the screen very briefly upon login and than disappears. I have had conky as a startup task since Ubuntu 7.10, whats wrong?

---

### Post by Technoviking on 2009-11-15
The best way to start conky at login so it does not have problems with compiz is to use a script.

```
gedit startupconky.sh
```

and enter the following

```
#!/bin/bash
sleep 25 && conky ;
```

Then add startupconky.sh to *System --> Preferences --> Startup Applications*.

---

### Post by Dark Aspect on 2009-11-15
Thank you, [COLOR="Red"]Technoviking[/COLOR].

Thread solved.

---

