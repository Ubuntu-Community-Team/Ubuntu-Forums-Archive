---
title: "Software center won't install software?"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2011-09-03
When going through the software center to install new software (KMYmoney..etc) I am getting a heap of errors.

```

Failed to download package files - check your internet connection

```then

```

Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.

```I have no idea what to do, my internet works fine am using it now.

Any ideas?

---

### Post by Sef on 2011-09-03
Change to another location. Synaptic > Settings > Repositories and it is on the first page.

---

### Post by scruffyeagle on 2011-09-03
> **terrykiwi83 said:**
> When going through the software center to install new software (KMYmoney..etc) I am getting a heap of errors.

```

Failed to download package files - check your internet connection

```then

```

Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.

```I have no idea what to do, my internet works fine am using it now.

Any ideas?

I ran into something very similar (identical?) to this, and eventually realized it was because the FF flash program software was from Adobe. Since Adobe isn't listed as a trusted source in the repositories, it generates the error messages. I suspect something similar is happening to you. Getting past it simply required me telling it to ignore the errors and proceed downloading from an untrusted source. Consider the source(s) of the KYMmoney (etc.) software. Are those sources within the structure of the repository? If not, there's your problem.

---

### Post by terrykiwi83 on 2011-09-03
Thanks for the replies it looks as if the errors are caused by :

```

Setting up otrs2 (2.4.9+dfsg1-3+squeeze1build0.11.04.1) .

```

OTRS2 always fails to install and I can't stop it trying to install. How would one get rid of this or get it to actually Install :)

Cheers

---

### Post by avinash-1 on 2011-09-04
> **terrykiwi83 said:**
> When going through the software center to install new software (KMYmoney..etc) I am getting a heap of errors.

```

Failed to download package files - check your internet connection

```then

```

Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.

```I have no idea what to do, my internet works fine am using it now.

Any ideas?

install upgrades for ur synaptic software centre..or update ur synaptic package :)
i also suffered from same problem now it's wrking flowless.

---

### Post by avinash-1 on 2011-09-04
install upgrades for ur synaptic software centre..or update ur synaptic package :)
i also suffered from same problem now it's wrking flowless.

---

### Post by Dry Lips on 2011-10-02
Try running these commands from the Terminal:```
sudo -i 
apt-get update 
apt-get upgrade 
apt-get clean 
apt-get autoclean 
exit         
```

---

### Post by vipul3325 on 2012-06-21
> **Dry Lips said:**
> Try running these commands from the Terminal:```
sudo -i 
apt-get update 
apt-get upgrade 
apt-get clean 
apt-get autoclean 
exit         
```

very very thanks dry lips...... this cure the problem..... thanks
:-)

---

### Post by Eudaimon on 2012-08-28
Dry lips -- Worked for me as well!  Thank you!

---

### Post by amandat on 2012-09-03
Hi, 

I am having the same issue. I tried to install GIMP, it sent up the second message. I treid another 3 times, all with the same effect. Then tried the linus version of Paint. Same thing. 
I then thought it might be something to do with the kind of software, so tried to install a small game. Same thing as before. 

In the Details section, it says:
gimp gimp-data gimp-help-common gimp-help-de gimp-help-en libbabl-0.0-0 libgegl-0.0-0 libgimp2.0

The system is updated. 

What can be done with this?


Edit: I have just done as dry lips said, and it still won't work.

---

### Post by terrykiwi83 on 2012-09-04
The Dry Lips solution worked for me. I will see if I can recall any other methods to fix it

---

### Post by mansonfan78 on 2012-09-04
> **terrykiwi83 said:**
> Thanks for the replies it looks as if the errors are caused by :

```

Setting up otrs2 (2.4.9+dfsg1-3+squeeze1build0.11.04.1) .

```OTRS2 always fails to install and I can't stop it trying to install. How would one get rid of this or get it to actually Install :)

Cheers


Is it already installed and trying to upgrade to a newer version?  If so, find it in synaptic, go to "package" and "lock version".  That will keep it from trying to install again.  Or you could try uninstalling and reinstalling it.

p.s. - if you version-lock anything, you have to unlock it before you can upgrade the operating system.

---

