---
title: "Thunderbird 3.1?"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by D1Knight on 2010-07-07
Hello all.:) I just today 7-7-10 had an update to Thunderbird, from 3.0.4 to 3.0.5 What has happened to 3.1? According to the home page, Mozilla Thunderbird 3.1 has been available for Linux since June 24th, 2010

Is Mozilla Thunderbird 3.1 update for Ubuntu 10.04 around the corner? Thanks for any and all input. Cheers.:)

---

### Post by okplayer02 on 2010-07-08
either you can be patient and wait for them to package it or you can install yourself 

here is the ppa that has 3.1 
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)


here is the link to show you how to add a ppa 

[http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html](http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html)

then all you do is 

```
sudo aptitude update && sudo aptitude safe-upgrade
```

this will update all your repos then it will upgrade all the programs including thunderbird to 3.1

---

### Post by roberthr on 2010-07-12
Wrong. Mozilla PPA hold first alpha version of Thunderbird 3.1 which is close to useless so don't upgrade yet.

---

### Post by TechBeastie on 2010-07-12
As far as I can tell, the best approach to making sure that you always have the bleeding-edge version of any mozilla application is to go and set up an "unmanaged" instance of that application.  That is, go to the mozilla website, download the generic Linux tarball, extract it in your folder of choice, and then set up symlinks to the binary in that folder to make execution easier.  True, you'll have to be personally responsible for keeping the thing updated (since aptitude will have no idea that the application is present on your system), but that also means you should be able to get new updates LONG before they hit the official Ubuntu repos.

---

### Post by spcwingo on 2010-07-12
If you're running the 32 bit version of Ubuntu you could use Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")

---

### Post by D1Knight on 2010-07-25
> **roberthr said:**
> Wrong. Mozilla PPA hold first alpha version of Thunderbird 3.1 which is close to useless so don't upgrade yet.

Thanks for the warning. Yes, better to wait for a stable release.:)

---

### Post by D1Knight on 2010-07-25
> **TechBeastie said:**
> As far as I can tell, the best approach to making sure that you always have the bleeding-edge version of any mozilla application is to go and set up an "unmanaged" instance of that application.  That is, go to the mozilla website, download the generic Linux tarball, extract it in your folder of choice, and then set up symlinks to the binary in that folder to make execution easier.  True, you'll have to be personally responsible for keeping the thing updated (since aptitude will have no idea that the application is present on your system), but that also means you should be able to get new updates LONG before they hit the official Ubuntu repos.

That is a pretty good idea, to be "bleeding edge". Thanks for sharing.:)

---

### Post by D1Knight on 2010-07-25
> **spcwingo said:**
> If you're running the 32 bit version of Ubuntu you could use Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)
 
Wow! Interesting link. I thank you.:)

---

