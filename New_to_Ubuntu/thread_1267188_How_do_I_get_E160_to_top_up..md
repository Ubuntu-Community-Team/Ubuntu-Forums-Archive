---
title: "How do I get E160 to top up."
date: 2009-09-15
forum: New to Ubuntu
---

### Post by pirate paul on 2009-09-15
Hi, I need to top up my E160 before my cred runs out/ I down loaded /tmp/vodafone-mobile-connect-2.10.01-1.noarch.rpm but it could not be opened because the associated helper does not exist. 
 Any ideas what to do about it?

---

### Post by durand on 2009-09-15
An rpm package is for RPM distributions like fedora. Ubuntu is a deb distribution so you need a .deb package. There is a way to convert the package however it could glitch.

Open a terminal (Applications > Accessories > Terminal), type:
```
sudo aptitude install alien
```

Then convert the rpm to a deb.
```
sudo alien  /tmp/vodafone-mobile-connect-2.10.01-1.noarch.rpm
```

I can't try it right now but you need to answer a few questions which you can just press Enter on and it will then create a deb file.

You then need to install it.

```
sudo dpkg -i vodafone*
```

That *should* work but its not guaranteed.

---

### Post by dionysius on 2009-09-15
If you only need to top up, can't you use a electronic top up card? 
And, if you need to convert your credit to a 'pass' or something, take the SIM out of the dongle, stick it into a Vodafone or unlocked phone and get the pass that way? 

I'm using T-Mobile broadband and just do it that way once a month without installing additional software. Happier not using telecoms companies redundant packages anyway.

---

