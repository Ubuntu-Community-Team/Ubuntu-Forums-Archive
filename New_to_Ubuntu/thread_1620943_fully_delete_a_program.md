---
title: "fully delete a program?"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by novus721 on 2010-11-13
I can't believe I'm having such an issue with this.

I want to fully delete and reinstall my Banshee due to iPod issues that I'm having.

Each time I've deleted it, it's come back with my old playlists, so I know something is sticking around.

I've done:

sudo apt-get --purge remove banshee

...and have also deleted the /usr/lib/banshee-1 files as well, as well as the /usr/share/ gnome help files


I've followed each remove command with apt-get clean, but to no effect...

---

### Post by brookie on 2010-11-13
linux programs usually have a config file in your home directory. hit ctrl + h in your home dir to see hidden files. delete all the banshee stuff. also do a search for banshee to find other left over stuff. i don't use it personally so i don't know where the config files are. good luck. :)

---

### Post by uRock on 2010-11-13
Does Banshee by any chance have a hidden folder in the Home folder?

Does uninstalling via Synaptic Package Manager and selecting to "Mark for Complete Removal" act any differently?

---

### Post by Decatf on 2010-11-13
Remove the ~/.config/banshee-1 directory.

---

### Post by novus721 on 2010-11-13
> **Decatf said:**
> Remove the ~/.config/banshee-1 directory.

Found and deleted! Also deleted a banshee-extensions-community folder in my home dir

As a note, there was no hidden banshee file in my home dir itself

Also, "complete removal" in the package manager did not make a difference...

Thanks for the help, remarking as solved. While it didn't fix my iPod syncing issue, it did get rid of all the residual banshee files.

---

