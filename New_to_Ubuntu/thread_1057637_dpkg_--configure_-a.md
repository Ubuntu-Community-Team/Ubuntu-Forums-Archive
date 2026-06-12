---
title: "dpkg --configure -a"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by cptrohn on 2009-02-02
Ok.. I screwed something up BAD it seems..

So when I try to get a new package saying that I need to run this in terminal```
dpkg --configure -a
```  so I open the terminal and type this in, after I do this is what comes back```
dpkg: requested operation requires superuser priveldges
```

Ok.. so what did I screw up this bad?

---

### Post by kostkon on 2009-02-02
You have to give it like this
```
sudo dpkg --configure -a
```
it will ask for a password, give yours.

Then, do a
```
sudo apt-get update
```

---

### Post by cptrohn on 2009-02-02
ok when I type in ```
dpkg --configure -a
``` it does not ask for a password and the very next line in the terminal is just the error message saying it requires a superuser password.

---

### Post by kostkon on 2009-02-02
The command must be given with a *sudo* in front of it, i.e.:
```
sudo dpkg --configure -a
```

---

### Post by cptrohn on 2009-02-02
> **kostkon said:**
> The command must be given with a *sudo* in front of it, i.e.:
```
sudo dpkg --configure -a
```

LOL Ok.. I wasn't paying close enough attention... I've been up for a VERY long time... Sorry and thanks for the help. It's very much appreciated!

---

### Post by kostkon on 2009-02-02
> **cptrohn said:**
> LOL Ok.. I wasn't paying close enough attention... I've been up for a VERY long time... Sorry and thanks for the help. It's very much appreciated!
No problem :)

Is everything OK now?

---

### Post by cptrohn on 2009-02-02
fixed, that did the trick. TYVVM

---

