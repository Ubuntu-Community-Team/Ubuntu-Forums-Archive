---
title: "Problems reinstalling GIMP."
date: 2010-08-15
forum: New to Ubuntu
---

### Post by aidenscool09 on 2010-08-15
Ok, well, I removed GIMP because I messed up all the settings and it wasn't working properly, and when I try to reinstall it says:
```
gimp:
  Depends: libgimp2.0 (>=2.6.10) but 2.6.7-1ubuntu1.1 is to be installed
  Depends: libatk1.0-0 (>=1.29.3) but 1.28.0-0ubuntu1 is to be installed
  Depends: libc6 (>=2.11) but 2.10.1-0ubuntu17 is to be installed
  Depends: libfontconfig1 (>=2.8.0) but 2.6.0-1ubuntu12 is to be installed
  Depends: libglib2.0-0 (>=2.23.5) but 2.22.3-0ubuntu1 is to be installed
  Depends: libgtk2.0-0 (>=2.20.0) but 2.18.3-1ubuntu2.2 is to be installed


```

---

### Post by jtarin on 2010-08-15
How did you remove it?

---

### Post by aidenscool09 on 2010-08-15
I did:
```
sudo apt-get remove gimp gimp-data
```

---

### Post by jcolyn on 2010-08-15
Sounds like you may have some broken package dependencies. Try fixing them in your package manager..

---

### Post by aidenscool09 on 2010-08-15
Yeah, it did say "E: Broken packages" but when I open Synaptic, I put the "Broken" filter on and nothing shows up. I also tried 
```
 sudo apt-get install -f 
```
and
```
 sudo apt-get install -f gimp 
```

---

### Post by aidenscool09 on 2010-08-15
Also, I installed GIMPShop for now while i try and fix the original GIMP. The thing is, GIMPShop opens up by just typing
```
 gimp
```
into the terminal...

---

### Post by jtarin on 2010-08-15
> Yeah, it did say "E: Broken packages" but when I open Synaptic, I put the "Broken" filter on and nothing shows up.Enter gimp in the search box before applying the filter. There is also a selection from the drop-down menu above to fix broken packages.Gimp-shop shares libs Standard Gimp.....that is why you can use the cammand gimp in the terminal. I would completely uninstall both and then reinstall Gimp.

---

### Post by jtarin on 2010-08-15
> **aidenscool09 said:**
> I did:
```
sudo apt-get remove gimp gimp-data
```
Should have been simply go into Synaptic and choose to remove Gimp completely and all its config files to insure you remove everything.

---

### Post by aidenscool09 on 2010-08-15
Ok, thanks, it's just that I'm used to doing most operations through the terminal.

---

### Post by aidenscool09 on 2010-08-15
Also, nothing came up by selecting "Fix broken packages" or by putting "gimp" into the search bar and then adding the filter.

---

### Post by jtarin on 2010-08-15
As I said earlier....> I would completely uninstall both and then reinstall Gimp.

---

### Post by aidenscool09 on 2010-08-15
I tried that, same thing.

---

### Post by jtarin on 2010-08-15
udo apt-get update
sudo apt-get -f install
sudo dpkg --remove --force-remove-reinstreq gimp

---

### Post by jtarin on 2010-08-15
udo apt-get update
sudo apt-get -f install
sudo dpkg --remove --force-remove-reinstreq gimp


If an installation breaks in the middle of the process and you find that it's no longer possible to install or remove packages, try running these two commands:

     # apt-get -f install
     # dpkg --configure -a

---

### Post by aidenscool09 on 2010-08-16
That didn't work... sudo apt-get -f install did nothing.
And sudo dpkg --remove --force-remove-reinstreq gimp just said 
```
dpkg: warning: ignoring request to remove gimp which isn't installed.
```

---

### Post by jtarin on 2010-08-16
Throw this at it.```
sudo dpkg --configure -a
```

---

### Post by aidenscool09 on 2010-08-16
Still nothing :(

---

### Post by aidenscool09 on 2010-09-25
Ok, fixed it, don't know how but I did. I just tried installing it after the last update and it worked and now it works perfectly. Thanks anyway guys.

---

