---
title: "uninstalling software"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by manuleka on 2009-02-05
i installed perlmon
[http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html](http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html)

i'm just wondering how to uninstall softwares that are not on synaptic... i installed perlmon from site above but i have no need for it and i want to uninstall it...

anyone help please

---

### Post by lykwydchykyn on 2009-02-05
Which method did you use to install?  The perl script or the .deb package?

---

### Post by stchman on 2009-02-05
> **manuleka said:**
> i installed perlmon
[http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html](http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html)

i'm just wondering how to uninstall softwares that are not on synaptic... i installed perlmon from site above but i have no need for it and i want to uninstall it...

anyone help please
If you installed via the .deb package use the following:

```

sudo apt-get autoremove <package_name>

```

The .tar.gz archive you will have to hunt around.

---

### Post by manuleka on 2009-02-06
i think it was a perl script... package came with an Installer file... not sure what that means tho in regards to perl or deb package installation

---

### Post by lykwydchykyn on 2009-02-06
> **manuleka said:**
> i think it was a perl script... package came with an Installer file... not sure what that means tho in regards to perl or deb package installation

If it had an installer file it was probably a perl script.  Did the package you downloaded end in .zip or .deb?

---

### Post by manuleka on 2009-02-06
.zip package

---

### Post by lykwydchykyn on 2009-02-06
Looks like it installs to /usr/share/perlmon.  I'd check that directory for an uninstall script.  Otherwise you'll probably have to hunt down all the files and delete them.

If you do:
```

sudo updatedb
sudo locate -i perlmon

```

You should be able to find most of the places it's hiding.

Good lesson in why package managers rock.

---

### Post by manuleka on 2009-02-06
so how do i uninstall the script? or scripts?

---

### Post by lykwydchykyn on 2009-02-09
> **manuleka said:**
> so how do i uninstall the script? or scripts?

Maybe we're not understanding each other, but I thought I just told you that.

---

