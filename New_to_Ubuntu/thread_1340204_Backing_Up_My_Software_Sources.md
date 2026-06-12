---
title: "Backing Up My Software Sources"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-11-28
I've had enough of karmic by upgrade. There have just been far too many problems with it that I can't seem to resolve. Therefore, I'm going to try a fresh install.

I've backed up my home directory using Pybackpack, and I've saved my markings in Synaptic, but what I can't work out is how to back up my software sources and authentication keys.

Could someone please tell me how that's done?

---

### Post by jlhaslip on 2009-11-28
Have a look at AptonCD from the repositories.
Might be what you are looking for.

---

### Post by Virtual Liberty on 2009-11-28
Not sure about authentication keys but the process of backing up sources.list is trivial:

```
sudo cp /etc/apt/sources.list $HOME/sources.list.bak
```

---

### Post by Roger Allott on 2009-11-28
> **Virtual Liberty said:**
> Not sure about authentication keys but the process of backing up sources.list is trivial:

```
sudo cp /etc/apt/sources.list $HOME/sources.list.bak
```

Cheers, but it's more the authentication keys that I need to back-up. The sources.list file only contains the URIs.

---

### Post by cariboo on 2009-11-28
Your keys are stored in ~/.gnupg, so if you have backed up your home directory, you have already backed the keys up.

---

### Post by Roger Allott on 2009-12-04
> **cariboo907 said:**
> Your keys are stored in ~/.gnupg, so if you have backed up your home directory, you have already backed the keys up.

I've done the fresh install now and restored my /home directory, but I'm still getting authentication key errors on Update Manager such as:
```
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 106A92EF1E5F9737
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24C
W: GPG error: http://repository.cairo-dock.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1392A97E41317877
```

---

### Post by halj32 on 2009-12-04
you must tell the pkgmanager where the keys are
---add key---

---

### Post by Roger Allott on 2009-12-04
> **halj32 said:**
> you must tell the pkgmanager where the keys are
---add key---

What is the non-cryptic variant of that response?

---

