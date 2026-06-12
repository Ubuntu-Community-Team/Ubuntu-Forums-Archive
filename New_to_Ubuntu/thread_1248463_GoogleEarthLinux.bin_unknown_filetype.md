---
title: "GoogleEarthLinux.bin: unknown filetype"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by njegbers on 2009-08-24
I want to install Google Earth for Linux, but Ubuntu considers the file GoogleEarthLinux.bin an unknown filetype.
O.
How can I install Google Earth for Linux, then?

---

### Post by MelDJ on 2009-08-24
tried this?
[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/)

---

### Post by twosev on 2009-08-24
Hi! Instead of installing it by hand just try to use medibuntu repository. It already contains packages related to google earth.
Add the next line into /etc/apt/sources.list:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #Medibuntu - Ubuntu 9.04 "jaunty jackalope"

Then as usual:
sudo apt-get update && sudo apt-get install googleearth

Good luck.

---

### Post by njegbers on 2009-08-24
> **MelDJ said:**
> tried this?
[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/)
Wasn't allowed to save the sources.list file. But this one worked fine.
Thank you!

---

### Post by hyperdude111 on 2009-08-24
You need to be root to save the sources .lst use "sudo"

To isntall the Googleearthlinux.bin just make the .bin executable then run it in terminal.

---

### Post by davidsrsb on 2009-08-24
I install Googleearth as user and run "sh Googleearth.bin"

---

### Post by sandyd on 2009-08-24
to edit /etc/apt/sources.lsit, you need to do
```

gksudo gedit /etc/apt/sources.list

```
in the terminal.

---

### Post by Zoot7 on 2009-08-24
> **njegbers said:**
> I want to install Google Earth for Linux, but Ubuntu considers the file GoogleEarthLinux.bin an unknown filetype.
O.
How can I install Google Earth for Linux, then?
Make the file you downloaded executable with the following command:
```
chmod +x GoogleEarthLinux.bin
```
And execute it with
```
./GoogleEarthLinux.bin
```
And that'll install Google Earth for you.

---

