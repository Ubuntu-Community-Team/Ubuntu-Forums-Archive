---
title: "what kind of packages will dpkg deal with"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by flylehe on 2009-09-07
Hi,
It seems that dpkg is not aware of packages installed from source and installed from some cdrom or .iso (like Matlab). I found this from dpkg -l. Nothing I mentioned shows from the list it gives.

Does it mean dpkg can only manage those packages installed via apt-get install? Is Synaptic Package Manager same as dpkg besides being Graphical?

Is it possible to manage those packages installed from source or cdrom or .iso just as conveniently as by dpkg or synaptic Package Manager?

Thanks and regards!

---

### Post by flylehe on 2009-09-07
Hi,
It seems that dpkg is not aware of packages installed from source and installed from some cdrom or .iso (like Matlab). I found this from dpkg -l. Nothing I mentioned shows from the list it gives.

Does it mean dpkg can only manage those packages installed via apt-get install? Is Synaptic Package Manager same as dpkg besides being Graphical?

Is it possible to manage those packages installed from source or cdrom or .iso just as conveniently as by dpkg or synaptic Package Manager?

Thanks and regards!

---

### Post by cariboo on 2009-09-07
Dpkg  only deals with .deb files. If you are installing from source, install checkinstall and use it instead of typing make. It will create a .deb.file for you.

---

### Post by Windows Nerd on 2009-09-07
Dpkg will deal with the same things as apt-get, I believe. 

Scott

---

