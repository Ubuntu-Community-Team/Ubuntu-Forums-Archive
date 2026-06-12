---
title: "sudo apt-get update"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by McTwitch on 2010-08-09
Alright, stupid beginner question, but I just want to make sure. The command "sudo apt-get update" that actually updates it, right? It doesn't just give you the list.

---

### Post by McTwitch on 2010-08-09
And while I have your attention, I did the update command, and I got this

```
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```
How does one remedy this?

---

### Post by Bachstelze on 2010-08-09
It just updates the list of installable packages. apt-get upgrade will upgrade all installed packages (provided that would not cause installation or removal of other packages).

You have to install the key used to sign packages of the medibuntu repository. The website should tell you how to do this.

---

### Post by Perfect Storm on 2010-08-09
> **McTwitch said:**
> And while I have your attention, I did the update command, and I got this

```
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```
How does one remedy this?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Seems you forgot to run, part of the whole medibuntu command. Try with
```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by McTwitch on 2010-08-09
Okay, I'm at the medibuntu site, but I'm not finding anything about the key.

---

### Post by McTwitch on 2010-08-09
Thank you Artificial Intelligence.

---

### Post by McTwitch on 2010-08-09
and the "sudo apt-get autoremove". What will that do exactly?

---

### Post by Bachstelze on 2010-08-09
It will remove all packages that were installed as a dependency of another packages and are not needed anymore.

For example, if you install package A, and package A depends on package B, package B will be installed as well. If you uninstall package A later, or if a newer version of package A doesn't need package B anymore, package B will not be automatically uninstalled. apt-get autoremove uninstalls such packages.

---

### Post by KdotJ on 2010-08-09
Another common joint command that people run is to and the update and upgrade commands together

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by McTwitch on 2010-08-09
Thanks, I'll start using the compound command.

---

