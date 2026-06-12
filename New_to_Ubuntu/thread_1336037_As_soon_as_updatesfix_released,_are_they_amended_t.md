---
title: "As soon as updates/fix released, are they amended to the online .iso?"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by emigrant on 2009-11-24
hi all ;)

can any one tell me, whether the new fixes and updates are integrated to the downloadable isos in the ubuntu page?

i mean an iso i downloaded on the first day of karmic release and an iso i download today, are both same?

thank you for your time :popcorn:

---

### Post by ninjapirate89 on 2009-11-24
I was wondering this myself the other day.

---

### Post by XCan on 2009-11-24
I don't believe so. Updates will only be added once every year or so to the LTS .isos.

---

### Post by Madel on 2009-11-24
Nope. Only in updates. Not in ISO.
Except for LTS versions as they usually ship like 6.06.1.
Not with 18month release cycle.

---

### Post by emigrant on 2009-11-24
then a 2008 hardy iso and a 2009 hardy iso are both different?
won't it surpass the 700mb cd size?
also how often they update the .iso?

---

### Post by bilalakhtar on 2009-11-24
No, updates aren't added to disk images, atleast not in the case of normal releases.
In LTS releases like 8.04 hardy, canonical adds updates to the ISO once in a few months. Like, when Hardy was released, its version number was 8.04 while now it is 8.04.3(proof of this is at releases.ubuntu.com). Since LTS releases recieve long term support, canonical amends updates into the ISOs every few months.:popcorn:

---

### Post by louieb on 2009-11-24
Take an LTS release like Hardy when 1st released its v8.04. Every so often - no set schedule an updated CD is put out:  v8.04.1, v8.04.2, right now  if your Hardy install is up to date its at v8.04.3. 

```

/home/lou%>uname -r  && cat /etc/*release  
2.6.24-25-generic
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.3 LTS"

```

If you download a Hardy CD today you would get v8.04.3.

---

### Post by donato roque on 2009-11-24
> **emigrant said:**
> hi all ;)

can any one tell me, whether the new fixes and updates are integrated to the downloadable isos in the ubuntu page?

i mean an iso i downloaded on the first day of karmic release and an iso i download today, are both same?

thank you for your time :popcorn:

No.
ISO is fix.  That's why you have to update. after installing you are prompted to update.

---

### Post by good_times on 2009-11-24
Agreed donato roque
 
There are several posts around the forums which mention the first thing you should do after a fresh install (from the CD) is to do a manual upgrade. If you do this you'll see that there are several bits to add on.
This'll put you right back up to date though

---

### Post by Cheesemill on 2009-11-24
I usually use the Mini CD to install. This is a small iso (around 12MB) which only contains the installer. All the latest versions of the packages required are downloaded from your selected mirror during the installation. This way you have a fully updated version as soon as the installation is complete. If you have a fast connection then this way of installation can be quicker than a normal install + updates, especially later on in the lifecycle of a version when there can be hundreds of updates.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by emigrant on 2009-11-24
> **Cheesemill said:**
> I usually use the Mini CD to install. This is a small iso (around 12MB) which only contains the installer. All the latest versions of the packages required are downloaded from your selected mirror during the installation. This way you have a fully updated version as soon as the installation is complete. If you have a fast connection then this way of installation can be quicker than a normal install + updates, especially later on in the lifecycle of a version when there can be hundreds of updates.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

thanks for the link,
yet i can't afford that, since even for normal updates im using keryx on faster connections :D

---

### Post by Cheesemill on 2009-11-24
Also it's possible to create your own up to date CD if you wish. Just install and update and then use Remastersys to create a new CD. I do this in a VM to create CD's for friends (I also install the medibuntu and restricted extras stuff onto the CD so it's usable straight away for them).

---

