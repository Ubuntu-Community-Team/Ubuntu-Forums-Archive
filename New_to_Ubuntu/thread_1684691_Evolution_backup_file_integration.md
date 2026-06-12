---
title: "Evolution backup file integration"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by vmsda on 2011-02-09
I have an old Evolution backup file which I would like to view from my current Evolution, without destroying my current data (mail, contacts, etc).
I just want to be able to view it from Evolution, and am not looking for any sync with my current data. Evolution Import will destroy my current data in favour of the old one; Evolution Search does not seem to support what I want either.

Any one for a cool suggestion? Thanks in advance.

---

### Post by ajgreeny on 2011-02-09
Temporarily rename the hidden ~/.evolution folder in your home as ~/.evolutionbak, and then restart evolution and import the old backup file.

Afterwards you can do the same again, renaming the new hidden folder as ~/.evolutionbak2 and then restoring the old one back to its original name.

---

