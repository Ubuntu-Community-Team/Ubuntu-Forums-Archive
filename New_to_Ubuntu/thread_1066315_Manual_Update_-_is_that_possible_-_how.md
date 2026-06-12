---
title: "Manual Update - is that possible? - how?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by dmurat on 2009-02-10
Hi there,
I need to update my Ubuntu 8.10 manually. What I mean is, install the update from a Windows machine, copy it to a usb disk and then run it on my Ubuntu.

I still couldn't establish an internet connection in Ubuntu (wrong driver loaded) and I first need to update to solve this problem. Since I don't have an internet connection, Ubuntu cannot update. 

Can an update be done manually? Downloading from a Windows machine and copying and pasting to Ubuntu? If so, where can I find these necessary update files?

Thanks.

---

### Post by UbuntuNerd on 2009-02-10
you can check here for some updates:
[http://archive.canonical.com/dists/]("http://archive.canonical.com/dists/")

---

### Post by dmurat on 2009-02-10
ok i guess that its here [http://archive.canonical.com/dists/intrepid-updates/](http://archive.canonical.com/dists/intrepid-updates/)

but what do i do with them? download all files in the directory and then what? copy and paste them what folder?

---

### Post by UbuntuNerd on 2009-02-10
/var/lib/apt/lists/ is where the files downloaded by 'apt-get update' are
placed, but im not sure if just downloading the update packages and putting them there will work.

---

### Post by UbuntuNerd on 2009-02-12
I found this link 
[http://keryx.betaserver.org/]("http://keryx.betaserver.org/")

---

### Post by Metallion on 2009-02-12
If it's just one program, you could download the .deb from packages.buntu.com and then copy it to your linux box. That would of course be a big hassle to do for a bunch of updates. Not sure what would be a good way for that.

---

### Post by Brandel Valico on 2009-02-12
Is the linux box hard wired or wireless your trying to update? 

Not really helpful I know just curious is all.

---

### Post by EXCiD3 on 2009-02-12
I'm the developer of Keryx. If you need any help with it, just let me know. :)

---

### Post by mc4100 on 2009-02-12
> Ok i guess that its here [http://archive.canonical.com/dists/intrepid-updates/](http://archive.canonical.com/dists/intrepid-updates/)
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
... or more specifically, [http://packages.ubuntu.com/intrepid-updates/allpackages](http://packages.ubuntu.com/intrepid-updates/allpackages) which will take about a year to load!
> **dmurat said:**
> Download all files in the directory and then what? copy and paste them what folder?
It's fine to do this is you know specifically what package(s) you need, but not for complete upgrading since you'll need to fetch dependencies too;```
/var/cache/apt/archives
```

---

### Post by UbuntuNerd on 2009-02-12
also check this link on how to make an Ubuntu update cd/dvd
[http://my.opera.com/ubuntunerd1/blog/how-to-create-an-ubuntu-update-cd-dvd]("http://my.opera.com/ubuntunerd1/blog/how-to-create-an-ubuntu-update-cd-dvd")
the only thing is you need another Ubuntu computer that can get online to do it this way.

---

