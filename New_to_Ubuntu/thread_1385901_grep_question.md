---
title: "grep question"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by mike941 on 2010-01-20
Can grep search for files or should i just use find for that? I know grep searches in files. I'm just wondering if you can find files with grep without having to know the command inside and out.

---

### Post by nick_goodfate on 2010-01-20
i think you need to give it an inptut so it can find something from the given input. you can use ```
locate file_you_r_looking_for
```

---

### Post by debil on 2010-01-20
```
ls -R dir-to-start-the-search/ | grep search-string
```

But **find** or **locate** suit much better for searching files.

---

### Post by wojox on 2010-01-20
Yes find is a better command. This will search my entire filesystem for Firefox:

```
wojox@wojox-desktop:~$ sudo find / -name firefox
[sudo] password for wojox: 
/home/wojox/.mozilla/firefox
/root/.mozilla/firefox
/usr/bin/firefox
/usr/share/firefox
/usr/share/doc/firefox
/usr/lib/firefox
/usr/lib/firefox-3.5.8pre/firefox

```

---

