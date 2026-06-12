---
title: "Graphics card problem"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Jonathan 56 on 2010-02-27
Ubuntu is telling me my graphics card is not ativated and wont let me ativate it. Its nvidia graphics. What do i do.

---

### Post by samantha_ on 2010-02-27
```

sudo apt-get install envyng-core
sudo envyng -t
```
or go to nvidia.com and download drivers there.

what card do you have?

---

### Post by Martin Marshalek on 2010-02-27
Go to system->administration->hardware drivers and activate from there. You may need to reload your packages a few times if it's not showing up.

---

