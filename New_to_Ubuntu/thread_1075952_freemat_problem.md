---
title: "freemat problem"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by cosine352 on 2009-02-20
Hi friends,

when I run
> freemat

I get this

> terminate called after throwing an instance of 'Exception'
Aborted


It used to work and suddenly I am getting this error

I tried 

> sudo aptitude reinstall freemat
sudo aptitude install freemat  build-essential

without any luck. 
any help is greatly appreciated.

---

### Post by RomeReactor on 2009-02-20
Hi. You could try purging freemat and then deleting the hidden .freemat folder in you home directory, if there is one, and then reinstall it. I don't use it, so I'm not sure if this would also delete any project/data you were working on.

Hope this helps.

---

### Post by cosine352 on 2009-02-20
That did not work. Thanks anyway.

---

### Post by krzysz00 on 2009-02-20
If there are and library packages (beginning with lib) and NOT essential system libraries (you'll know by the giant of applications that will be removed) purge and reinstall them as well.

---

