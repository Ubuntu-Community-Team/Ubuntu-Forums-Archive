---
title: "go from x.org edgers back to stable"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by libihero on 2010-06-24
im having some bugs on my desktop and i dont kno if its because i'm using the x.org edgers.  how can i make my drivers back to the stable ones?

---

### Post by VH-BIL on 2010-06-24
Can you uninstall it and install xorg from the reps?

---

### Post by sandyd on 2010-06-24
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```

---

### Post by libihero on 2010-06-24
so if i do that i wont have to worry about reinstalling the stable drivers?

---

### Post by -humanaut- on 2010-06-24
> **libihero said:**
> so if i do that i wont have to worry about reinstalling the stable drivers?

I had to purge xorg edgers from one my systems and i did have to reinstall the stable drivers again. I recommend using Xswat xorg its a bit more stable I use it on my main system so I can use the 256.35 Nvidia driver. which is the current stable release as of yesterday i think lol

---

### Post by alphacrucis2 on 2010-06-24
> **-humanaut- said:**
> I had to purge xorg edgers from one my systems and i did have to reinstall the stable drivers again. I recommend using Xswat xorg its a bit more stable I use it on my main system so I can use the 256.35 Nvidia driver. which is the current stable release as of yesterday i think lol

ppa-purge does the reinstall from main automatically.

---

### Post by VastOne on 2010-06-24
> **carlee said:**
> ```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```

+1

ppa-purge makes life on the edge a lot easier

---

