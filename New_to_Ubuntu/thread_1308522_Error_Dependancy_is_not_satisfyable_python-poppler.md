---
title: "Error: Dependancy is not satisfyable: python-poppler"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by green0eggs on 2009-10-31
Hello!

So I'm trying to install a .deb file and I get the error message telling me to get the package: python-poppler only it isn't in Synaptic Package manager and 
```
sudo apt-get python-poppler
``` gives ```
 E: Invalid operation python-poppler
```

The only think that I can think is that the .deb I'm trying to install is [from here]("http://gummi.midnightcoding.org/?page_id=6") which is software for Ubuntu 9.04 and I'm running 8.10. Could this be my problem? Probably.

Cheers


*EDIT: just noticed the spelling error in the thread title, how embarrassing!*

---

### Post by diesch on 2009-10-31
It's

```
sudo apt-get install python-poppler
```

---

### Post by green0eggs on 2009-10-31
> **diesch said:**
> It's

```
sudo apt-get install python-poppler
```

:oops:

Ok yes that was obvious. Now I'm getting:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python-poppler

```

---

### Post by happyhamster on 2009-10-31
That package doesn't exist for Intrepid, but you could try the Jaunty version. Download:

[http://packages.ubuntu.com/jaunty/python-poppler](http://packages.ubuntu.com/jaunty/python-poppler)

Make sure you get the right architecture (i386 for 32 bits ubuntu or amd64 for 64 bits). Just double-click the .deb file and keep your fingers crossed: there's no guarantee that it will work. Reason is because that package might depend on some other package that's not in Intrepid and so on. The installer will tell you of any conflicts.

---

### Post by kevdog on 2009-10-31
Im not sure what the actual phython-poppler package is named.  Since its a dependency, its probably something like libpopular or something.

Search for python-poppler within the repositories using:

sudo apt-cache search poppler

or 

sudo apt-cache search python | grep poppler

or

sudo apt-cache search python-poppler

Once you find the package (again likely to begin with the lib prefix), install it with:

sudo aptitude install <package_name>

Hopefully that helps.

---

### Post by green0eggs on 2009-11-01
> **happyhamster said:**
> keep your fingers crossed: there's no guarantee that it will work. Reason is because that package might depend on some other package that's not in Intrepid and so on. 

Yep more Dependancy not satisfiable. I guess I'll get round to upgrading to Jaunty or Karmic eventually. Thanks for the help Hamster and Kev!

---

