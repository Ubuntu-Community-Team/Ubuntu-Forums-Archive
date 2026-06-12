---
title: "anything wrong with the repos"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by koba101 on 2009-12-15
hI,

I've noticed the following message when i was trying to update




> Failed to fetch [http://ppa.launchpad.net/ubuntu-it-dev/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/ubuntu-it-dev/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/ubuntu-it-dev/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-it-dev/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by t0p on 2009-12-15
Your error message indicates that the problem is not with the usual repos, but rather with a PPA repo you set up for some reason.

If you look at your sources list file (/etc/apt/sources.list) and compare the url in the error message with the urls in the file, you will be able to see which repo is giving you the problem.

---

### Post by audiomick on 2009-12-15
Could well be that the server is having a problem. Try again tomorrow.

---

### Post by kansasnoob on 2009-12-15
Maybe try the main server.

---

### Post by sandyd on 2009-12-15
[http://ppa.launchpad.net/ubuntu-it-dev/ubuntu/dists](http://ppa.launchpad.net/ubuntu-it-dev/ubuntu/dists)

they seem to have dropped the karmic distro

---

### Post by k3lt01 on 2009-12-15
Carlee has hit the nail on the head, either that or there was never a Karmic repo in that ppa in the first place. Have you updated that exact repo before?

---

### Post by koba101 on 2009-12-15
yeah!

i'll try again tomorrow again tomorrow

---

### Post by koba101 on 2009-12-15
intereting...why is dapper still supported

---

### Post by sandyd on 2009-12-15
> **k3lt01 said:**
> Carlee has hit the nail on the head, either that or there was never a Karmic repo in that ppa in the first place. Have you updated that exact repo before?
type this in...
```

sudo gedit /etc/apt/sources.list

```

change "karmic" in the line
```

deb http://ppa.launchpad.net/ubuntu-it-dev/ubuntu 
```
to "jaunty"
then 
```

sudo apt-get update

```

---

### Post by k3lt01 on 2009-12-15
> **koba101 said:**
> intereting...why is dapper still supportedDapper is an LTS that's why. Even Ubuntu still has the Dapper Repos in its active archive.

---

### Post by koba101 on 2009-12-15
carlee....why would i use jaunty, if i got karmic?  it's been a while since karmic has been released so i'm thinking a seperate repos'll be there, i really doubt i put that by myself (maybe i got amnesia)

---

### Post by k3lt01 on 2009-12-15
> **koba101 said:**
> carlee....why would i use jaunty, if i got karmic?  it's been a while since karmic has been released so i'm thinking a seperate repos'll be there, i really doubt i put that by myself (maybe i got amnesia)
Worse things have happened, lol.

Carlee is showing you a way to still use the programs you want to get even though they don't currently have a Karmic repo. It's your choice, you can either do as she has suggested or wait until they release a Karmic repo. The fact remains we don't even know if you have ever obtained anything from the missing (if it was ever there anyway) repo.

---

### Post by koba101 on 2009-12-16
ok this is getting wierd


i'm seeing the 

> deb [http://ppa.launchpad.net/ubuntu-it-dev/ubuntu](http://ppa.launchpad.net/ubuntu-it-dev/ubuntu)

only on the GUI, in the sources.list file itself it's not there, how come?

---

### Post by philinux on 2009-12-16
```
cat /etc/apt/sources.list.d
```

Is where they are.

---

### Post by koba101 on 2009-12-16
right..because it's part of "other software"
thanks

i'm not sure if i should mark this thread as solved or not

---

