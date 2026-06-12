---
title: "Is madwifi driver always installed?"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by Sunnz on 2007-01-19
If no wifi card was installed during the installation of Edgy, would madwifi drivers already been installed?

Say if I want to install a atheros wifi card into an existing Edgy system, do I need to install driver for it, or would it be already installed?

Thanks.

---

### Post by tdwester on 2007-01-20
Madwifi is there. I just installed an atheros and it just worked.

---

### Post by Sunnz on 2007-01-20
That's very cool thanks!!

---

### Post by tturrisi on 2007-01-20
AFAIK, madwifi is NOT installed by default but it exists in the restricted-modules package.  You must enable the multi-universe repositiries by editing your /etc/apt/sources.list or enable those sources using Synaptic.  Afterwhich, do:
apt-get update
or in Synaptic press the Reload button on the toolbar.  Then locate and install the linux-restricted-modules that match your kernel.  Then reboot.  Madwifi will now be loaded if the card was inserted at boot.

---

### Post by Zzwazz on 2007-01-23
I have an atheros card and when I first installed Ubuntu it worked without me touching a thing. I screwed it up though and now I can't connect. Is there any way to just reset the settings to how it is when you first install Ubuntu?

---

### Post by Sunnz on 2007-01-24
> **tturrisi said:**
> AFAIK, madwifi is NOT installed by default but it exists in the restricted-modules package.  You must enable the multi-universe repositiries by editing your /etc/apt/sources.list or enable those sources using Synaptic.  Afterwhich, do:
apt-get update
or in Synaptic press the Reload button on the toolbar.  Then locate and install the linux-restricted-modules that match your kernel.  Then reboot.  Madwifi will now be loaded if the card was inserted at boot.
It turns out that the linux-restricted-modules are already installed for me.

---

### Post by Sunnz on 2007-01-24
> **Zzwazz said:**
> I have an atheros card and when I first installed Ubuntu it worked without me touching a thing. I screwed it up though and now I can't connect. Is there any way to just reset the settings to how it is when you first install Ubuntu?
Can you please post the output of this command:
```
uname -r
```

---

