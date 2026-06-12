---
title: "how do I install all the java packages?"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by inthejuice on 2010-06-04
I would like to know how to download java in terminal or in any other way... I'm trying to install limewire but it keeps asking for some java packages... but i would like to have them all just so i can get rid of this problem. Im a  noob and I really need help!!:confused::confused::confused:
If you could help me, i would appreciate it.


InTheJuice

---

### Post by greyfox1 on 2010-06-04
First, I recommend you use [Frostwire]("http://www.frostwire.com/") over Limewire (it uses the same P2P network but is completely free, unlike Limewire).

Second, you should have all the java-related stuff you need by installing the ubuntu-restricted-extras package by opening Terminal (Applications->Accessories->Terminal):

```
sudo apt-get install ubuntu-restricted-extras
```

If you still have trouble after installing the restricted extras, please let us know exactly what error message you are seeing and what package(s) are being asked for.

---

### Post by 3rdalbum on 2010-06-04
You   need   to   enable   the  Partner   repository,   in   the  Other Software   tab   of  Software   Sources.   Then   you   can   install   the   'sun-java6-jre'   package   in   Synaptic.

---

### Post by inthejuice on 2010-06-04
> **greyfox1 said:**
> First, I recommend you use [Frostwire]("http://www.frostwire.com/") over Limewire (it uses the same P2P network but is completely free, unlike Limewire).

Second, you should have all the java-related stuff you need by installing the ubuntu-restricted-extras package by opening Terminal (Applications->Accessories->Terminal):

```
sudo apt-get install ubuntu-restricted-extras
```


I already tried that, and it says that the package I have is the latest update. So, it is still not working. do you know anyother way?

---

### Post by inthejuice on 2010-06-04
> **3rdalbum said:**
> You   need   to   enable   the  Partner   repository,   in   the  Other Software   tab   of  Software   Sources.   Then   you   can   install   the   'sun-java6-jre'   package   in   Synaptic.

let me try it... it's running a bit slow tho... and iI can't find that package :S

---

### Post by wojox on 2010-06-04
Have a look here. [URL="http://wojox.homelinux.org/?p=78"]
Install Sun Java on Ubuntu 10.04
[/URL]

---

