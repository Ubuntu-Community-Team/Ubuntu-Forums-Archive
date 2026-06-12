---
title: "compiz effects"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by benk95 on 2010-09-06
i can't find all of the effects in compiz fusion that many people have like cube deformation and 3d windows and many more is there a way to enable more effects.

---

### Post by Mze on 2010-09-06
Install the compiz extra-plugins package

source: [CompizFusion Plugins]("http://wiki.compiz.org/CompizFusionPlugins")

---

### Post by Chesamo on 2010-09-06
You'll have to install the CompizConfig Manager. ```
sudo apt-get install compizconfig-settings-manager
``` You can find it in System > Preferences > Advanced Desktop Effects Settings.

---

### Post by sikander3786 on 2010-09-06
> **Chesamo said:**
> You'll have to install the CompizConfig Manager. ```
sudo apt-get install compizconfig-settings-manager
``` You can find it in System > Preferences > Advanced Desktop Effects Settings.

I think he has already installed that ;)

You need to install the compiz-fusion-plugins-extra package.

```

sudo apt-get install compiz-fusion-plugins-extra

```

That will give you all the extra animations. 

Regards.

---

### Post by Verbeck on 2010-09-06
Add compiz repositories:
```
sudo apt-add-repository ppa:compiz/ppa
```
```
sudo apt-get update
```

Install extra and unsupported plug ins:
```
sudo apt-get install compiz-fusion-plugins-unsupported compiz-fusion-plugins-extra
```

All new plugins will be in compizconfig settings manager

;)

---

### Post by cake nom nom on 2010-09-06
Please mark your thread as solved if this is the case

---

### Post by benk95 on 2010-09-12
i found it i just searched compiz extras in the software center, and it added the rest of the effects

---

