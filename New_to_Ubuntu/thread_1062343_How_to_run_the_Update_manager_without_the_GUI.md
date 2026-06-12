---
title: "How to run the Update manager without the GUI"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-02-06
Is there a way to do it? I'm not referring to launching it from the terminal but having it run inside it like installing a program using apt-get install.

---

### Post by MarblePanther on 2009-02-06
```
sudo apt-get update && sudo apt-get upgrade
```

note: it will ask for your password 2 times during this process

---

### Post by Sup3r3g0 on 2009-02-06
Thanks, is it faster to do it this way instead? BTW it worked.

---

### Post by MarblePanther on 2009-02-06
It should be faster since it doesn't have to load a GUI up--theoretically ;)

---

### Post by punx45 on 2009-02-06
its also more convenient, since you can do it from anywhere*


*additional conditions necessary...

---

