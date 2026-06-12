---
title: "Software Versions and apt-get install"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by beegary on 2010-01-04
Just a quick one:
 
I have used apt-get install to add most of the software on my Ubuntu install.
I sometimes use the Software Centre.
 
 
What are the advantages/disadvantages of each?
 
If I add a PPA software source that includes a different version of software already in the approved repo's how do I ensure that I apt-get the one from a specific source?
 
 
Cheers

---

### Post by halitech on 2010-01-04
Synaptic, apt-get install, software center are all front ends to apt so they use the same sources.list file to determine where to get the files from so no difference in which way you install a package.

apt-get - faster but you need to either know the name of the package or search for it
Synaptic and Software center - slower but allows you to see a description of the program before installing.

---

### Post by Cheesemill on 2010-01-04
Software Centre is just a graphical front-end for the apt-get command, they have exactly the same effect.

When you've added PPA's, apt-get automatically uses whichever source has the latest version number.
You can look into apt-pinning if you want to make sure you're getting software from a particular source.
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by beegary on 2010-01-04
Thank you very much, I think I will leave the pinning for a while! Seems a bit complicated! 
I thought it would be just a case of appending the version number to the apt-get install command! Silly me.

---

### Post by Tayl on 2010-01-04
How do you do a search via apt-get if you don't know the specific name but do not wish to use the software center?

Tayl.

---

### Post by howefield on 2010-01-04
```

``````

```> **Tayl said:**
> How do you do a search via apt-get if you don't know the specific name but do not wish to use the software center?

Tayl.

Use the search command eg

```
apt-cache search searchword
```

You could also use grep to refine and narrow the returns a bit, eg

```
apt-cache search searchword | grep somethingelse
```

---

### Post by bodhi.zazen on 2010-01-04
> **Cheesemill said:**
> Software Centre is just a graphical front-end for the apt-get command, they have exactly the same effect.

When you've added PPA's, apt-get automatically uses whichever source has the latest version number.
You can look into apt-pinning if you want to make sure you're getting software from a particular source.
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Typically one does not use pinning with ppa. Typically a ppa offers either a package not yet in the repositories or a newer version. Nothi9ng wrong with pinning a ppa, it is not *that* hard to do, just mentioning it is not necessary to use a ppa.

Pinning is typically used when one mixes repositories, ie debian + ubuntu or ubuntu 9.04 and 9.10. Mixing repositories in not advised if you are not experienced with package management and can easily result in a broken system.

---

### Post by mcduck on 2010-01-04
> **howefield said:**
> ```

``````

```

Use the search command eg

```
apt-cache search searchword
```

You could also use grep to refine and narrow the returns a bit, eg

```
apt-cache search searchword | grep somethingelse
```

..and if you want to see more details about a package, "apt-cache show *packagename* does the trick. :)

---

### Post by Tayl on 2010-01-04
Ah excellent, thank you!

Tayl.

---

### Post by slakkie on 2010-01-04
> **bodhi.zazen said:**
> Typically one does not use pinning with ppa. Typically a ppa offers either a package not yet in the repositories or a newer version. Nothi9ng wrong with pinning a ppa, it is not *that* hard to do, just mentioning it is not necessary to use a ppa.

Pinning is typically used when one mixes repositories, ie debian + ubuntu or ubuntu 9.04 and 9.10. Mixing repositories in not advised if you are not experienced with package management and can easily result in a broken system.

I beg to differ, PPA's also have the tendency to have more packages then you want to have installed from a PPA, so pinning is IMO needed once you start using PPA's. Unless you want to upgrade all packages that you have installed and might be available on a PPA you have included in your sources.list then do it without pinning. 

I made a blog-post about pinning, it is not difficult or hard to do.
[http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)

---

