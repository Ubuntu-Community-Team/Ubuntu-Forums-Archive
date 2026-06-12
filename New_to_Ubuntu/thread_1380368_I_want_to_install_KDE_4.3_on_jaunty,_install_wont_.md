---
title: "I want to install KDE 4.3 on jaunty, install wont work."
date: 2010-01-13
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-01-13
Hey guys, i want to try KDE on ubuntu 9.04 im following this guide here, [http://news.softpedia.com/news/How-to-Install-KDE-4-3-on-Ubuntu-9-04-118645.shtml](http://news.softpedia.com/news/How-to-Install-KDE-4-3-on-Ubuntu-9-04-118645.shtml)

when i go to install KDE 4.3 by clicking the link it gives me an error saying that the package cannot be corrected and may be broken, is this a broken link with the site or have i done something wrong?

---

### Post by SuperSonic4 on 2010-01-13
What step did you get to?

---

### Post by Rave Gloves on 2010-01-13
> **SuperSonic4 said:**
> What step did you get to?

I got to step 2, where it says "click here to install KDE version 4.3"

---

### Post by Rave Gloves on 2010-01-13
Anyone else know what to do?, i tried more guides and they are all diffrent.

---

### Post by warfacegod on 2010-01-13
Give this a shot:

```
sudo apt-get install kubuntu-desktop kde-admin kdebase kdenetwork kdemultimedia
```

---

### Post by Rave Gloves on 2010-01-13
> **warfacegod said:**
> Give this a shot:

```
sudo apt-get install kubuntu-desktop kde-admin kdebase kdenetwork kdemultimedia
```

I ended up getting it working in terminal, thanks (:

First impressions. Looks lovely. text looks, strange.
Its kinda laggy when looking through the menus. I have activated my hardware driver for the graphics, for some reason in Gnome i couldnt get my effects activated in appearance. Will this problem carry over to the KDE?

---

### Post by warfacegod on 2010-01-13
> **Rave Gloves said:**
> I ended up getting it working in terminal, thanks (:

First impressions. Looks lovely. text looks, strange.
Its kinda laggy when looking through the menus. I have activated my hardware driver for the graphics, for some reason in Gnome i couldnt get my effects activated in appearance. Will this problem carry over to the KDE?

I don't know. I found the initial install "laggy" as well. I sped things up nicely with a few tweaks. As a whole somewhat more pleasing to the eye than gnome with a few glaring exceptions. The menu layout has no grasp of logic or reason. As a whole pretty good.

---

### Post by Rave Gloves on 2010-01-13
> **warfacegod said:**
> I don't know. I found the initial install "laggy" as well. I sped things up nicely with a few tweaks. As a whole somewhat more pleasing to the eye than gnome with a few glaring exceptions. The menu layout has no grasp of logic or reason. As a whole pretty good.

I agree with the layout, its very damn confusing. 

You cant get kde 4.4 on 9.04 can you?. Karmic dosent like my laptop for some reason.

---

### Post by warfacegod on 2010-01-13
> **Rave Gloves said:**
> I agree with the layout, its very damn confusing. 

You cant get kde 4.4 on 9.04 can you?. Karmic dosent like my laptop for some reason.

I have no idea, sorry. The code I gave you I did in a 9.10 upgrade from 9.04 and I never bothered to check the KDE version.

---

