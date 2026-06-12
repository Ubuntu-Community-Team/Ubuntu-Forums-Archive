---
title: "Upgrade notification icon in system tray"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by tarahmarie on 2009-05-18
Hi, all:

I don't want the 9.04 upgrade notification icon in the system tray; I'd rather stick with Intrepid for a bit.  There doesn't seem to be any way to remove it permanently without shutting down Adept Updater.  

Does anyone know how to do this?

Thanks!

---

### Post by taurus on 2009-05-18
Did you set your /etc/apt/sources.list to intrepid or jaunty?

```
cat /etc/apt/sources.list
```

---

### Post by tarahmarie on 2009-05-18
> **taurus said:**
> Did you set your /etc/apt/sources.list to intrepid or jaunty?

```
cat /etc/apt/sources.list
```

There are no Jaunty deb lines in my sources list.

---

### Post by pastalavista on 2009-05-18
System > Administration > Software Sources >> Update tab >> uncheck everthing....

or even better

below where it says distribution upgrades select never

---

### Post by taurus on 2009-05-18
Make sure you have closed down the update manager.  Then, post the outputs of these two commands from a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by tarahmarie on 2009-05-20
> **taurus said:**
> Make sure you have closed down the update manager.  Then, post the outputs of these two commands from a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

I have already gotten the upgrade; I simply don't wish to see the notification for that upgrade in the system tray.  

Any ideas?

Thanks!

---

### Post by faraz_k86 on 2009-05-20
did u try what pastalavista  said?

---

### Post by tarahmarie on 2009-05-20
> **faraz_k86 said:**
> did u try what pastalavista  said?

I did, but as I'm using Kubuntu and not Ubuntu, the settings are not in the same place.  I went to Adept and looked at the settings there; there were no correlates to the same settings in Gnome.

---

