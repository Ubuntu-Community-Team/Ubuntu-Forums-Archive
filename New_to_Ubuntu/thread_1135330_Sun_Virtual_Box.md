---
title: "Sun Virtual Box"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by elleppahc on 2009-04-24
Need Help please.
Just rebuilding system after disastrous 9.04 upgrade.
Problem related to ATI Graphic Card.

I need to instal Sun Virtual Box for 8.10.

Can't find my hard copy of instructions.

Can some one please help

---

### Post by amingv on 2009-04-24
Add this repository:
[noparse]deb http://download.virtualbox.org/virtualbox/debian hardy non-free[/noparse]

Using these instrucctions:
[https://help.ubuntu.com/8.10/add-applications/C/extra-repositories.html#extra-repositories-adding](https://help.ubuntu.com/8.10/add-applications/C/extra-repositories.html#extra-repositories-adding)

With this key:
[http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc)

And then do

```
sudo aptitude update
sudo aptitude install virtualbox2.2
```

But how is that related to your ATI card?

---

### Post by kanikilu on 2009-04-24
That should work, but you can always reference the official site: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) (list of repositories and instructions are listed below the manual download options).

---

### Post by Didius Falco on 2009-04-24
Here is a direct link to a PDF of the User Manual:

[http://download.virtualbox.org/virtualbox/2.2.0/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.2.0/UserManual.pdf)

---

### Post by elleppahc on 2009-04-24
I had nooo display after upgrade as I have an ATI Radeon 1600 Pro  which appears not to be supported in 9.10.
As a result I have had to reinstall every thing. I used virtual box to run Windows xp in as My family tree programme is not ubuntu capable.
As I am reasonably new too ubuntu, I am still learning the processes, installing ubuntu programmes is not my strong point

---

