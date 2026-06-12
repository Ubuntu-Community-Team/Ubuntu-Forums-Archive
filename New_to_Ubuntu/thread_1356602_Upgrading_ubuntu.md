---
title: "Upgrading ubuntu"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Aloush on 2009-12-16
hey guys
I put 64bit as prefix i didnt mean to
so i messed up my windows parition so i am going to use ubuntu for a while and to recover some files
the only CD i could find was 8.4
is there a way to upgrade to 9.10 from 8.04 without needing the 9.10 CD

thanks

---

### Post by snowpine on 2009-12-16
The following command will (at this particular instant in time during Lucid testing) upgrade from 8.04 directly to 9.10:

```
sudo do-release-upgrade -d
```

However, I **STRONGLY** recommend a fresh install of 9.10 (rather than upgrading from a previous version). If you can't afford a blank CD, Canonical will [ship you one for free]("https://shipit.ubuntu.com/")!

---

### Post by philinux on 2009-12-16
> **Aloush said:**
> hey guys
I put 64bit as prefix i didnt mean to
so i messed up my windows parition so i am going to use ubuntu for a while and to recover some files
the only CD i could find was 8.4
is there a way to upgrade to 9.10 from 8.04 without needing the 9.10 CD

thanks

Unfortunately you would need to upgrade to 8.10 then to 9.04 then to 9.10.

If 10.04 was out you could upgrade directly as it will be the next LTS.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by Aloush on 2009-12-16
It not i cant afford a blank CD i just want it doing now quickly

---

### Post by philinux on 2009-12-16
> **Aloush said:**
> It not i cant afford a blank CD i just want it doing now quickly

```
update-manager -d
```

Will upgrade to 9.04 if you are running 8.10 Intrepid Ibex, then you would have to repeat that.

It will take ages and a lot a bandwidth doing it twice.

Easier to get 9.10 iso burnt and clean install.

I have /home on it's own partition so re-install is dead easy.

---

### Post by Merk42 on 2009-12-16
> **Aloush said:**
> It not i cant afford a blank CD i just want it doing now quickly

Downloading the 9.10 iso, especially via torrent, will be MUCH faster than downloading the updates to 8.10, and then 9.04, and then 9.10.

---

### Post by ST3ALTHPSYCH0 on 2009-12-16
I just d/led the 9.10 .iso from torrent in about 10 minutes, so it is pretty quick. Make sure to get the torrent from ubuntu's site, and not somewhere like isohunt like I did the first time... noone's seeding the torrent that on isohunt anymore :(

---

### Post by Georgia boy on 2009-12-16
> **snowpine said:**
> The following command will (at this particular instant in time during Lucid testing) upgrade from 8.04 directly to 9.10:

```
sudo do-release-upgrade -d
```

However, I **STRONGLY** recommend a fresh install of 9.10 (rather than upgrading from a previous version). If you can't afford a blank CD, Canonical will [ship you one for free]("https://shipit.ubuntu.com/")!

I seem to remember reading somewhere that they were going to start limiting the free shipment of CD's. Something about the cost of the CD's? Think that it was being limited to Members, the loco teams etc. Can't remember what site I was on when I read that now. Maybe someone else remembers that.

Tom

---

