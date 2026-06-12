---
title: "Want to use ISO image of APTonCD as local repositary"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by rraj.be on 2008-12-27
My internet connection is very slow and hence i am using APTonCD for package backup and i am using this one as my local repositary . .

There are two big _[COLOR="Red"]problems [/COLOR]_involved in this for me.

1) Packages are updated frequently and i have to use new DVD's frequently.

2) I have to insert APTonCD DVD every time i need to install any package from it. .

[U][COLOR="Red"]
MY REQUIREMENT:[/COLOR][/U]

I have a APTonCD image in my home folder.

I have to mount it automatically every time ubuntu boots 

and add it as local repository.


Could any one help me in this. . .

---

### Post by zvacet on 2008-12-28
I find old post but I hope it will work.Look [here.]("http://ubuntuforums.org/showthread.php?t=35807&highlight=add+iso+fstab")

---

### Post by mapes12 on 2008-12-28
If reinstalling the aptoncd packages from a CD or DVD simply change the Synaptic "Origin" button to that media selection. If reinstalling the aptoncd packages from the iso file they will be installed back in your "var" directory when you run the "Restore" option in Aptoncd. So, you will need to run this to install them:
```
sudo -i /var/cache/apt/archives/*.deb
```
This works in 8.04 but I can't guarantee the same result with any other version.

---

### Post by cypherbios on 2009-01-04
> **rraj.be said:**
> My internet connection is very slow and hence i am using APTonCD for package backup and i am using this one as my local repositary . .

There are two big _[COLOR="Red"]problems [/COLOR]_involved in this for me.

1) Packages are updated frequently and i have to use new DVD's frequently.

2) I have to insert APTonCD DVD every time i need to install any package from it. .

[U][COLOR="Red"]
MY REQUIREMENT:[/COLOR][/U]

I have a APTonCD image in my home folder.

I have to mount it automatically every time ubuntu boots 

and add it as local repository.


Could any one help me in this. . .

It is quite simple. You can use the option "Restore" from the aptoncd's main window. Then you select your .iso image then the application will copy all the packages in the CD to your cache, so when APT tries to install any of those packages it will look for it in the cache first, thus it will not ask for the CD.

Hope that helps.

---

