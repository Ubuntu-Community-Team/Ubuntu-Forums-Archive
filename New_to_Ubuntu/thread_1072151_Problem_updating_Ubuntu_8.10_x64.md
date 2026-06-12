---
title: "Problem updating Ubuntu 8.10 x64"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by rausuar on 2009-02-17
I have downloaded and installed the Ubuntu 8.10 x64, and doing an update which includes the new kernel, as well as some other packages I get an error of "Forbidden" or that certain packages can not be downloaded (notice that I am downloading what appears in the official repositories).

I would like to know if that is a problem with my machine or a network problem, as well as how can I solve it (meaning if it is my problem, how can I delete those packages and make Ubuntu recheck in the servers if the packages still exist.

Thanks...

---

### Post by drs305 on 2009-02-17
Normally a "403 Forbidden" error is not a problem with your machine - it is a problem with connecting to a server. 

You can try changing servers in synaptic - Settings, Repositories, Ubuntu Software tab. Change "Download From" to another server and see if you still have problems. 

If you post your error message and the contents of your sources.list we can probably find the cause of the error. To post the sources.list contents:
```
cat /etc/apt/sources.list
```

---

### Post by rausuar on 2009-02-17
> **drs305 said:**
> Normally a "403 Forbidden" error is not a problem with your machine - it is a problem with connecting to a server. 

You can try changing servers in synaptic - Settings, Repositories, Ubuntu Software tab. Change "Download From" to another server and see if you still have problems. 

If you post your error message and the contents of your sources.list we can probably find the cause of the error. To post the sources.list contents:
```
cat /etc/apt/sources.list
```

Thanks man,

I was thinking so, due that I manually surfed to the address that was showing the error (an address directing to a package).

My surprise was that it was a clean install of Ubuntu 64x and the packages with the problem were gnome-games-data, the kernel source 2.6.27.11, among others, which is very annoying because the update notification keeps appearing and cant be downloaded.

I tried several servers already, the main one, the Spanish servers, one in the US, and another in Australia... it keeps showing the issue... I think those packages dont exist in the servers (but in the main one??)

Thanks...

---

### Post by drs305 on 2009-02-17
If you will run this and post the errors you get, and also sources.list, we can see the exact nature of the problem.
```
sudo apt-get update && sudo apt-get upgrade
```

Unless you compile your own packages, you don't need the (kernel) source so you can uncheck the "source code" box in synaptic > settings > repositories: ubuntu software tab. 

As a temporary solution, you could either "lock" the current version of gnome-games-data or uninstall it if you don't use that package. You lock a version by highlighting it in synaptic and then Package: Lock version.

Since you said there are others this isn't a complete solution nor an efficient one. If you post the information requested we might sort it out for you.

---

### Post by rausuar on 2009-02-17
> **drs305 said:**
> If you will run this and post the errors you get, and also sources.list, we can see the exact nature of the problem.
```
sudo apt-get update && sudo apt-get upgrade
```

Unless you compile your own packages, you don't need the (kernel) source so you can uncheck the "source code" box in synaptic > settings > repositories: ubuntu software tab. 

As a temporary solution, you could either "lock" the current version of gnome-games-data or uninstall it if you don't use that package. You lock a version by highlighting it in synaptic and then Package: Lock version.

Since you said there are others this isn't a complete solution nor an efficient one. If you post the information requested we might sort it out for you.

Err [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16
  403 Forbidden
Err [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) intrepid-updates/main openoffice.org-core 1:2.4.1-11ubuntu2.1
  403 Forbidden
Err [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) intrepid-updates/main evolution-common 2.24.3-0ubuntu1
  403 Forbidden
Err [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) intrepid-updates/main gnome-games-data 1:2.24.1.1-0ubuntu1
  403 Forbidden
Imposible obtener [http://co.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb](http://co.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb)  403 Forbidden
Imposible obtener [http://co.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.4.1-11ubuntu2.1_amd64.deb](http://co.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.4.1-11ubuntu2.1_amd64.deb)  403 Forbidden
Imposible obtener [http://co.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.24.3-0ubuntu1_all.deb](http://co.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.24.3-0ubuntu1_all.deb)  403 Forbidden
Imposible obtener [http://co.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.24.1.1-0ubuntu1_all.deb](http://co.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.24.1.1-0ubuntu1_all.deb)  403 Forbidden
E: No se pudieron obtener algunos archivos, ¿quizás deba ejecutar
apt-get update o deba intentarlo de nuevo con --fix-missing?

---

### Post by rausuar on 2009-02-17
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by rausuar on 2009-02-17
There are many packages missing in the x64 ... I just also tried to install the NVIDIA kernel 180, 64x package from the Ubuntu Repo and it didnt work either...

---

### Post by drs305 on 2009-02-17
Your sources.list works for me without any problems. I can also download the deb files when I click on the links you provided, so the server is also working. Example: [http://co.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.24.3-0ubuntu1_all.deb]("http://co.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.24.3-0ubuntu1_all.deb")

You can check your System, Preferences, Network Proxy and see if "Direct internet connection" is selected.

My Spanish is not so good but I believe the error message is telling you that you can run apt-get with the "--fix-missing" option. It will skip problem downloads and avoid error messages, although it doesn't really *fix* the problem. So you could run upgrade with:
```
sudo apt-get upgrade --fix-missing
```

---

### Post by rausuar on 2009-02-17
> **drs305 said:**
> Your sources.list works for me without any problems. I can also download the deb files when I click on the links you provided, so the server is also working. Example: [http://co.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.24.3-0ubuntu1_all.deb]("http://co.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.24.3-0ubuntu1_all.deb")

You can check your System, Preferences, Network Proxy and see if "Direct internet connection" is selected.

My Spanish is not so good but I believe the error message is telling you that you can run apt-get with the "--fix-missing" option. It will skip problem downloads and avoid error messages, although it doesn't really *fix* the problem. So you could run upgrade with:
```
sudo apt-get upgrade --fix-missing
```

Ohh yes, I got it... I am using a proxy and it doesnt allow me to download those due to a restriction (I also tried with the fix missing suffix, but it didnt work either)... Thanks... I will try to do it from somewhere else!! ;-P

Thanks!

---

