---
title: "How do I upgrade Scribus?"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by UncleAlan on 2010-12-24
I am running 10.10 and require a Scribus version that works. The Software Centre version is 1.3.3.13svn but this DOES NOT work on my 10.10 or 10.04.1. Scribus say this is because version 1.3.3.13 uses something called QT3 which is broken in Ubuntu and so I need to use Scribus 1.3.8/1.3.9svn which uses QT4.

As a beginner this doesnt mean much to me, how ever I did obtain version 1.3.9.tar.bz2 and have the Ubuntu Community instructions on how to make this work but its all a bit confusing. Although I can work with sudo codes etc I am getting confused with the rest of the instructions.

I cant be alone with this Scribus problem so it would be helpful to have a later version that works, available in the download centre. Meanwhile any assistance / advice will be gratefully received.

Thanks

Uncle Alan

---

### Post by Dark_Stang on 2010-12-24
Install Scribus-NG, it's 1.3.8.

---

### Post by charlie_b on 2010-12-24
Another possibility is to install Wine, if you haven't already got it. The Windows version of the latest Scribus is likely to be available, so you can download it and run it in Wine.
As an open source purist, I don't like having to resort to this sort of thing, but I had a project recently which needed to be done in the latest Scribus and so this is what I did.

---

### Post by crichard on 2010-12-25
Add the following repository in your Software Sources,

```
deb http://debian.scribus.net/debian/ maverick main
```

Then, authenticate the key by using the following command,
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEF818CF
```

Then update your software sources,

```
sudo apt-get update
```

Install scribus-ng,
```
sudo apt-get install scribus-ng
```

---

### Post by UncleAlan on 2011-01-01
THANK YOU for the three replies above. I now have Scribus 1.3.8 up and working on the 10.10 pc. I didnt actually know about wine before and can see a possible use for this if push come to shove with an application I use.

 I learnt several things there so a Result.  Thanks  Alan

---

