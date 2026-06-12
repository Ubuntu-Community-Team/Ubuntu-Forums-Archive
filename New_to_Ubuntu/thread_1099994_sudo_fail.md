---
title: "sudo fail"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Minirogue on 2009-03-18
username@ubuntu:~/RNA/stemconvert$ dir
documentation.doc  stemconvert
username@ubuntu:~/RNA/stemconvert$ ./stemconvert
bash: ./stemconvert: Permission denied
username@ubuntu:~/RNA/stemconvert$ sudo ./stemconvert
sudo: ./stemconvert: command not found



So yeah...su didn't do like I asked...

---

### Post by Rocket2DMn on 2009-03-18
Is stemconvert set as executable?
```
chmod +x stemconvert
```

---

### Post by Minirogue on 2009-03-18
> **Rocket2DMn said:**
> Is stemconvert set as executable?
```
chmod +x stemconvert
```

and this is why I am a noob...thank you, thank you.

---

### Post by taurus on 2009-03-18
Next time, run the **ls -la** command to list everything about files/directories in the current directory.

---

