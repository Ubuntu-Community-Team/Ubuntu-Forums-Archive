---
title: "Banshee Help"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by lilredcougar07 on 2009-08-29
Hey all. I'm trying to add the PPA from the Banshee team to my software sources. I do exactly what it tells me to do on the launchpad website, but when I try and reload the sources it tells me that the one from launchpad because "the signatures could not be verified because the public key is not available. NO_PUBKEY 4874D3686E80C6B7" Is anyone able/willing to help me out with this? I'd greatly appreciate it.

---

### Post by powel212 on 2009-08-29
You will need to import the key as follows.

first save the attached banshee Key.

Then

Go to "System\Administration\Software sources

click the authentication tab and then click import

then choose the Key that you saved a moment ago, hit ok and then 

now run

```
sudo apt-get update && sudo apt-get upgrade
```

and your done.


I hope that helps

Powel

---

