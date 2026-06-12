---
title: "pdf programs"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by trevorc on 2009-11-03
I cant get any of the PDF programs in Package Manager to load I get the following error
E: /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1intrepid1_i386.deb: subprocess new pre-removal script returned error exit status 2
What do I do nw please

---

### Post by emigrant on 2009-11-03
you already have an built-in pdf program:
type in terminal

```

evince

```

---

### Post by 3rdalbum on 2009-11-03
> **trevorc said:**
> I cant get any of the PDF programs in Package Manager to load I get the following error
E: /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1intrepid1_i386.deb: subprocess new pre-removal script returned error exit status 2
What do I do nw please

This may be because the version of Flash Plugin referenced in the package is old and no longer on the Adobe server.

You should either upgrade to a later version of Ubuntu, or get the Flash Plugin package from [www.adobe.com](www.adobe.com) and put the "libflashplayer.so" file from the package into the /usr/lib/mozilla/plugins folder.

Also, Flash Plugin only does Flash; it doesn't do PDFs. You already have a PDF viewer preinstalled (it's called Evince).

---

