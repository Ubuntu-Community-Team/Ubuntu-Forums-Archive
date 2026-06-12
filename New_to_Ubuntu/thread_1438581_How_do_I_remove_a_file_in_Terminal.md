---
title: "How do I remove a file in Terminal?"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by asharpham on 2010-03-25
I have a file that requires root permissions to remove or edit it. Therefore I can only remove it in Terminal as root. I can get to the file as root but I don't know the command to remove it. Can someone help me please?

---

### Post by cjv8888 on 2010-03-25
> gksu nautilus

then you can remove it graphically

---

### Post by Kenny_Larsen on 2010-03-25
```
sudo rm file
```

Obviously be careful what you delete using sudo!

---

### Post by derekeverett on 2010-03-25
The command is rm

```

rm path/filename

```

---

### Post by asharpham on 2010-03-28
Thanks for that. It seems so simple when you know!

---

