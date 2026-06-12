---
title: "Ubuntu Software Center never loading."
date: 2011-05-08
forum: New to Ubuntu
---

### Post by Melophonic on 2011-05-08
Recently, I went to look for some apps at the USC (Ubuntu Software Center), and suddenly when I choose a type of app (Internet), the loading sphere appears. Yes, it's loading. Been some minutes now, hasn't loaded yet.

Well, USC usually loads pretty  quick, is this because of my Internet connection or because there may be a problem? any tips?

NOTE: I've tried several other types, closed and reopened the USC, tried searching, and it just doesn't load.

Even "Installed Software" section doesn't load, and now I'm pretty sure it's not my Internet connection.
Another NOTE: Restarting or simply shutting down does not fix this problem.

---

### Post by Rex Bouwense on 2011-05-09
Does the Synaptic Package Manager load properly?  If it does, perhaps you have a broken package.  Can you check for updates via the command line?

---

### Post by Locke_99GS on 2011-05-09
Start *software-center* from a terminal and note any peculiar output when this is happening.

---

### Post by Melophonic on 2011-05-09
> **Rex Bouwense said:**
> Does the Synaptic Package Manager load properly?  If it does, perhaps you have a broken package.  Can you check for updates via the command line?

This is what happens when I try opening the Synaptic Package Manager.
An error shows up saying the following:
[I]E: Type '/t/tiheum/equinox/ubuntu' is not known on line 3 in source list /etc/apt/sources.list.d/tiheum-equinox-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct this problem.
E: _cache->open() failed, please report[/I]

How do I fix this?

---

### Post by Melophonic on 2011-05-09
Please, I'm in sort of a hurry, and I really need the USC right now.
Does anyone know how to fix this? I posted the error output above.

---

### Post by Locke_99GS on 2011-05-10
```
gksudo gedit /etc/apt/sources.list.d/tiheum-equinox-natty.list
```

Check out the third line in that file, and make sure it's proper. It should begin with "deb" and be followed by a web address, following that will likely be the name of your distribution, "natty".

If it confuses you, just paste the contents of that file here for us to look at.

---

