---
title: "Cannot install Opera or Flock"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by wannabegeek on 2010-01-06
Hello all,

I'm running Hardy and can't seem to install Opera or Flock. 

until recently my Firefox worked perfectly, all of a sudden  certain pages won't load.
I want to try out Opera anyways...I amended my sources.list file with:

```
deb http://archive.canonical.com/ hardy partner 
```Then I updated, and tried the usual:
```
sudo apt-get update 
sudo apt-get install opera

```

and it built the dependency trees, then said that there was no install candidate.

I think it's time for me to install a newer Ubuntu distro., but I want a new computer in about a month and will go through all this again...so for now I'd love get Opera working, and /or fix my Firefox.

TIA

wbg

---

### Post by mechro on 2010-01-06
I use Opera and download it from the Opera site. It usually offers you the correct debian package for your system. Once downloaded just right-click the file and gdebi install...

[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by wannabegeek on 2010-01-06
thanks for reply mechro,

I want to stick to the Ubuntu repositories since I'm a newb...

I did find this cool page, which has a comprehensive list of what's in the Repo.

 [http://sathyasays.com/2008/11/18/a-comprehensive-list-of-ubuntu-hardy-heron-and-ubuntu-intrepid-ibex-repositories/](http://sathyasays.com/2008/11/18/a-comprehensive-list-of-ubuntu-hardy-heron-and-ubuntu-intrepid-ibex-repositories/)

I found this: 
# The Opera browser (packages) (GPG key: 6A423791)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

and added to my sources.list....already had the from an earlier misguided attempt...

Then I was able to install with apt-get...I dare say this is solved.

---

### Post by mechro on 2010-01-06
> **wannabegeek said:**
> 

I want to stick to the Ubuntu repositories since I'm a newb...



Yep, I was kind of sad when my present and previous Ubuntu installations took Opera out of the Ubuntu repositories :(  But I love my Opera so I had to arrange my fix elsewhere. :D

---

### Post by wannabegeek on 2010-01-06
hey Mechro how do I change my home page in Opera...can't find it...

have you ever had problems loading certain pages, when other machines don't...I'm thinking I have some kind of firewall issue...I haven't thought about firewalls since I starting using Ubuntu...

thx

---

### Post by mechro on 2010-01-06
To change your Home page... navigate to the page you want... go to Tools > Preferences > General - click "Use Current" button.

I don't get too many issues with pages not loading. Can you give an example of a page that isn't loading for you? Perhaps flashplayer is now broken in Hardy?

---

### Post by wannabegeek on 2010-01-06
hey,

the one definite page which doesn't load is the login for my University, Opera had a slightly better time than Firefox.  The page appears to be a secure login, which fails, and in Firefox, I get redirected to an error.  Not sure how to describe it...

---

