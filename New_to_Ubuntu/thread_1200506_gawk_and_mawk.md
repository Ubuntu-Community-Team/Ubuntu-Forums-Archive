---
title: "gawk and mawk"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by stuckagain on 2009-06-30
Hi all,

I have installed gawk on my Ubuntu 8.10 system. Now the awk command invokes gawk, instead of the default mawk. How do I change this? I want awk to invoke mawk (as before) so that existing system scripts don't get affected in any way. (I can always use gawk with the "gawk" command and not as awk.)

Rgds.

---

### Post by Mornedhel on 2009-06-30
Hi,

Try

```
sudo update-alternatives --config awk
```

On my system it lets you choose between mawk and gawk as the default executable for awk.

---

### Post by stuckagain on 2009-06-30
Thanks! It works.:p

---

