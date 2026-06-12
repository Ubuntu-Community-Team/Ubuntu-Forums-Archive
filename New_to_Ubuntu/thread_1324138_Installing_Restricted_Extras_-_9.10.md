---
title: "Installing Restricted Extras - 9.10"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-11-12
Hello all. Does anyone know how to install all the restricted extras in Ubuntu 9.10? I searched in the Synaptic Manager but couldn't find the package. Thanks for the help!

---

### Post by ukripper on 2009-11-12
> **UnknownFear said:**
> Hello all. Does anyone know how to install all the restricted extras in Ubuntu 9.10? I searched in the Synaptic Manager but couldn't find the package. Thanks for the help!

Go to applications-->Ubuntu software center--> type in search box "ubuntu restricted extras" install from there

---

### Post by lotharmat on 2009-11-12
This ought to do it!

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Tholley on 2009-11-12
This link will really help you out... it is good to read thru the whole thing, but what you are looking for is under the Multimedia section.
 
[http://sites.google.com/site/easylinuxtipsproject/Home](http://sites.google.com/site/easylinuxtipsproject/Home)
 
 
Cheers!

---

### Post by UnknownFear on 2009-11-12
> **ukripper said:**
> Go to applications-->Ubuntu software center--> type in search box "ubuntu restricted extras" install from there

I read on a UbuntuWiki that there was a bug in 9.10 that wouldn't let you install it from the Ubuntu software center; guess I should have checked there first.

> **lotharmat said:**
> This ought to do it!

```
sudo apt-get install ubuntu-restricted-extras
```

I'll check the Software center first, but thanks for the terminal link! I knew it was something along the lines of that code, but wasn't sure. I like to install things via terminal anyway, makes me feel cool :P

---

### Post by sisco311 on 2009-11-12
ubuntu-restricted-extras is in the multiverse repositories. 

go to System > Administration > Software Sources to enable it.

or:
```
sudo software-properties-gtk -e  multiverse
sudo apt-get update 
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by UnknownFear on 2009-11-13
@lotharmat: Worked perfectly, thanks!!

---

### Post by lotharmat on 2009-11-13
Glad to be of help!

---

### Post by UnknownFear on 2009-11-13
I love Linux so much!!! It is my main OS, but I do use Windows for games.

---

