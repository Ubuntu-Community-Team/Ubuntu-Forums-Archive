---
title: "problem with plugin"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by RemyCarson on 2008-12-05
hey peeps, want to play a game tells me: 

Choose a plugin for media type application/x-java-vm:

It gives me a list of 4 options all of which i have installed and still the page wont load (mozilla)

Advise please.

---

### Post by SuperSonic4 on 2008-12-05
Are you in 32bit or 64bit? 64bit Java is still quite lacking:

If you're in 32bit: ```
sudo apt-get sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

```

---

### Post by RemyCarson on 2008-12-05
i am in 32 and thanks but that gave me:

E: Invalid operation sun-java6-fonts

---

### Post by SuperSonic4 on 2008-12-05
Bugger I made a typo >.<

```
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

```

---

### Post by RemyCarson on 2008-12-05
now it loads without sayng install but just comes up with a blank. no idea whats going on with that, anyway, it is no longer a problem as i dont need it anymore. but thanks for your help!! R.

---

