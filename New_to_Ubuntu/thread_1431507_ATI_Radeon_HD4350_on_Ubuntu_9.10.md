---
title: "ATI Radeon HD4350 on Ubuntu 9.10"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by robfindlay on 2010-03-16
My brother is running 9.10 his nVidia card died and the only "slim line" card we could find at the local shop that would fit his case is the above mentioned HD4350 

When booting to a live DVD OR trying an install we get the following error: 

```
init mountall main process 1291 terminated with status 127
```

Now from reading through the forums it looks like that this card is not supported in 9.10 or supported very poorly. 

Two questions: 
1. Is it worth trying to hack around and make this ATI card work? Has anyone done it and if so how? 
OR
2. Would it be EASIER to just order an nVidia card that would fit and avoid the above mentioned nightmare altogether? 

-Rob

---

### Post by inobe on 2010-03-16
i will be honest and say it's not that the card isn't supported !

all hardware is supported if the manufacturer produces a "good" driver.....

ati/amd hasn't produced very good drivers for as long as i can remember.


we'll take that into account and the fact that the old driver may still be activated and something may be corrupt "now" ?

possibly if you can get some help purging the old driver in command line.

i don't know how to do that, you may find someone here that does.

as for nvidia, it uses a unified driver' so swapping cards would be effortless, with some ati cards this isn't possible without some sort of hardware/ driver corruption.

it's a known fact that nvidia does a better job producing linux drivers, any nvidia 6 series cards and up are good.

---

### Post by robfindlay on 2010-03-16
> **inobe said:**
> i will be honest and say it's not that the card isn't supported !

all hardware is supported if the manufacturer produces a "good" driver.....

ati/amd hasn't produced very good drivers for as long as i can remember.


we'll take that into account and the fact that the old driver may still be activated and something may be corrupt "now" ?

possibly if you can get some help purging the old driver in command line.

i don't know how to do that, you may find someone here that does.

as for nvidia, it uses a unified driver' so swapping cards would be effortless, with some ati cards this isn't possible without some sort of hardware/ driver corruption.

it's a known fact that nvidia does a better job producing linux drivers, any nvidia 6 series cards and up are good.

Well since he has a working 9.10 install I'd rather not bugger we're just going to look for an nVidia me thinks. 

THANKS MAN!

-Rob

---

### Post by inobe on 2010-03-16
hit escape when seeing the grub screen and choosing recovery mode.

in there are some tools, you can try xfix if still there.

i doubt that it will help, you may get a loaded desktop with poor resolution, but you may be able to reinstall ati's driver.

---

### Post by Joshcush on 2010-03-16
Im not sure if this will be any help to you, but my laptop has a 4570 and it works flawlessly.

---

### Post by robfindlay on 2010-03-16
My brother has a "slim line" case from dell, so it wont fit the standard width E-PCI cards. I.E. width meaning from the motherboard to the mounting screw.

What is the technical term to look for when shopping for cards for one that will fit this "slim" form-factor? 

-R

---

### Post by albert s on 2010-03-16
I dont know whether to be glad or not that I have absolutely no idea what you are talking about,
and I thought I had a sort of an idea about cards,
I suppose now I start all over again.....


:( :( :(

---

### Post by lidex on 2010-03-16
> **robfindlay said:**
> My brother has a "slim line" case from dell, so it wont fit the standard width E-PCI cards. I.E. width meaning from the motherboard to the mounting screw.

What is the technical term to look for when shopping for cards for one that will fit this "slim" form-factor? 

-R

Low profile?
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048&bop=And&ActiveSearchResult=True&SrchInDesc=low%20profile&Page=1]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048&bop=And&ActiveSearchResult=True&SrchInDesc=low%20profile&Page=1")

---

### Post by robfindlay on 2010-03-16
> **lidex said:**
> Low profile?
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048&bop=And&ActiveSearchResult=True&SrchInDesc=low%20profile&Page=1]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048&bop=And&ActiveSearchResult=True&SrchInDesc=low%20profile&Page=1")

that's it thanks!

---

