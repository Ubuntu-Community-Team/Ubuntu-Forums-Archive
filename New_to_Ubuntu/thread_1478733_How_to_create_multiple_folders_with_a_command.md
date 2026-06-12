---
title: "How to create multiple folders with a command"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by karthick87 on 2010-05-10
I would like to create a multiple folders using a single command at once....How to do this....?For example i should have a folder named new and inside this new folder i should have another folder and so on....

---

### Post by Paqman on 2010-05-10
To create the folder in your current location:
```
mkdir /new/folder/with/as/many/nested/folders/as/you/want
```

You'll need sudo to create the folder anywhere outside your home folder.

---

### Post by sisco311 on 2010-05-10
> **Paqman said:**
> To create the folder in your current location:
```
mkdir **-p** /new/folder/with/as/many/nested/folders/as/you/want
```

You'll need sudo to create the folder anywhere outside your home folder.

fixed ;)

---

### Post by karthick87 on 2010-05-10
Thank You....:)

---

### Post by Paqman on 2010-05-10
> **sisco311 said:**
> fixed ;)

Whoops. Cheers!

---

