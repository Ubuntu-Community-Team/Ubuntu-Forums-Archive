---
title: "How do I install Java6 SDK on my machine?"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by emeka_micro on 2011-07-12
Hello All,

I need aninstruction on how to install Java6 SDK.

Janus

---

### Post by jerrrys on 2011-07-12
maybe this

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by mikewhatever on 2011-07-12
You have to add the partner repository:
```
sudo add-apt-repository “deb http://archive.canonical.com/ natty partner”
```

then
```
sudo apt-get update

sudo apt-get install sun-java6-jdk
```

---

### Post by emeka_micro on 2011-07-13
Mike*

It worked, however why do I need to do that?

Janus

---

### Post by wildmanne39 on 2011-07-13
Hi, because that particular repository is not included in the official repositories by ubuntu, otherwise you could have probably went to the java website and downloaded it but that might have made the process of installing it a lot harder.

---

### Post by mikewhatever on 2011-07-13
You have to add the partner repository because Sun's java is in there, no other reason.

---

