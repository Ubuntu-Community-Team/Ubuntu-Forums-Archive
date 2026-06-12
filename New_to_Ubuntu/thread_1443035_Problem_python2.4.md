---
title: "Problem python2.4"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by Al B on 2010-03-30
When I try to update using synaptic I get the following error messages

E: python2.4-minimal: subprocess installed post-installation script returned error exit status 2

E: python2.4: dependency problems - leaving unconfigured

I have tried reinstalling python but have had no success in removing the error messages.  Can anyone suggest a possible solution to this problem.

---

### Post by blazemore on 2010-03-30
What happens if you run the command
```
sudo apt-get upgrade
```
in a terminal?

---

### Post by Al B on 2010-03-30
> **blazemore said:**
> What happens if you run the command
```
sudo apt-get upgrade
```
in a terminal?

The following is produced

Setting up python2.4-minimal (2.4.6-1ubuntu3.2.9.10.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python2.4-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.6-1ubuntu3.2.9.10.1); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Errors were encountered while processing:
 python2.4-minimal
 python2.4
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by blazemore on 2010-03-30
OK try
```
sudo dpkg --configure python2.4-minimal
```

---

### Post by Al B on 2010-03-31
> **blazemore said:**
> OK try
```
sudo dpkg --configure python2.4-minimal
```

The following error message is produced

Setting up python2.4-minimal (2.4.6-1ubuntu3.2.9.10.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python2.4-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.4-minimal

---

### Post by blazemore on 2010-03-31
> **Al B said:**
> The following error message is produced

Setting up python2.4-minimal (2.4.6-1ubuntu3.2.9.10.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python2.4-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.4-minimal

Right try manually purging the package cache and trying again.
This command is potentially dangerous if you type it wrong; best to copy and paste
```
sudo rm -fv /var/cache/apt/archives/*.deb
sudo apt-get update
sudo apt-get upgrade
```

Then whatever you were trying to do originally, and it should work. Problem was a dodgy .deb download, (probably).

---

### Post by Al B on 2010-03-31
> **blazemore said:**
> Right try manually purging the package cache and trying again.
This command is potentially dangerous if you type it wrong; best to copy and paste
```
sudo rm -fv /var/cache/apt/archives/*.deb
sudo apt-get update
sudo apt-get upgrade
```

Then whatever you were trying to do originally, and it should work. Problem was a dodgy .deb download, (probably).

Carried out the above but still get

Setting up python2.4-minimal (2.4.6-1ubuntu3.2.9.10.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python2.4-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.6-1ubuntu3.2.9.10.1); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Errors were encountered while processing:
 python2.4-minimal
 python2.4
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by blazemore on 2010-03-31
> **Al B said:**
> Carried out the above but still get

Setting up python2.4-minimal (2.4.6-1ubuntu3.2.9.10.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python2.4-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.6-1ubuntu3.2.9.10.1); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Errors were encountered while processing:
 python2.4-minimal
 python2.4
E: Sub-process /usr/bin/dpkg returned an error code (1)

Ugh. Try ```
sudo rm -fv /var/cache/apt/archives/partial/*.deb
```
Does that delete anything?

---

### Post by Al B on 2010-03-31
> **blazemore said:**
> Ugh. Try ```
sudo rm -fv /var/cache/apt/archives/partial/*.deb
```
Does that delete anything?

Not a thing

---

