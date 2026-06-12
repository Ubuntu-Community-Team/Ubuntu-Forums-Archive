---
title: "Lock Version in Synaptic doesn't translate to apt-get upgrade / aptitude safe-upgrade"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by lethalfang on 2009-05-12
I have locked to an older version of Kile (2.0.1) by checking "Lock Version" in the GUI synaptic package manager, but the aptitude and apt-get will still try to upgrade Kile each time. 
How do I get around that? 

Thanks in advance.

---

### Post by lethalfang on 2009-05-12
Ok, after looking around on the internet, this seems to work:

```
 sudo aptitude hold kile 
```

It works with aptitude package manager, but not the apt-get, but that's okay.... now I am able to upgrade things remotely thru the terminal without frowning over the Kile issue.

---

