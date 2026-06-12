---
title: "Updating to Transmission 1.8"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by GL541 on 2010-02-10
Hi everyone,

I recently installed Ubuntu 9.10 and all is going well.

However, I want to install the latest version of Transmission because my present version (1.75) doesn't support magnets.

I don't know how to do this. Ubuntu Software Center only offers me version 1.75. Transmission's site has downloads of newer versions (latest 1.83) for lots of platforms but apparently not Ubuntu. In any case it's probably simpler/safer to install through the Software Center or the command line.

Is it possible to do so? Will it be possible sometime in the future?

Thanks :)

---

### Post by mcduck on 2010-02-10
It's not lielly to appear in official Ubutnu repositories.

In general all the program versiosn are frozen during the development, since that allows to test all those versiosn together to make sure they work as theya re supposed to. After release the only updates are for security reasons and to fix serious bugs.

The backports repository is an exception, some new apps might be backported from the next Ubutnu development version, but that pretty much depends on the developer's willingness to do the extra work.

Anyway, you can probably find some PPA repsoitory with up-to-date versions of Transmission, or alternatively just download the .deb packages from [getdeb.net]("http://www.getdeb.net/software/Transmission")...

---

### Post by nhasian on 2010-02-10
to get the latest version of Transmission, open a terminal from Applicaions->accessories then copy/paste the following commands:

```
sudo add-apt-repository ppa:transmissionbt/ppa
```

```
sudo apt-get update && sudo apt-get upgrade
```

viola! your done

NOTE: unlike installing a deb manually from GetDeb.net, when the PPA is updated with a newer version of transmission you will automatically be updated to the newer version next time the update-manager is run.

---

### Post by mcduck on 2010-02-10
> **nhasian said:**
> 
NOTE: unlike installing a deb manually from GetDeb.net, when the PPA is updated with a newer version of transmission you will automatically be updated to the newer version next time the update-manager is run.
That's true. Although GetDeb also has a repository, so if you want to you can get automatic updates for *all* the apps available through GetDeb.

But application-specific PPA repositories are probably more reliabe when it comes to getting the latest versions of programs quickly.

---

### Post by GL541 on 2010-02-10
> **nhasian said:**
> to get the latest version of Transmission, open a terminal from Applicaions->accessories then copy/paste the following commands:

```
sudo add-apt-repository ppa:transmissionbt/ppa
```

```
sudo apt-get update && sudo apt-get upgrade
```

viola! your done

NOTE: unlike installing a deb manually from GetDeb.net, when the PPA is updated with a newer version of transmission you will automatically be updated to the newer version next time the update-manager is run.

Wow! That was painless! I put in those two lines of code, restarted Transmission and I now have version 1.83, as required.

Thank you both for your replies :)

---

### Post by egalvan on 2010-02-10
> **nhasian said:**
> to get the latest version of Transmission, open a terminal from Applicaions->accessories then copy/paste the following commands:

```
sudo add-apt-repository ppa:transmissionbt/ppa
```

```
sudo apt-get update && sudo apt-get upgrade
```


NOTE: unlike installing a deb manually from GetDeb.net, **when the PPA is updated with a newer version of transmission you will automatically be updated to the newer version next time the update-manager is run.**

+1 for PPA, great job.

---

### Post by andrew.46 on 2010-02-12
There is also the option of compiling your own copy which I have done on Karmic Koala and written a brief guide:

Howto: Build the BitTorrent client Transmission under Karmic Koala
[http://ubuntuforums.org/showthread.php?t=1391718](http://ubuntuforums.org/showthread.php?t=1391718)

All the best,

Andrew

---

### Post by deviator on 2010-02-12
this might be abit off topic but does ubuntu update all programs i install. the reason i ask this is because i see alot of "canoical does not support updates for this program" in most of the programs i install. do i have to update all programs manually?

---

### Post by benmoran on 2010-02-12
If you installed them through Software Center, Synaptic,or through a PPA, then they will update automatically (when Update Manager is run). 

If you just download a single deb and install it manually, it won't update itself.

---

### Post by fmfrisch on 2010-02-12
Ubuntu will only update software for which you have PPA's. The ppa's can be found in most cases at [Launchpad.net]("http://launchpad.net") Now every time there is an update released in the ppa's your computer will install it. By standard you have the official ubuntu ppa installed from that necessary updates to the OS and sometimes also applications will be released. You can add a ppa under System>Administration>Software Sources

---

### Post by deviator on 2010-02-12
> **benmoran said:**
> If you installed them through Software Center, Synaptic,or through a PPA, then they will update automatically (when Update Manager is run). 

If you just download a single deb and install it manually, it won't update itself.

thanks for that.

anyway to check the programs installed or to run a manual update on the .debs i may have forgotten about? like to clean the system for example?

computer janitor seems buggy

---

