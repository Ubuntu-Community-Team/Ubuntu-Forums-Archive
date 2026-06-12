---
title: "Gnome desktop gone"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by steigerjb on 2011-03-18
I did a boo boo. I added the natty repo to my maverick ubuntu to update the themes. While i was in synaptic, it upgraded other stuff. When i rebooted my computer, all i have is the desktop and nautilus. I think somehow gnome was uninstalled. I tried sudo apt-get install gnome but it didn't work.

I couldn't just do update-manager -d because the update manager is gone.

---

### Post by aktiwers on 2011-03-18
```
sudo apt-get install ubuntu-desktop --reinstall
```

But if you updated your entire system, you could be in worse trouble..

---

### Post by steigerjb on 2011-03-18
> **aktiwers said:**
> [code]sudo apt-get install ubuntu-desktop --reinstall

I'll give that a try tomorrow. I shut down my computer for the night.

---

### Post by aaryansh on 2011-03-18
Hey there,
I guess the first thing you should do is remove the natty repos,

```
sudo nano /etc/apt/sources.list
```

Also check your /etc/apt/sources.list.d directory.

Update and fix broken dependencies.

```
sudo apt-get update && sudo apt-get -f check
```

Have fun

P.S - You wouldn't be able to see a desktop without gnome, so it's still there. :)
You Probably will have to manually install some other things though.

---

### Post by steigerjb on 2011-03-19
> **aaryansh said:**
> Hey there,
I guess the first thing you should do is remove the natty repos,

```
sudo nano /etc/apt/sources.list
```

Also check your /etc/apt/sources.list.d directory.

Update and fix broken dependencies.

```
sudo apt-get update && sudo apt-get -f check
```

Have fun

P.S - You wouldn't be able to see a desktop without gnome, so it's still there. :)
You Probably will have to manually install some other things though.

Didnt work...failed to fetch.....

---

### Post by steigerjb on 2011-03-19
I probably need a wired internet connection?

---

### Post by steigerjb on 2011-03-19
I decided to just reinstall

---

