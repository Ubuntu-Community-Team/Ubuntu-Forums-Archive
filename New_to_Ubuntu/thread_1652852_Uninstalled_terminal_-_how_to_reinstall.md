---
title: "Uninstalled terminal - how to reinstall?"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by Esotera on 2010-12-25
I've recently been pruning installed software and accidentally uninstalled the terminal through ubuntu software centre. 
Tried reinstalling through this, but get the following message (for all programs, not just the terminal):

"Requires installation of untrusted packages:
The action would require the installation of packages from unauthenticated sources.
Details: gnome-terminal"

Is there any way to repair this without reinstalling the OS? I'm running 10.04 - thanks in advance!

---

### Post by Griffiss on 2010-12-25
You can install it with Synaptic: Menu > System > Administration > Synaptic Package Manager

Search for 'gnome-terminal'

---

### Post by H4F on 2010-12-25
you can always do :
sudo apt-get install gnome-terminal 
in the command line

---

### Post by Esotera on 2010-12-25
Thank you Griffis :D worked a charm!

---

### Post by mcduck on 2010-12-26
Also, the warning message you get is usually a result from adding some extra software repository, but not adding the signing key for that repository.

Without the signing key the downloads can't be authenticated, and you'll get a warning about it every time you install anything. It shouldn't stop you from installing things, though, but you should still add the missing key to get rid of the warning.

---

### Post by Esotera on 2010-12-28
Thank you - I've read a bit about public and private gpg keys and how to install them via the terminal, but have no idea of the location of the key that needs to be downloaded. The system is also having trouble checking for updates - would this be fixed by getting the key?

---

### Post by karthick87 on 2010-12-28
What's the trouble?Post the output of
```
sudo apt-get update
```

---

### Post by Esotera on 2010-12-28
E: The method driver /usr/lib/apt/methods/hyyp could not be found.
E: The method driver /usr/lib/apt/methods/hyyp could not be found.

For sudo apt-get update, the same occurs using update manager. And when attempting to install any program via ubuntu software centre the same problem occurs:

The action would require the installation of packages from unauthenticated sources.
Details: "program_being_installed"

---

