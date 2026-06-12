---
title: "installing edubuntu with an existing Ubuntu install?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by cptrohn on 2009-03-06
would it go something like this?
```
sudo apt-get install-edubuntu-desktop
```

Like installing the KDE desktop with Ubuntu?  Or would it be better to just burn the ISO CD and install strictly with edubuntu?

I am purchasing 2 laptops for my niece and nephew for school and would like to install Edubuntu on them since it is designed for school-age kids.

---

### Post by perpetualcacophany on 2009-03-06
It should work fine to install Edubuntu from within Ubuntu exactly the same way you would if you wanted to try Kubuntu or Xubuntu.

```
sudo apt-get install edubuntu-desktop
```

That would do it.

If you don't want the splash screen for it and all that you could just install the extra programs though.

```
sudo apt-get install edubuntu-addon-science edubuntu-addon-young edubuntu-artwork
```

That would just install the extra programs into Ubuntu without the splash screen. "edubuntu-artwork" just adds the themes, so if you don't need that you can ignore that part of it.

So I guess that's two options to consider. It will also work just fine to use the Edubuntu ISO to do it, but if you already have a standard Ubuntu cd downloaded it might be easier to add it all after the fact.

---

### Post by cptrohn on 2009-03-06
> **perpetualcacophany said:**
> It should work fine to install Edubuntu from within Ubuntu exactly the same way you would if you wanted to try Kubuntu or Xubuntu.

```
sudo apt-get install edubuntu-desktop
```

That would do it.

If you don't want the splash screen for it and all that you could just install the extra programs though.

```
sudo apt-get install edubuntu-addon-science edubuntu-addon-young edubuntu-artwork
```

That would just install the extra programs into Ubuntu without the splash screen. "edubuntu-artwork" just adds the themes, so if you don't need that you can ignore that part of it.

So I guess that's two options to consider. It will also work just fine to use the Edubuntu ISO to do it, but if you already have a standard Ubuntu cd downloaded it might be easier to add it all after the fact.

Yes I do already have an Ubuntu CD downloaded and was thinking it might be easier (and save some time) to just install with an existing ubuntu CD... Thanks much!

---

