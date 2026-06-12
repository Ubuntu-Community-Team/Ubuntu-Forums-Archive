---
title: "upgrade pidgin failed under Hardy(ppc)"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Leechow on 2009-11-07
my system:
  Ubuntu 8.04 Hardy for PowerPC (Apple iBook G4)

problem:
  I'm try to upgrade pidgin by using the code below which is from pidgin webside:
  ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
 echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

```

After doing this, i open Update Manager, check for updates, and then install the newly available Pidgin packages.

then, i restart my computer, and pidgin is gone from the "applications". So, i tried:
```
sudo apt-get install pidgin
```

the system returns me with this:
```
leechow@G4:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: libpurple0 (>= 1:2.4.1-1ubuntu2.6) but it is not going to be installed
          Depends: pidgin-data (< 1:2.4.1-z) but 1:2.6.3-1ubuntu1~pidgin1.8.04.1 is to be installed
E: Broken packages

```

anyone can help???

---

### Post by yeats on 2009-11-07
Try this:

```
sudo apt-get update
sudo apt-get -f install

```

---

