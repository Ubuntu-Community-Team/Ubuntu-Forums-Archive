---
title: "applcation to open deb files"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Skull Kid on 2009-07-19
Hi, I am using ubuntu netbook remix on my eee PC and I'm trying to install the flash player for firefox. I am trying to install it manually through Adobe's site, but whenever I download the deb file, ubuntu asks me to choose an application to open it with. Can anyone tell me what is the application and where it is located in the system? Thanks

---

### Post by philinux on 2009-07-19
On ubuntu it would be gdebi which is default installed. Can you install it from add/remove or synaptic

or firefox address bar

apt://gdebi

---

### Post by snowpine on 2009-07-19
Better yet, install it from the Ubuntu repository, that way you will receive updates as they are available, and you'll be using a version trusted and tested to work with your Ubuntu release.

```
sudo apt-get install flashplugin-installer
```

(or use the Synaptic Package Manager if you don't like the terminal)

---

### Post by philinux on 2009-07-19
I'm with snowpine on this. Forget windows ways of doing things. Far better to use synaptic package manager. Downloading from ubuntu's servers is the way to go.

---

### Post by Skull Kid on 2009-07-19
Hmm, when i go to synaptic it says gdebi is already installed. I tried reinstalling it but still doesn't work. 

Also, I initally did use synaptic to install the flashplugin.. again it says it's installed but when I try to use something with flash on firefox just a gray box with a large play button appears.. when I click on that play button nothing happens. Thanks for the help

---

### Post by /usr/sbin on 2009-07-19
> **philinux said:**
> I'm with snowpine on this. Forget windows ways of doing things. Far better to use synaptic package manager. Downloading from ubuntu's servers is the way to go.

I had the same problem as you did and this method worked for me.

---

### Post by snowpine on 2009-07-19
> **Skull Kid said:**
> Also, I initally did use synaptic to install the flashplugin.. again it says it's installed but when I try to use something with flash on firefox just a gray box with a large play button appears.. when I click on that play button nothing happens. Thanks for the help

Sounds suspiciously like you also have the Gnash player installed... try uninstalling Gnash (if my theory is correct).

---

### Post by VCoolio on 2009-07-19
use gdebi-gtk or you won't have a gui. Use 'which gdebi-gtk' in terminal to check the location, which is /usr/bin/gdebi-gtk.

---

### Post by fooman on 2009-07-19
> **snowpine said:**
> Sounds suspiciously like you also have the Gnash player installed... try uninstalling Gnash (if my theory is correct).

yeah check that gnash is *not* installed,  if it is then uninstall it....also check for any libswfdec packages and uninstall those as well.

then restart firefox and see if that helps.

---

