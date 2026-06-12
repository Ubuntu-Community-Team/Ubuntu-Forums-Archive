---
title: "Symbolic link not shown by ls and not working"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by Mariane on 2011-05-19
I tried to create a symbolic link to ./Desktop/Videos called kdenlive. 

Unless I tell the program kdenlive each time I use it that I want it to save in ./Desktop/Videos it creates a directory called kdenlive and saves there. 

I deleted the kdenlive directory, then I typed: 

```

ln -s kdenlive ./Desktop/Videos

```

It returned but "ls" does not show kdenlive and "cd kdenlive" does not work. 

```

sudo ln -sf kdenlive ./Desktop/Videos

```

Does not work either. 

Mariane

---

### Post by mcduck on 2011-05-19
You are doing the linking wrong way. You need to first tell what to link, and then where to link it.

This should work:
```
ln -s ~/Desktop/Videos kdenlive
```

---

### Post by Mariane on 2011-05-19
:oops::oops::oops: 

Thank you

---

