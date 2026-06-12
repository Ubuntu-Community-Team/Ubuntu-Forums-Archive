---
title: "Google earth kinda screwy on Ubuntu?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by cptrohn on 2009-01-31
hmm I downloaded google earth and it seemed to have some kind of a graphics problem with it..

I am using kubuntu on a pretty new laptop so I wouldn't thing something like Google earth would be a problem..

Does anybody else have experience with this issue?

---

### Post by taurus on 2009-01-31
What kind of graphic card does your laptop have and have you installed a driver for it?

---

### Post by Crafty Kisses on 2009-01-31
Do you have desktop effects enabled? What are your system specs?

---

### Post by cptrohn on 2009-01-31
> **taurus said:**
> What kind of graphic card does your laptop have and have you installed a driver for it?

Hmm I don't really know what the graphics card is.. and I know I have never installed a driver for it.

How do I check?

---

### Post by Crafty Kisses on 2009-01-31
You would go to **System->Administration->Hardware Drivers**, then from there you can check and see if there's any drivers available for you to download.

---

### Post by taurus on 2009-01-31
Open a terminal and run

```
lspci | grep VGA
```

---

### Post by taurus on 2009-01-31
> **Codename said:**
> You would go to **System->Administration->Hardware Drivers**, then from there you can check and see if there's any drivers available for you to download.

That is for Gnome but I think he/she is running KDE (Kubuntu).

---

### Post by eagle416 on 2009-01-31
when I installed google earth, it was extremely slow and choppy. I can't get it to go either.

---

### Post by cptrohn on 2009-01-31
ok this is what I get back on the graphics card```
00.02.0 VGA compatible controller: Intel Corporation Mobile GM 963/GL 960 Integrated Graphics Controller (rev 03)
```

Now when I checked for the hardware drivers all that showed up were the ones for my wireless card.

---

### Post by cptrohn on 2009-01-31
> **taurus said:**
> That is for Gnome but I think he/she is running KDE (Kubuntu).

LOL I'm a guy..

and I have KDE as my desktop, but it was installed after I installed 8.10... I don't know if that makes a difference or not.

---

### Post by cptrohn on 2009-01-31
> **Codename said:**
> Do you have desktop effects enabled? What are your system specs?

I think I do have desktop effects enabled. I think I remember that.

---

### Post by k3lt01 on 2009-01-31
Remove Compiz and its associated parts, and install MetaCity.

That "should" fix your Google Earth problem.

---

### Post by cptrohn on 2009-01-31
> **k3lt01 said:**
> Remove Compiz and its associated parts, and install MetaCity.

That "should" fix your Google Earth problem.
Ahh ok, so the compiz doesn't play nice with google earth...

Thanks.

---

### Post by cptrohn on 2009-01-31
Ok after playing around some it was the desktop effects being enabled that was screwing with Google Earth..

No big deal... just toggle them on and off as needed I suppose.

---

### Post by Crafty Kisses on 2009-01-31
I'm glad that worked for you my friend. :)

---

### Post by k3lt01 on 2009-01-31
> **cptrohn said:**
> Ahh ok, so the compiz doesn't play nice with google earth...

Thanks.

> **cptrohn said:**
> Ok after playing around some it was the desktop effects being enabled that was screwing with Google Earth..

No big deal... just toggle them on and off as needed I suppose.
Compiz is the Windows Manager that enables Desktop Effects, thats why I suggested you remove it. I had the same issue on my fathers laptop and with him being a new user I just did what I suggested to you. I'm glad you figured it out :D.

---

### Post by LinnetLegs on 2009-02-01
Just to elaborate a bit further - I had this problem and turned off desktop effects. I can view google earth no problem, but some of the text of town names disappears - ie Birmingham  reads Birm ng am. Any ideas?

---

