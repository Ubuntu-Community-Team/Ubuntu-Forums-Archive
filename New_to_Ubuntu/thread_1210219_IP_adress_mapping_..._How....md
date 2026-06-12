---
title: "IP adress mapping ... How..."
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Ordes on 2009-07-11
Since these days china blocked youtube....

for windowsXP there is a solution...

\windows\system32\drivers\etc\hosts

the file is to map IP adresses to host names... when unchanged, it basiclly contains
127.0.0.1       localhost

after adding these lines
203.208.39.104  [www.youtube.com](www.youtube.com)
203.208.33.100  gtata.youtube.com

i can access youtube with IE or FF again....

Any idea how i can get this done in ubuntu... or where such a file exists... 

thanks

---

### Post by credobyte on 2009-07-11
```
sudo gedit /etc/hosts

```

---

### Post by Martje_001 on 2009-07-11
You have to type that into a terminal.

---

