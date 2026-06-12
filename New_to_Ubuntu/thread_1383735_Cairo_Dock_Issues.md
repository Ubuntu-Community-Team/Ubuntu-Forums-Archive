---
title: "Cairo Dock Issues"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by turboopugsleylx on 2010-01-17
Hey guys I tried installing cairo dock thru synaptic after doing a fresh install and when I download it all I have in one theme on there....where is all the cairodock themes...also how do I get the most current cairo dock edition?

---

### Post by tom4everitt on 2010-01-17
Usually themes are in a different package. Try to find a package named 

cairo-themes,
cairo-extensions,
cairo-extras

or something like that. 

If you want a newer edition then the one in respositories, you will have to find their website and download the latest version from there. 

EDIT: If you're not using the latest ubuntu, upgrading to the latest ubuntu will get you more updated packages.

---

### Post by fabounet on 2010-01-17
actually there is no themes package, they are all available on the server, which is temporarily down.
so until it comes back, launch the dock with 
```
cairo-dock -S http://themes.cairo-dock.vef.fr
```

---

