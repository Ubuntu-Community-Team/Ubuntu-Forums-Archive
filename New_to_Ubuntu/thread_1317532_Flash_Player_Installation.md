---
title: "Flash Player Installation"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by ZenChrono on 2009-11-06
I tried to install Flash player by using the command 
sudo apt-get install flashplugin-nonfree
but then this happens 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
Any help?

---

### Post by madverb on 2009-11-06
sudo apt-get install flashplugin-installer

---

### Post by ZenChrono on 2009-11-06
did that and this happened 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-installer

---

### Post by madverb on 2009-11-06
System > Administration > Software Sources

Make sure Universe, Restricted and Multiverse are ticked.

Then try again.

---

### Post by ZenChrono on 2009-11-06
there is no software sources under administrative

---

### Post by MelDJ on 2009-11-06
get the .deb package for flash from: [http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ)

---

### Post by wojox on 2009-11-06
Sure it does:

```

wojox@wojox-desktop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for wojox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.

```


Try:

```
sudo apt-get update
```

---

### Post by RochJer on 2009-11-07
Try going to Administration>Synaptic Package Manager then type in flashplugin-nonfree and see if that is installed or not - you will notice the checkbox is either white or green. If you see green, it's installed. If not, click on it then press apply and the package manager should download/apply installed items for your flashplugin.

---

