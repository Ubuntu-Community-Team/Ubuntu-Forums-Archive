---
title: "Trouble installing furiusisomount"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by kapildubey on 2009-11-26
Hello friends,

I am using ubuntu 9.04, when i am trying to install furiusisomount_0.11.1.2 , i am getting the error  as 

Error: Dependency is not satisfiableython-support(>=0.90.0)

Any help would be highly appreciated :D.

regards.

---

### Post by yeats on 2009-11-26
Hi,

How are you going about installing (i.e., are you using Synaptic/Ubuntu Software Center or a downloaded .deb file from the web)?

Standard steps to take when you get this kind of thing include refreshing your package cache.  In the terminal:

```
sudo apt-get update
```

or clicking "Reload" in Synaptic, then trying again..

---

### Post by kapildubey on 2009-11-27
Hi,

never mind. i was able to install an earlier version of furius iso mount version furiusisomount_0.9.0.2-1_i386.deb downloaded from internet.

thanks for the help.

---

