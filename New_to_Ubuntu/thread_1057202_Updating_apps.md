---
title: "Updating apps"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by MikeBasilico on 2009-02-01
How do you get ubuntu to update individual apps without waiting for the next release, its rather annoying doing it manually

---

### Post by perlluver on 2009-02-01
> **MikeBasilico said:**
> How do you get ubuntu to update individual apps without waiting for the next release, its rather annoying doing it manually

You can enable pre-released software under System>Administration>Software sources, also Back-Ports.  They might cause problems on some programs, so un-check those you don't want to update, and make sure to un-check both of them, after you have installed the program you want.

---

### Post by MikeBasilico on 2009-02-01
That helped, but it still didnt update kdenlive, i have .6 still instead of .7.1, this is actually the most important part

---

### Post by MikeBasilico on 2009-02-01
bump

---

### Post by perlluver on 2009-02-01
> **MikeBasilico said:**
> That helped, but it still didnt update kdenlive, i have .6 still instead of .7.1, this is actually the most important part

You might have to download that and install from the maintainers website.  Otherwise follow the directions at [http://www.kubuntu.com](http://www.kubuntu.com) to install KDE 4.2, and see if it is available in the PPA repository.  If it is not in the ppa, then you will have to install it from the maintainers website.

---

### Post by perlluver on 2009-02-01
Or you can follow the directions listed here: [http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages) for Ubuntu Intrepid.

---

### Post by jimmy the saint on 2009-02-01
You have to understand that the updater app isn't looking to the application's developers for updates.  The devs can update their app many times and it wouldn't matter becasue the update app is looking to Ubuntu's repositories.  That means that someone (a package maintainer) has to get the app and package it for Ubuntu and submit it to the repos in order for your package to update.  Also, many updates are only applied to the most current, or even upcoming Ubuntu version and may not ever be backported to previous ones unless they are deemed important.

Edit: sometimes software developers maintain their own repositories with updated packages for ubuntu that you can add to synaptic.

---

### Post by MikeBasilico on 2009-02-02
so there is normally no simple way? or has a third party made anything that automatically does it

---

### Post by mkvnmtr on 2009-02-02
It would seem to me that the easiest way to update an app to a newer would be to uninstall it and reinstall the newer version.

---

### Post by perlluver on 2009-02-02
> **MikeBasilico said:**
> so there is normally no simple way? or has a third party made anything that automatically does it

The link I posted above, about Ubuntu Intrepid has instructions to add a third party repository to synaptic, to get the updated package.  [http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages).

---

### Post by Rolcol on 2009-02-02
The Ubuntu repositories are maintained by humans.  There are simply too many packages to update immediately when a new version becomes available.  If you want the newest version of an application, your best solution would be to update it manually by compiling the source code or installing the .deb package if they offer one.

---

