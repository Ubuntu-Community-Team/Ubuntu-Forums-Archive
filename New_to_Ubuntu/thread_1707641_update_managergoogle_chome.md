---
title: "update manager/google chome"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by sean neilan on 2011-03-15
When the update manager comes up do I or should go ahead do the updates?Also should I have google chrome when I already have firefox as a web browser and if I don't need chrome how do I remove it from the applications>internet on my control panel?](*,)

---

### Post by Paqman on 2011-03-15
> **sean neilan said:**
> When the update manager comes up do I or should go ahead do the updates?

Yes. At the very least, do all the ones listed under "security updates". These are important. Unless you have severely restricted downloads i'd just go ahead and do them all.

> 
Also should I have google chrome when I already have firefox as a web browser and if I don't need chrome how do I remove it from the applications>internet on my control panel?](*,)

Up to you, use whichever browser you prefer. There's no problem with having two browsers installed.

If you want to completely remove Chrome, just open up Ubuntu Software Centre or Synaptic and uninstall it from there.

---

### Post by _0R10N on 2011-03-15
> **Paqman said:**
> Yes. At the very least, do all the ones listed under "security updates". These are important. Unless you have severely restricted downloads i'd just go ahead and do them all.



Up to you, use whichever browser you prefer. There's no problem with having two browsers installed.

If you want to completely remove Chrome, just open up Ubuntu Software Centre or Synaptic and uninstall it from there.

About uninstalling chrome, since I assume you've donwloaded and installed the .deb package from google page, a shortcut to delete it is by

```
sudo aptitude purge chrome
```

Since I haven't installed it, I don't know the exact name of the package, but if you press <TAB> a couple of times, it will autocomplete the package name.

---

### Post by Ozitraveller on 2011-03-15
chromium-browser

---

### Post by Paqman on 2011-03-15
> **Ozitraveller said:**
> chromium-browser

That's Chromium. The package name for Chrome is google-chrome-stable.

Just open up USC and search though, you don't need to know the exact package name.

---

