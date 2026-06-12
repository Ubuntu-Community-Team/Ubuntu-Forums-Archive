---
title: "unable to remove brken package"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by Zavie A. on 2011-02-02
okay so, in an attempt to install a flash player plugin for firefox, in encountered a broken package,which gives me this message

> dpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

When I try to reinstall it it tells me that I can't because of a broken cache. 

Does anyone know of a way to get rid of this? :/

---

### Post by ben889 on 2011-02-02
I am new to but i believe that all you have to do is open synaptic click edit and select fix broken package

---

### Post by sikander3786 on 2011-02-02
> **Zavie A. said:**
> okay so, in an attempt to install a flash player plugin for firefox, in encountered a broken package,which gives me this message



When I try to reinstall it it tells me that I can't because of a broken cache. 

Does anyone know of a way to get rid of this? :/
From Applications > Accessories > Terminal, please post the outputs of these commands.

```
sudo apt-get clean
sudo apt-get autoclean
```

```
sudo apt-get install --reinstall flashplugin-nonfree
```

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

---

### Post by Zavie A. on 2011-02-03
Thanks for the quick reply!

> zavire@zavire-laptop:~$ sudo apt-get clean

> zavire@zavire-laptop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

> zavire@zavire-laptop:~$ sudo apt-get install --reinstall flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

> zavire@zavire-laptop:~$ sudo dpkg --configure -a 

> zavire@zavire-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 22.2kB of archives.
After this operation, 73.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse flashplugin-installer 10.1.102.65ubuntu0.10.04.1 [20.1kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse flashplugin-nonfree 10.1.102.65ubuntu0.10.04.1 [2,110B]
Fetched 22.2kB in 0s (31.7kB/s)            
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by sikander3786 on 2011-02-03
First try,

```
sudo apt-get remove --force flashplugin-nonfree
```

If that doesn't work, try this one.

```
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree

```

If that is successful, re-do the following one's.

```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Zavie A. on 2011-02-03
This is what I got.

> zavire@zavire-laptop:~$ sudo apt-get remove --force flashplugin-nonfreeE: Command line option --force is not understood

> zavire@zavire-laptop:~$ sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 174046 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree

It seems like they were both unsucessful. :/

---

### Post by sikander3786 on 2011-02-03
Sorry, I think I missed a step. Please try these.

```
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
```

```
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
```

---

### Post by Zavie A. on 2011-02-03
hey  it worked! Thanks Alot. :)

---

