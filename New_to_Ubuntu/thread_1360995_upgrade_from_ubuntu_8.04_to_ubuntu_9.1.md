---
title: "upgrade from ubuntu 8.04 to ubuntu 9.1"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by johndingli on 2009-12-21
Hi guys need help on how to update from ubuntu 8.04 to ubuntu 9.1. I have an asus netbook so the version must be for netbooks thanks for any help

---

### Post by Extract_Here on 2009-12-21
[www.ubuntu.com](www.ubuntu.com) has a netbook version of Karmic 9.10

---

### Post by johndingli on 2009-12-21
can I upgrde by doing sudo apt-get

---

### Post by cartisdm on 2009-12-21
> can I upgrde by doing sudo apt-get

Personally, I never use the Update Manager thing - always runs too much of a risk for running into problems.  Just go to [Ubuntu.com]("http://www.ubuntu.com/getubuntu/download-netbook") and download the Ubuntu NBR ISO

However I have found the regular versions of ubuntu and linux mint to run just fine on even low level Netbooks

---

### Post by slughappy1 on 2009-12-21
Upgrading is just fine, not sure about NBR though. Just make sure to delete the old files after. I use Ubuntu-Tweak for that. Makes it much easier to see all the old config files, cached debs, and old kernels. Then deleting them is as simple as point and click.

---

### Post by bodhi.zazen on 2009-12-21
You have to update sequentially so

8.04 -> 8.10 -> 9.04 -> 9.10 

That is a ton of bandwidth, so it may be best simply to install 9.10.

The preferred method of upgrading is via update manager and t should not matter that you are using the netbook edition.

---

### Post by slughappy1 on 2009-12-21
I had no idea you had to update sequentially, lame. But it makes sense I guess.

---

### Post by bodhi.zazen on 2009-12-21
> **slughappy1 said:**
> I had no idea you had to update sequentially, lame. But it makes sense I guess.

You can upgrade from LTS to LTS, so you could go direct from 8.04 -> 10.04 once it becomes available.

---

### Post by slakkie on 2009-12-21
It is possible to upgrade from 8.04 to 9.10 directly. You need to run some KDE specific app to do so. See [https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04](https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04)

Also you can download the alternate CD images and upgrade from those. See [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

I have never tested either upgrade on a netbook remix, so your millage may vary.

If you would perform the sequential upgrade I would advise the alternate CD route. Quicker and less bandwidth.

---

