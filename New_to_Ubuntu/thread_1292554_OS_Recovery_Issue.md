---
title: "OS Recovery Issue"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by MiTavis on 2009-10-16
I installed Ubuntu 8.10 on an external USB SATA drive. Then I performed all updates and then the update to 9.04. I checked available software and downloaded and installed most of the software packages with a high rating. (I did download a few images and choose to use the 8.04 background image. When I shut down and then later rebooted, all I got was a thick green line at the top of the screen. I then tried various recovery options with no luck until I tried using version 8.04 which was an option for booting.
 
On a netbook machine, I got the Kubuntu logo while loading but then the image froze.
 
I recall loading some software that was KDE specific. I believe I have a conflict between a Ubuntu load and a Kubuntu load.
 
Is there a way for unloading the KDE packages from the hard drive from within the 8.04 environment? I understand that by hitting the escape key while loading I can go to a command line environment but I do not know the Linex command syntex.
 
Thanks for any help.

---

### Post by bumanie on 2009-10-16
Form command line you can purge any of the packages you think may be causing a problem. However, you need to know the exact package name. To get rid of the package and configuration files use this command > sudo apt-get --purge remove <packagename>Inserting the package name and leaving out the < > symbols.

---

### Post by MiTavis on 2009-10-16
Is there a way to list the packages installed?
 
Thanks

---

### Post by hal10000 on 2009-10-16
> s there a way to list the packages installed
```
dpkg -l

``` 
or for example 
```
dpkg -l |grep kde
```
to find packages containing "kde" in their package name

---

### Post by MiTavis on 2009-10-17
Actually I tried aptitude. It gave the list of installed packages and I was able to remove packages. However, this did not work and I finally re-installed Ubantu 8.10 and then upgraded to 9.04. I noticed however, that when booting I am no longer given the choice of booting into 8.04. I am not sure how I got that choice the first time. Perhaps it was because I had installed KDE educational products as well as other available software. I don't think there is much more that can be discussed about this issue unless someone has some insights.

---

