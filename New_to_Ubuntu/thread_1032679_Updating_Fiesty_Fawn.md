---
title: "Updating Fiesty Fawn"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by buckrah on 2009-01-06
Can anyone tell me how to update fiesty fawn with out loosing files or reinstalling everything?  Thanks for any help.

---

### Post by donkyhotay on 2009-01-06
Feisty fawn is pretty old and I don't think it's supported anymore. You'd be better off upgrading to either hardy or intrepid (probably hardy since it's LTS).
try
```
gksu "update-manager -d"
```

---

### Post by JoshuaRL on 2009-01-06
> **donkyhotay said:**
> Feisty fawn is pretty old and I don't think it's supported anymore. You'd be better off upgrading to either hardy or intrepid (probably hardy since it's LTS).
try
```
gksu "update-manager -c"
```

I think you mean:
```

gksu update-manager -d

```

---

### Post by donkyhotay on 2009-01-06
> **JoshuaRL said:**
> I think you mean:
```

gksu update-manager -d

```

Thanks for correcting me. (c:

---

### Post by avtolle on 2009-01-06
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) is a link to upgrade from Feisty to Gutsy; if you want to upgrade further, the process will need to be repeated to go to Hardy (8.04 LTS). There have been a few threads, at least, on the forum indicating problems with pursuing this path.

---

### Post by buckrah on 2009-01-06
After plugging that command into a terminal I got this:Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by buckrah on 2009-01-06
After plugging that command into a terminal I got this:Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by ugm6hr on 2009-01-06
You will need to upgrade sequentially: Feisty to Gutsy to Hardy etc.

You may also need to use Gutsy AlternateCD for the Feisty to Gutsy upgrade, since the Feisty repo is no longer available.

---

### Post by buckrah on 2009-01-06
After plugging that command into a terminal I got this:Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by LowSky on 2009-01-06
> **ugm6hr said:**
> You will need to upgrade sequentially: Feisty to Gutsy to Hardy etc.

You may also need to use Gutsy AlternateCD for the Feisty to Gutsy upgrade, since the Feisty repo is no longer available.

The Fiesty repos have been cut off since October. If you need to upgrade you are going to have to get a gutsy Alt install CD or back up your files and upgrade to 8.04 or 8.10

---

### Post by zvacet on 2009-01-06
@ **buckrah**

> The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

You probably added 

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse 

to your source list but did you put # sign in front of 

deb [http://archives.ubuntu.com/ubuntu/](http://archives.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://archives.ubuntu.com/ubuntu/](http://archives.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://archives.ubuntu.com/ubuntu/](http://archives.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse 

If you didn´t do it.

```
sudo apt-get update && sudo apt-get upgrade
```

After that do to update manager and upgrade to Gutsy.

---

### Post by JoshuaRL on 2009-01-06
Let me also ask this:  Is there any reason you absolutely NEED to upgrade from Feisty to Intrepid?  That's quite a while in Linux, and may be a lot easier to just back up your info and do a fresh install.  It will be cleaner, faster, and overall a better chance of a good install.  I understand if you have some reason you can't or shouldn't do that, but I just wanted to check.

---

### Post by buckrah on 2009-01-11
If I upgrade to Gutsy will I lose my files?

---

