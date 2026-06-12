---
title: "How to update from downloaded packages"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by dileepdinesh on 2008-12-14
Hi,
   I am a beginner with linux,,,,installed 8.04 on to my desktop 
and updated everything. My net connection is slow that it took me 2 days to update completely. Now i have installed 8.04 on to my laptop and want to update it,,,some snooping around the forums tells me all packages will be downloaded to /var/cache/apt....now if i copy to this my laptop's same directory,,the update procedure would be done,,,i have copied the entire thing....
and tried this commands apt-get update and also tried apt-get upgrade...but they are trying to download the packages from internet rather than installing from the directory...how do i overcome this?

---

### Post by iponeverything on 2008-12-14
either do a:

```
sudo apt-get update
```

to update your source list or copy over the contents of:

```
/var/lib/apt/lists
```

---

