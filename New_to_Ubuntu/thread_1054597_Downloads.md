---
title: "Downloads"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by dmalloch on 2009-01-29
I enjoy using the flight simulator Flightgear and would like to download the latest version (v1.9.0).  Although I installed the previous version (1.0.0) using Synaptic the newer one seems not to be there.  It can be downloaded at [http://www.proformatique.org/deb/](http://www.proformatique.org/deb/) but is presented in a way that I don't understand.  It is just a list of folders and their contents.  Could someone give me some guidance in dealing with this format?

Thanks.

---

### Post by snova on 2009-01-29
It appears to be a repository. If you add this URL to your list of sources, then FlightGear will be updated from this repository automatically.

Open System -> Administration -> Software Sources, click Third Party Software, Add, and type in that URL.

Also, download the **proformatique.asc** file you see there and import it under the Authentication tab.

Open Synaptic (System -> Administration -> Synaptic) and press Refresh. From now on you should be able to update from this repo (which you should do now).

---

### Post by AlucardArg on 2009-01-29
Or, the Ubuntu package is in /deb/pool/main/f/flightgear
Anyway, it's good to have it in the repos, as it'll update automatically with Synaptic

---

### Post by dmalloch on 2009-01-29
Thanks to both of you for the guidance.  However, I'm inexperienced enough with these things that I still don't have it quite right.  When I try to add a new APT line in the third-party tab of Software Sources it will not accept my entry.   I entered the URL [http://www.proformatique.org/deb/](http://www.proformatique.org/deb/) but that does not seem to be enough.  Is there something more that should be there?

Also, in downloading the file proformatique.asc from the repository do I use the command 'wget -q [http://proformatique.org/deb/proformatique.asc](http://proformatique.org/deb/proformatique.asc) -O- | sudo apt-key add -' as written out in their readme file?  Will apt-key supply the authentication needed by Software Sources?

---

### Post by snova on 2009-01-29
Ah! I made a mistake. The input line should be:

```
deb http://www.proformatique.org/deb/ intrepid main
```

Try that instead.

[QUOTE=dmalloch]Also, in downloading the file proformatique.asc from the repository do I use the command 'wget -q [http://proformatique.org/deb/proformatique.asc](http://proformatique.org/deb/proformatique.asc) -O- | sudo apt-key add -' as written out in their readme file? Will apt-key supply the authentication needed by Software Sources?[/QUOTE]

It'd do the same thing as it would through the Authentication tab; whichever you prefer.

(At least I think so- I never use this tool, which explains my mistake!)

---

### Post by dmalloch on 2009-01-29
Thanks for all the patient help.  Everything is now in good order.

---

