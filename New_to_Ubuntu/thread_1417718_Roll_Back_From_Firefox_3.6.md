---
title: "Roll Back From Firefox 3.6"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2010-02-27
I updated to Firefox 3.6 via the Mozilla Stable PPA and decided that it would be better to use the one with the Ubuntu repos for compatibility's sake. How would one roll back from this?

---

### Post by koba101 on 2010-02-27
```
sudo apt-get remove firefox
```

then install the one in the repos

---

### Post by Martin Marshalek on 2010-02-27
Yes, I just finished doing that actually. Until now I though linux was the same way toward firefox as MS is to Internet Explorer. Thanks for the help though.

---

### Post by lovinglinux on 2010-02-27
Disable the ppa, update and re-install Firefox.

---

