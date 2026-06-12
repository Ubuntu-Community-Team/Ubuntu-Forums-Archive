---
title: "adding more available program"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by ave2 on 2009-09-01
I enabled compiz fusion on my machine by following a tutorial on the internet- they said you have to install emerald and I think it was (compiz config settings manager) but not sure

anyway when I tried to explain it to a friend of mine, he went into synaptic package manager and typed in emerald and nothing came up. Now thinking back right in the beginning im sure I had to enable/add a library or something in the terminal, in order to gain access to a lot more of the programs that I would need to download, and was wondering what it could be

---

### Post by nhasian on 2009-09-01
actually compiz is installed by default.  you dont need to install it.  the configuration manager however is not.  you can install it from a terminal with the command:

```
sudo apt-get install compizconfig-settings-manager 
```

---

### Post by anujpathania on 2009-09-01
Try typing and searching "ccsm" in  synaptic package manager.

---

### Post by Soulcage on 2009-09-01
try: sudo apt-get update ????

---

### Post by nhasian on 2009-09-01
> **Soulcage said:**
> try: sudo apt-get update ????

apt-get update only refreshes the list of applications available in the repository.  it doesnt install anything.

```
man apt-get
```

---

### Post by 3rdalbum on 2009-09-01
You don't need Emerald - it's just a fancy window decorator. If you want it, it's in the Universe repository (System > Administration > Software Sources and enable the top four checkboxes).

I'm a little worried that you "followed a tutorial" on the Internet to get Compiz Fusion, as it comes preinstalled these days, and the tutorials for installing Compiz on earlier versions of Ubuntu can mess up a modern system. If you can go to System > Preferences > Appearance, click on the Visual Effects tab and then click "Extra", then you've got Compiz.

---

### Post by ave2 on 2009-09-01
> **3rdalbum said:**
> You don't need Emerald - it's just a fancy window decorator. If you want it, it's in the Universe repository (System > Administration > Software Sources and enable the top four checkboxes).

I'm a little worried that you "followed a tutorial" on the Internet to get Compiz Fusion, as it comes preinstalled these days, and the tutorials for installing Compiz on earlier versions of Ubuntu can mess up a modern system. If you can go to System > Preferences > Appearance, click on the Visual Effects tab and then click "Extra", then you've got Compiz.

The tutorial just told me to install the config manager....

The biggest problem is that none of the programs are coming up in the synaptic package manager- wine, emerald, the compiz config manager.....
The top four icons have been checked as suggested above (inc univers and multiverse) and the manager has been refreshed, but they are still no where to be found- I wonder what could be the problem??

---

### Post by nhasian on 2009-09-01
> **ave2 said:**
> The biggest problem is that none of the programs are coming up in the synaptic package manager- wine, emerald, the compiz config manager

if you copy and paste the text into a terminal exactly as i typed it, it will install the compizconfig-settings-manager.  Then you can find it in System->Preferences

---

### Post by Soulcage on 2009-09-02
When you run sudo apt-get update for the first time it adds packages that weren't there before.

---

### Post by zkriesse on 2009-09-02
Go to applications/add-remove...type in what you want there but make sure that the drop down from the top is set to All Available Applications.

---

