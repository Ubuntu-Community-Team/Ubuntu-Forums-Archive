---
title: "Package installer doesn't install StarDict"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by al.adab on 2009-04-29
hello

I'm trying to install StarDict on Ubuntu 9.04 after downloading it from the StarDict site (and choosing the package for Linux Debian) and choosing to open it with "package installer". 

The installer gives me the following error message: 

"Error: Dependency is not satisfiable: libgucharmap6"

Does anyone know how to fix this? Thnaks.

---

### Post by sahabcse on 2009-04-29
sudo apt-get install stardic

---

### Post by Pollox on 2009-04-29
It's just saying that libgucharmap6 is not currently available in your repositories, and you need it to run this package.  You could try to find it/enable a repository that has it.  A better option is to just install stardict from the repositories (enable the "universe" repository).  You can do as the above user suggested in terminal, or try it in a gui like Synaptic.

---

### Post by smudi on 2009-04-29
You should always prefer installing via the repositories rather than d/l packages from sites, as it automagically handles dependencies for you.

You're not on windows anymore ;)

---

### Post by al.adab on 2009-04-29
thanks both.

if I run "sudo apt-get install stardic" I get the Chinese-English dict version (whose script is in Chinese...). Not extremely handy to me. 

The alternative IS to get the International version from Synaptics (didn't know I'd find it there).

---

### Post by sahabcse on 2009-04-29
hi 

run

sudo apt-get install gucharmap

---

