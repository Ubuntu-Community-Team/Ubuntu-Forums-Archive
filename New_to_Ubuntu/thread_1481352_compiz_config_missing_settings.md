---
title: "compiz config missing settings"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2010-05-12
so, on my girlfriends laptop, she has simple compiz config settings manager and advanced desktop effects (ccsm). the "enable extra animations" button wont let her click on it, and the paint fire option has disappeared. What happened?

---

### Post by themusicalduck on 2010-05-12
Open Synaptic (System > Administration) search for compiz-fusion-plugins-extra and install the package listed. Or if you want just run ```
sudo apt-get install compiz-fusion-plugins-extra
``` in a terminal.

Hopefully that will install everything.

---

### Post by LunaticHiatus on 2010-05-12
yup, worked. weird... thanks!

---

### Post by dkjMusic on 2010-09-25
> **LunaticHiatus said:**
> yup, worked. weird... thanks!

Yeah, it's weird alright. After I installed the extras via Synaptic, CCS let me click the "Enable extra animations" box, but its tooltip says "Can't find any animation extension plugins." What do I do now?

---

