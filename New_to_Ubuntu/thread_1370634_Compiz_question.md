---
title: "Compiz question"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by myolbug on 2010-01-02
I had a hard drive fail and som I um using a temporary one for now.  I installed 9.04 then did the upgrade to 9.10.  I have compiz fusion icon but that doesn't really do me much good.  On my old drive, I had a Compiz Fusion under System - Preferences - Compiz.  I don't now and I would like to be able to use the features again.

I have my Visual Effect set to the highest but how do I regain waht I had before?

---

### Post by starcraft.man on 2010-01-02
> **myolbug said:**
> I had a hard drive fail and som I um using a temporary one for now.  I installed 9.04 then did the upgrade to 9.10.  I have compiz fusion icon but that doesn't really do me much good.  On my old drive, I had a Compiz Fusion under System - Preferences - Compiz.  I don't now and I would like to be able to use the features again.

I have my Visual Effect set to the highest but how do I regain waht I had before?

I'm unsure whether you mean just regular compiz or the settings manager.

System > Preferences > Appearances > Visual Effects Tab > Pick an option.

OR

System > Preferences > CompizConfig Settings Manager

This one is installed separately in a package, a sample install can be following command in a terminal:

```
sudo apt-get install compizconfig-settings-manager
```

Hope that answers.

---

### Post by myolbug on 2010-01-02
Thanks for the reply, I get this:
> E: Couldn't find package compizconfig-settings-manager
randy@randy-desktop:~$ 


---

### Post by myolbug on 2010-01-02
Never mind, I pointed to Synaptic to the main US Repository and it is installing it.

---

